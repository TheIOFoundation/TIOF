# Infrastructure: Custom Fields

## IMPORTANT

All field syncs follow the route

App A >> SF >> App B

In other words, 2 Apps won't be synchronizing data between themselves. Any sync MUST involve App A pushing the data to Salesforce and pulling it from it towards App B.

## Salesforce

### Accounts

#### Segments

### Contacts

#### Time Zones

Time Zones Source: https://msdn.microsoft.com/en-us/library/ms912391(v=winembedded.11).aspx Customization:

* Joined fields
* Added GMT >> UTC/GMT

Time Zone Area

#### Segments

## Encharge

Custom fields are organized in Folders whose name corresponds to TIOF project codes. \[TIOF] \[TIOF TU] etc.

Inside each Folder are stored the corresponding Project's Custom Fields.

Custom fields take the sane name as in Salesforce.

### Segments

### Field correspondance

| Salesforce                                    | Encharge.io                                   | Notes                                                                                         |
| --------------------------------------------- | --------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Email                                         | email                                         |                                                                                               |
| ???                                           | firstName                                     |                                                                                               |
| ???                                           | lastName                                      |                                                                                               |
| Name                                          | name                                          |                                                                                               |
| npsp\_\_Primary\_Affiliation\_\_c             | company                                       |                                                                                               |
| TIOF\_Website\_\_c                            | website                                       |                                                                                               |
| ???                                           | salutation                                    |                                                                                               |
| Title                                         | title                                         |                                                                                               |
| ???                                           | leadScore                                     |                                                                                               |
| ???                                           | userId                                        |                                                                                               |
| ???                                           | updatedAt                                     |                                                                                               |
| HasOptedOutOfEmail                            | unsubscribed                                  |                                                                                               |
| ???                                           | id                                            |                                                                                               |
| ???                                           | enchargeAnonymousId                           |                                                                                               |
| ???                                           | segmentAnonymousId                            |                                                                                               |
| ~~Phone~~                                     | phone                                         | Do NOT sync                                                                                   |
| ~~MailingAddress~~                            | address                                       | Do NOT sync                                                                                   |
| ???                                           | country                                       |                                                                                               |
| ???                                           | city                                          |                                                                                               |
| ???                                           | state                                         |                                                                                               |
| ~~???~~                                       | postcode                                      | Do NOT sync                                                                                   |
| TIOF\_Time\_Zone\_\_c                         | timezone                                      |                                                                                               |
| ???                                           | groupId                                       |                                                                                               |
| ???                                           | referrer                                      |                                                                                               |
| ???                                           | firstReferrer                                 |                                                                                               |
| ???                                           | UTMSource                                     |                                                                                               |
| ???                                           | UTMMedium                                     |                                                                                               |
| ???                                           | UTMTerm                                       |                                                                                               |
| ???                                           | UTMContent                                    |                                                                                               |
| ???                                           | UTMCampaign                                   |                                                                                               |
| ???                                           | firstUTMSource                                |                                                                                               |
| ???                                           | firstUTMMedium                                |                                                                                               |
| ???                                           | firstUTMTerm                                  |                                                                                               |
| ???                                           | firstUTMContent                               |                                                                                               |
| ???                                           | firstUTMCampaign                              |                                                                                               |
| ???                                           | landingPage                                   |                                                                                               |
| N/A                                           | ip                                            | Do NOT sync                                                                                   |
| N/A                                           | platform                                      | Do NOT sync                                                                                   |
| N/A                                           | browser                                       | Do NOT sync                                                                                   |
| N/A                                           | deviceType                                    | Do NOT sync                                                                                   |
| N/A                                           | device                                        | Do NOT sync                                                                                   |
| PENDING                                       | unsubscribeReason                             |                                                                                               |
| ???                                           | MRR                                           |                                                                                               |
| ???                                           | trialStart                                    |                                                                                               |
| ???                                           | trialEnd                                      |                                                                                               |
| ???                                           | deletedAt                                     |                                                                                               |
| ???                                           | validationResult                              |                                                                                               |
| ???                                           | validationConfidence                          |                                                                                               |
| ???                                           | isEmailDisposable                             |                                                                                               |
| ???                                           | isEmailRole                                   |                                                                                               |
| N/A                                           | TIOF\_Sync\_Status                            | This is an internal indicator for Encharge                                                    |
| LeadSource                                    | LeadSource                                    | x                                                                                             |
| ???                                           | Rolling                                       |                                                                                               |
| Title                                         | Title                                         |                                                                                               |
| N/A                                           | Airmeet\_Registration                         | To be updated to: TIOF\_Airmeet\_Registration / To be deprecated and introduced in LeadSource |
| TIOF\_Segment\_TU\_Open\_Source\_Project\_\_c | TIOF\_Segment\_TU\_Open\_Source\_Project\_\_c |                                                                                               |
| TIOF\_Segment\_TU\_Organization\_\_c          | Segment\_Organization                         | To be updated to: TIOF\_Segment\_TU\_Organization\_\_c                                        |
| TIOF\_Segment\_TU\_Speaker\_\_c               | Segment\_Speaker                              | To be updated to: TIOF\_Segment\_TU\_Speaker\_\_c                                             |
| TIOF\_Segment\_TU\_Audience\_\_c              | Segment\_Audience                             | To be updated to: TIOF\_Segment\_TU\_Audience\_\_c                                            |
| TIOF\_Segment\_TIOF\_Newsletter\_\_c          | Segment\_Newsletter                           | To be updated to: TIOF\_Segment\_TIOF\_Newsletter\_\_c                                        |
| TIOF\_Time\_Zone\_Area\_\_c                   | TIOF\_Time\_Zone\_Area\_\_c                   |                                                                                               |
|                                               |                                               |                                                                                               |
