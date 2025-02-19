# Active Directory (AD) Overview

## Object
An **object** is any resource present within an Active Directory (AD) environment, such as:
- Organizational Units (OUs)
- Printers
- Users
- Domain Controllers (DCs)
- Computers
- Groups

## Attributes
Every object in AD has a set of **attributes** that define its characteristics. For example:
- A **computer object** has attributes like **hostname** and **DNS name**.
- A **user object** has attributes such as **displayName** (Full Name) and **givenName** (First Name).
- Each attribute has an associated **LDAP name**, used for querying AD.

## Schema
The **Active Directory schema** is the blueprint of the AD database. It defines:
- Object types that can exist in AD.
- Their associated attributes.
- Class definitions (e.g., "user" for users, "computer" for computers).
- When an object is created from a class, this is called **instantiation**, and the resulting object is an **instance** of that class.

## Domain
A **domain** is a logical grouping of objects (users, computers, groups, OUs, etc.). It functions independently but can establish **trust relationships** with other domains.

## Forest
A **forest** is a collection of AD domains and the topmost container in AD. It includes:
- Domains
- Users
- Groups
- Computers
- Group Policy Objects (GPOs)
- Trust relationships between domains

## Tree
A **tree** is a collection of AD domains sharing a **common namespace**. It consists of a **root domain** and **child domains** (e.g., `corp.inlanefreight.local`). Multiple trees form a **forest**.

## Container & Leaf Objects
- **Container objects** hold other objects and define a **hierarchical structure** in AD.
- **Leaf objects** do not contain other objects and are at the end of the hierarchy.

## Global Unique Identifier (GUID)
A **GUID** is a **128-bit unique identifier** assigned to every AD object upon creation. It never changes and is stored in the **ObjectGUID** attribute. It is the most reliable way to query AD objects.

## Security Principals
Security principals are entities that AD can authenticate, including:
- Users
- Computers
- Services running under specific accounts

## Security Identifier (SID)
A **SID** is a **unique identifier** assigned to each security principal (user, group, or computer). Even if an account is deleted, its SID is never reused.

## Distinguished Name (DN) & Relative Distinguished Name (RDN)
- A **Distinguished Name (DN)** specifies an object's full AD path (e.g., `CN=bjones,OU=IT,OU=Employees,DC=inlanefreight,DC=local`).
- A **Relative Distinguished Name (RDN)** is a **unique** identifier at its level (e.g., `bjones` in the example above).

## Account Naming Attributes
- **sAMAccountName**: The **user logon name** (must be **≤ 20 characters**, unique per domain).
- **userPrincipalName (UPN)**: Alternative logon format (`bjones@inlanefreight.local`).

## FSMO Roles (Flexible Single Master Operations)
FSMO roles prevent conflicts in AD replication. They include:
- **Schema Master** (1 per forest)
- **Domain Naming Master** (1 per forest)
- **RID Master** (1 per domain)
- **PDC Emulator** (1 per domain)
- **Infrastructure Master** (1 per domain)

Each role ensures proper domain operations and replication.

## Global Catalog (GC)
A **Global Catalog (GC)** is a DC that stores:
- **A full copy** of objects in its domain.
- **A partial copy** of objects in other domains of the forest.
- It enables **fast searches** across the entire forest and **authentication** of users from other domains.

## Read-Only Domain Controller (RODC)
An **RODC** has a **read-only AD database**, used for:
- **Security** (prevents local password caching except for explicitly allowed accounts).
- **Reduced replication traffic**.
- **Separation of administrative roles**.

## Replication
AD **replication** synchronizes changes across **Domain Controllers**. The **Knowledge Consistency Checker (KCC)** manages replication topology.

## Service Principal Name (SPN)
An **SPN** uniquely identifies a service instance and is crucial for **Kerberos authentication**.

## Group Policy Object (GPO)
GPOs define **security settings, software installations, and policies** that apply to AD users and computers.

## Access Control Lists (ACLs) & Access Control Entries (ACEs)
- **ACL**: A list of permissions assigned to an object.
- **ACE**: Defines **who** has access and **what permissions** they have.
- **DACL (Discretionary ACL)**: Determines **who can access** an object.
- **SACL (System ACL)**: Logs **access attempts** for security auditing.

## Fully Qualified Domain Name (FQDN)
An **FQDN** specifies a computer’s **hostname** and **domain name** (e.g., `DC01.INLANEFREIGHT.LOCAL`).

## Tombstone
A **tombstone** is a **soft-deleted** AD object. It remains in AD for a **Tombstone Lifetime** (default: **60-180 days**) before **permanent deletion**.

# Trusts

A **trust** in Active Directory is used to establish authentication between forests or domains. It allows users to access resources or administer systems in a different domain than the one where their account resides. Essentially, a trust creates a link between the authentication systems of two domains.

There are several types of trusts in Active Directory, each serving different purposes:

| **Trust Type**       | **Description**                                                                                       |
|----------------------|-------------------------------------------------------------------------------------------------------|
| **Parent-child**      | Establishes a trust between domains within the same forest. The child domain has a two-way, transitive trust with the parent domain. |
| **Cross-link**        | A trust between child domains to speed up authentication processes.                                  |
| **External**          | A non-transitive trust between two separate domains in different forests that are not connected by a forest trust. This trust utilizes SID filtering. |
| **Tree-root**         | A two-way, transitive trust between a forest root domain and a new tree root domain. This trust is automatically created when setting up a new tree root domain within a forest. |
| **Forest**            | A transitive trust between two forest root domains, enabling full authentication and access between forests. |

# AD Roles

Active Directory also uses specific roles to manage various aspects of domain and forest operations. These roles are assigned to Domain Controllers (DCs) in the environment:

| **Role**              | **Description**                                                                                       |
|-----------------------|-------------------------------------------------------------------------------------------------------|
| **Schema Master**      | Manages the read/write copy of the AD schema, which defines all possible attributes that can be applied to objects in AD. |
| **Domain Naming Master** | Ensures that domain names within the forest are unique and prevents the creation of domains with duplicate names. |
| **Relative ID (RID) Master** | Assigns blocks of RIDs (Relative Identifiers) to other DCs in the domain for use in creating new objects. This ensures that objects have unique Security Identifiers (SIDs). |
| **PDC Emulator**       | Acts as the authoritative DC for authentication requests, password changes, and managing Group Policy Objects (GPOs). It also maintains time synchronization within the domain. |
| **Infrastructure Master** | Translates GUIDs, SIDs, and DNs between domains, particularly in multi-domain forests. If this role fails, Access Control Lists (ACLs) will display SIDs instead of fully resolved names. |



