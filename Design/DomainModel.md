# Explanation: 
- User
    - User is a superclass as it represents attributes and behaviors of homeowners and tenants.
    - Users will have common properties and user types might be able to inherit from User class.
    - A user can own multiple properties.
    - This class will have methods to create and update the user's profile.
    - Users will have to authenticate themselves via a password they make upon creating their account and by having an email associated with it.
 - Property
     - **Property** class represents the actual properties that **User** will manage within the app.
     - It will have **property details** which will be provided by the user, which will help in property management.
     - This class will have methods to add, remove, and edit the property.
     - Each property will be able to have projects attached to them for organization and tracking.
- Project
    - **Project** class will represent the tasks related to a property, including repairs, upgrades, or maintenance.
    - It will have attributes to identify tasks, and to capture the time frame of projects.
    - It will have methods to add, edit, and remove tasks.
    - It will also have a method to upload relevant documents to the project.
- Document
    - **Document** class will keep track of records related to a **Property's** **Projects**, helping users to have a recorded history of the work done to their **Properties**.
    - It will have an identifier and the time when the document was uploaded.
    - It will have methods to add, edit, and delete documents. 








# Domain Model:
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
