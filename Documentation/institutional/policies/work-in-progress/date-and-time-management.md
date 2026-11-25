---
description: Version 0.1 | This Policy has not been approved yet.
---

# 🚧 Date and time management

## Introduction

This Policy sets one way of writing time everywhere The IO Foundation structures data by time: GitBook, Google Drive, Canva, Calendars, ERPNext and the CRM. It applies to all TIOF Members.

## Policy details

### 1. Time

* Every stored time is UTC.
* A calendar is local only when it is meant to follow the local day of its people (for example the Argos Club calendars of Indonesia use Asia/Jakarta).

### 2. Seasons

* A Season is a natural calendar year in UTC. No Activity spans two Seasons.
* A record belongs to the Season and the month of its start timestamp (UTC).
* Seasons and Fiscal Years are different concepts that deliberately coincide.
* A Season with no information is hidden from the sidebar and is unhidden when it gets its first Activity page.

### 3. Names that people read (titles)

* Seasons: `Season 2026`. Months: `11 - November` (zero-padded number, English long name).
* Activities: `[#Tag] Full event name YYYY-MM-DD`, with the date after the name.
* `00` means the whole period: `2026-02-00` is the whole month and `2026-00-00` the whole year.
* A year inside an official or edition name (`APRICOT 2026`) is a name, not a date.
* When the organizer's own name already identifies the event uniquely, we keep it.
* Tag codes come from the CRM and are written with `#`. The legacy `[ADM]` prefix (administration) stays.
* An Activity has an internal title and an audience Subtitle (for example "Discovering ICANN").

### 4. Names that machines read (slugs and paths)

* Paths are permanent: `calendar/all-seasons/season-YYYY/NN-month/...`.
* A slug is generated from the same facts as the title (date, series, city) and always matches them. If the date or the name changes, the slug changes too; GitBook keeps the old address working.

### 5. Files

* `[TIOF] Team [X] YYYY-MM-DD Title LANG vX.Y`. The date slot is always present (`0000-00-00` when there is none).
* The bracket letter `[X]` is the confidentiality level (levels to be defined).
* Reports: `YYYY-MM-DD_HHMMSSz-<source id>.md` in `channels/<channel>/season-YYYY/MM-month/`.

### 6. Calendars

* Calendars are long-lived containers named by Team, Project, Habitat or Channel. A Season never appears in a calendar name.
* Calendars made for one Activity or one person are archived (hidden and unshared) when the Activity ends.

### 7. Pending information

* `@@@PENDING` means pending information to arrange. It sits at the bottom of a Space's pages.

## Meetings

### Regular meetings

All regular meetings need to be set latest 1 week before the beginning of a new month.

### Scheduling meetings

The IO Foundation requires the coordinated efforts of TIOF Members who are located in different countries around the world. In addition, several countries observe Daylight Saving Time (DST) when local times shift by one hour forward or back depending on the season. This adds more complexity to coordinating meetings. The total number of potential time zones means that setting meeting times agreed upon creates a complex problem.

To reduce the difficulties of finding mutually convenient meeting times TIOF shall implement a scheduling platform that will simplify these processes no matter how many attendees there are or where they are located.

## Review and Amendments

This policy shall be reviewed regularly to ensure its continued relevance and effectiveness. Amendments follow the procedures described in TIOF's Statute.
