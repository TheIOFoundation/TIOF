# Infrastructure: Salesforce

![logo](http://tiof.click/TIOFWikiHeader)

## About

## Usage

## Information

## Object Model

This section describes the object model used in this App.

See render here: http://www.plantuml.com/plantuml/png/bP3HYnCn4CRVyrVCzULESBjwY4eVv4hXyC1YeTwpp2MpJJ2RXCd4KiJ\_tVJSdgwbnSlB9j\_C\_BxvzYOBifJUgwpH4xn-TVq6jiw87OHtRz-39RUnejI5eSu5WfXnLKV0YgGyQrl6xNJZn9Q7aebr3491fZhsxO8nMpAz2wPTUGnol\_pKn4GXaoxiP8UihHFIKfYk6rTdSzjZ5c9ruOBsnJpPjOlOzp5CKxqV5--hSulUdoX\_H3PRP3hJidHPdoclYR-VjLWx-Gklr6NppACkuIvqZ5cuFFuGk2qXaCzAueR44iCFLTs-6ihV9AQhkTQn17a9a-4sgTVrVBv-\_AAdt4NMD7ancbfYIcGMCGZg\_UplDmp2MOJ7j2UisFN8kp-8GVWlXblP6EXgtdNEEvIdJN9jFXPFedugfORKq3GVO9Hg1eSIKsBA52eI7dOmpZeT4SQfPeSc48i2srXy9L1z4LHS3Pk8SmnG5wgYomVBCVGuKTtDUpYyWCdlgo3n7qezNOn235-gvTrdkAswGN4nA7L3mPJU\_m80

### Contacts

Contacts are at the core of the SF Object Model.

All App syncs are done based on SF Contacts.

### Accounts

Accounts are considered as "Groups of Contacts". They are related using the following associations:

#### Mapped Contact

Quantity: Only one

Usage: This Contact is the necessary "twin" Contact that contains all the data relative to an Account.

Rationale: Accounts are not synchronized with certain Apps (such as Google Contacts or Encharge.io) so there needs to be a Contact that carries all the necessary information. This approach also allows for a standard approach when treating SF data.

#### Primary Contact

Quantity: Zero or one

Usage: This Contact indicates who would be the primary person to reach out when attempting to reach out to this Account.

#### Affiliated Contacts

Quantity: Zero or more

Usage: These Contacts represent all the members that belong to this Account.

***

## PlantUML diagram source.

@startuml scale 1024 width scale 768 height

!define osaPuml https://raw.githubusercontent.com/Crashedmind/PlantUML-opensecurityarchitecture2-icons/master !include osaPuml/Common.puml !include osaPuml/User/all.puml !include osaPuml/Hardware/all.puml !include osaPuml/Misc/all.puml !include osaPuml/Server/all.puml !include osaPuml/Site/all.puml

'------------------------------------------------ ' Infrastructure Funnels together { osa\_desktop(Account, "Account", "SAAS", "Salesforce") osa\_desktop(MappedContact, "Mapped Contact", "SAAS", "Salesforce") osa\_laptop(PrimaryContact, "Primary Contact", "SAAS", "Salesforce") osa\_iPhone(AffiliatedContacts, "AffiliatedContacts", "SAAS", "Salesforce") }

Account --> MappedContact: Account represented by Mapped Contact. Account --> PrimaryContact: Contact that would be the entry person for this Account. Account --> AffiliatedContacts: All Contacts related to this Account.

footer The IO Foundation

@enduml
