# CCDI Federation Data Model Conversion Guide

## 🎯 Objective

Convert the Entity-Relationship (ER) diagram in `/model-desc/federation_resource/CCDI-Federation-API-Data-Model-v1.2.0.png` into structured YAML data model files. This guide will help you extract entities, properties, and relationships from the ER diagram and format them according to the CCDI Federation data model standards.

## 📋 Output Requirements

You will generate two YAML files:
1. **`fed_model.yml`** - Contains entity definitions and relationships
2. **`fed_model.props.yml`** - Contains detailed property specifications

## � Entity Definition Template (`fed_model.yml`)

Each entity in the ER diagram should be converted using this YAML structure:

```yaml
entity_name:
  Desc: Brief description of the entity
  Tags:
    Category: administrative|biospecimen|clinical|index_file|data_file|analysis|notation
    Assignment: core|extended|deprecated
    Class: primary|secondary|utility
    Template: 'Yes'|'No'
  Props:
    - property_1
    - property_2
    - property_3
    # ... additional properties
```

### Field Descriptions:
- **Desc**: Concise description of the entity's purpose
- **Category**: Functional classification of the entity
- **Assignment**: Entity importance level in the model
- **Class**: Primary (main entities) or secondary (supporting entities)
- **Template**: Whether this entity serves as a template for others
- **Props**: List of all properties belonging to this entity

## � Step-by-Step Conversion Process

### Step 1: Entity Analysis
**Identify and catalog each entity from the ER diagram**

**Example: Subject Entity**
From the ER diagram, locate the `subject` entity and extract its properties:

| Property | Data Type | Description |
|----------|-----------|-------------|
| `summary` | `object` | Summary information about the subject |
| `data` | `array` | Collection of subject data points |
| `gateways` | `array` | Associated gateway connections |
| `subject_data` | `object` | Detailed subject data structure |

### Step 2: Entity Definition
**Convert entity information to YAML format**

Create the entity definition in `fed_model.yml`:

```yaml
subject:  
  Desc: Represents a research subject or participant in the study
  Tags:
    Category: clinical
    Assignment: core
    Class: primary
    Template: 'No'
  Props:
    - summary
    - data
    - gateways
    - subject_data
```

### Step 3: Relationship Mapping
**Define relationships between entities**

Identify connections in the ER diagram and create relationship definitions:

```yaml
Relationships:
  belongs_to:
    Mul: many_to_one
    Ends:
      - Src: subject
        Dst: subject_data
    Props: null
```

**Relationship Types:**
- `one_to_one`: 1:1 relationship
- `one_to_many`: 1:n relationship  
- `many_to_one`: n:1 relationship
- `many_to_many`: n:n relationship

### Step 4: Property Specifications
**Define detailed property characteristics in `fed_model.props.yml`**

Template structure for properties:

```yaml
property_name:
  Desc: Clear description of the property's purpose
  Term:
    - Origin: caDSR|GDC|CRDC|local
      Code: 'unique_identifier'
      Value: 'Standardized term name'
  Src: data_source_identifier
  Type: string|number|integer|datetime|boolean|array|object
  Req: 'Yes'|'No'
```

**Example: Subject Summary Property**
```yaml
summary:
  Desc: Summary information and statistics for the subject
  Term:
    - Origin: caDSR
      Code: 'TBD'
      Value: 'Subject Summary Data'
  Src: CCDI
  Type: object
  Req: 'Yes'
```

**Property Type Guidelines:**
- `string`: Text values
- `number`: Decimal numbers
- `integer`: Whole numbers
- `datetime`: Date/time values
- `boolean`: True/false values
- `array`: List of values
- `object`: Complex nested structure

## ✅ Quality Assurance Guidelines

### Validation Checklist
Before finalizing your YAML files, ensure:

- [ ] All entities from the ER diagram are included
- [ ] Entity names use consistent naming conventions (lowercase, underscores)
- [ ] All properties are listed under their respective entities
- [ ] Relationships accurately reflect the ER diagram connections
- [ ] Property types are appropriate for the data they represent
- [ ] Required fields (`Req: 'Yes'`) are properly identified
- [ ] Descriptions are clear and concise
- [ ] YAML syntax is valid and properly indented

### Common Pitfalls to Avoid
- **Inconsistent naming**: Use snake_case for all entity and property names
- **Missing relationships**: Every connection in the ER diagram should have a corresponding relationship
- **Incorrect multiplicity**: Verify relationship cardinality matches the diagram
- **Vague descriptions**: Provide meaningful descriptions rather than placeholders like "TBD"
- **Wrong data types**: Ensure property types align with their intended use

### Best Practices
- Use descriptive but concise entity and property names
- Group related properties logically within entities
- Maintain consistency in terminology across the model
- Document any assumptions made during conversion
- Cross-reference with existing CCDI standards where applicable

## 📚 Additional Resources

- ./model-desc/federation_resource/OpenAPI-Federation-Resource-v1.2.0.yml
- ./model-desc/federation_resource/OpenAPI-Spec-Released.yml
- ./model-desc/federation_resource/CCDI-Federation-API-Data-Model-v1.2.0.png

---

*Last updated: August 2025*
*Version: 1.0*