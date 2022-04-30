# 🚧 Tags

{% hint style="info" %}
**ShortURL | Playbook | Assistant**
{% endhint %}



{% hint style="warning" %}
**NOTICE**

This documentation page is under construction.\
Should you want to be notified once it's published, [**let us know**](https://tiof.click/TIOFTarianUpdatesService).
{% endhint %}

### Existing Tags

https://docs.google.com/spreadsheets/d/1Q4CSDg3Vg-M7I5pENX1pxPDJckT8H0E2Rrxz2QTZb2g/edit#gid=0

### Requesting a new Tag

Link to Requisition form: https://docs.google.com/forms/d/e/1FAIpQLSfUOuTHpqLD1i7XDXmgvN1se1-9WfL\_FcNKwCCnQg9\_rzGqQQ/viewform

### Creating a new Tag

* Go to TIOF main repo Labels: https://github.com/TheIOFoundation/TIOF/labels
* Create new Tag, following existing code convention (Naming, color, description)
* Dry run Tag replication to all TIOF repos with github-sync.js
* node github-sync.js labels -s TheIOFoundation/TIOF -t TheIOFoundation --token \[INSERT TOKEN] --dry-run
* If all correct, execute Tag replication to all TIOF repos with github-sync.js
* node github-sync.js labels -s TheIOFoundation/TIOF -t TheIOFoundation --token \[INSERT TOKEN]
* Enjoy
