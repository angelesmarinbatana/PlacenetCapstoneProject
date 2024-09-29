```mermaid
classDiagram
    class User {
      +String name
      +String email
      +String password
      +createProfile()
      +updateProfile()
    }

    class Property {
      +String address
      +int numberOfBeds
      +int numberOfBaths
      +float size
      +createProperty()
      +editProperty()
    }

    class Project {
      +String name
      +String address
      +String contractor
      +Date date
      +createProject()
      +editProject()
      +deleteProject()
    }

    class Document {
      +String documentName
      +Date dateAdded
      +String userAdded
      +editDocument()
      +deleteDocument()
      +addDocument()
    }

    User "1" --> "0..*" Property : connects to
    Property "0..*" --> "0..*" Project : connects to
    Project "0..*" --> "0..*" Document : connects to
