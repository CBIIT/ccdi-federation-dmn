### The CCDI Federation Data Model

The CCDI Federation data model is a graph-based structure designed to enable federated access to pediatric cancer data across multiple organizations and data repositories. Nodes in this federation model represent key entities such as organizations, namespaces, subjects, samples, and files, with properties within each node defining the essential attributes and metadata. This federated approach allows the CCDI to integrate and provide unified access to diverse pediatric cancer datasets while maintaining data sovereignty and governance at the source organizations. The model supports cross-institutional collaboration by providing standardized interfaces for data discovery, access, and integration across the federation's participating members.

### Federation Node Categories

All nodes in the CCDI Federation data model are assigned to categories that represent the federated infrastructure and data organization. The **Core** category contains the fundamental federation entities including organizations that own data, namespaces that provide logical groupings, and the primary data entities (subjects, samples, files). Each organization within the federation maintains sovereignty over their data while participating in the unified federation structure. The model includes secondary nodes that provide detailed metadata and identifier structures, and gateway nodes that define access mechanisms for federated data retrieval.

<!-- PAGE BREAK -->

### Facet-Based Filtering

The facet-based filtering options presented within the left-hand sidebar of the Data Model Navigator allow users to filter the display of nodes based upon their designations for Category, Assignment and Class; based upon nodes containing required versus preferred versus optional properties; and based upon nodes containing properties that are displayed within the federation interface. Using this array of filtering criteria, users can quickly partition the federation data model into smaller sets of nodes and thereby identify nodes of particular interest for federated data access and integration. Note that filtering criteria can be applied to both the Graph View and the Table View, and that filter selections are maintained when switching back and forth between viewing modes.

### Graph View

In Graph View mode, the Data Model Navigator provides users with an interactive, graphical rendering of the CCDI Federation data model, which can be filtered as described above, in order to identify the nodes and therefore properties most relevant for federated data access and integration. Selecting a node of interest invokes a Properties Dialogue box which indicates the node's Assignment and Class designations and quantifies the number of properties within the node that are Required, Preferred and Optional. A detailed tabular view of the node can be invoked by selecting the "Open Properties" option displayed within the Properties Dialogue box.

### Table View

In Table View mode, the Data Model Navigator displays detailed tabular views of each node in the CCDI Federation data model, which fully-define the properties within them, inclusive of the applicable controlled vocabularies of acceptable terms for enumerated properties. The tabular views also clearly identify which properties are Required versus those that are Preferred or Optional; the acceptable data type for each property; which properties are displayed within the federation interface; and the labels via which such properties are displayed. Note that many properties displayed within the interface are renamed with labels which are more intuitive than the property names themselves, and that some properties are displayed via more than one label. As described below, comprehensive documentation of the federation data model's nodes and property requirements can be downloaded in PDF format via the Table View, alongside node-specific data loading templates for federation participants.

### Required, Preferred and Optional Properties

Each property is assigned one of three requirement levels - Required, Preferred, or Optional.

- **Required** properties are largely self-explanatory, i.e. data destined for a node which contains required properties must include values for all such properties, and values must be compliant with the acceptable values for properties which are both required and enumerated. Controlled vocabularies for such properties typically include terms such as "Not Applicable", "Not Determined" and "Unknown" to accommodate situations where data values aren't relevant or weren't collected, either by design or otherwise.
- **Preferred** properties represent properties for which data values are not required, but which add significant insight and detail, have been populated to a significant degree thus far, and for which data is typically available when requested during federation onboarding.
- **Optional** properties are precisely that and null values are allowed.

<!-- PAGE BREAK -->

### Key Properties

Many nodes contain a single property visually identified as a Key Property by a **blue key icon** displayed next to the name of the appropriate property. In addition to several nodes that require one in support of data updates, all nodes which act as parents of child nodes will likewise have a single property within them identified as a Key Property. During federation data integration, **_child records_** are associated with their correct **_parents_** by virtue of data structures which contain the appropriate values for the property identified as their parents' Key Property. For example, sample records are linked to subjects through identifier structures that reference the subject's Key Property, such as "subject_id" being designated as the Key Property within the **subject** node. Key Properties are therefore functionally equivalent to foreign keys in traditional relational databases and enable federated data relationships across organizations.

### PDF Documentation

Detailed documentation of the CCDI Federation data model's nodes and property requirements can be downloaded as PDF exports, either in the form of a comprehensive data dictionary inclusive of all nodes, invoked via the upper-level "Available Downloads" option, or from within the Table View, and invoked on a node-by-node basis. Used alongside the corresponding data loading templates described below, these node-specific PDF exports function as user guides for federation participants in understanding data structure and integration requirements.

### Data Loading Templates

In support of federation data integration, data loading templates can be downloaded, either in the form of a zip file containing copies of all available templates, invoked via the upper-level "Available Downloads" option, or from within the Table View, and invoked on a node-by-node basis. Templates include columns into which the data values required to associate child records with their parents can be inserted. Notably, each template will include a **mapping column** for each potential parent, but although **_all child records must be mapped to at least one parent_**, federation participants are not required to provide a mapping value for each and every potential parent, _only the_ **_most appropriate parent(s)_**. Guided by the corresponding node-specific PDF exports described above, federation participants can use these data loading templates to understand the structure and requirements for federated data integration within the CCDI Federation.

### Controlled Vocabularies

In the interests of data quality and consistency, the CCDI Federation data model makes extensive use of Common Data Elements (CDEs), enumerated properties and controlled vocabularies of acceptable terms. All such controlled vocabularies can be viewed via Table View mode, and value sets are included in full in the appropriate PDF exports. In addition to the acceptable terms available through the Data Model Viewer, CDEs can be accessed via NCI's [caDSR website](https://cadsr.cancer.gov/onedata/Home.jsp) or [caDSR APIs](https://cadsrapi.cancer.gov/NCIAPI/1.0/index.html). Furthermore, in support of federation participants validating their data structures, all controlled vocabularies can be exported in machine readable JSON and TSV formats, either in the form of a zip file containing copies of controlled vocabularies for all enumerated properties, invoked via the upper-level "Available Downloads" option, or from within the Table View, and invoked on a property-by-property basis. As more organizations join the CCDI Federation, many of these controlled vocabularies will continue to evolve to accommodate additional terms and ensure interoperability across federated data sources.
