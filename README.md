# Navya’s Notes

Navya’s Notes is a fictional, read-only notes app for Module 3 of the ACM-W x CRUx data-leak investigation competition. Participants explore everyday notes, archived and deleted material, and an activity history to determine what happened. The interface should feel like a familiar notes product; the notes and logs serve as evidence in the case.

## App experience

The planned app is a responsive, PWA-style website with:

- A home/list view, note detail view, categories, and search
- Archived notes and Trash
- TODO checkboxes shown as part of the evidence
- Settings with version and sync status
- An activity-history screen
- A private-note reveal tied to clues in the notes

The app does not need real authentication or live synchronization. Evidence is read-only: the interface must not edit or overwrite the canonical data.

## Investigation content

The 12-note collection mixes ordinary personal notes and case evidence. Grocery lists and meeting notes provide noise and realism; Thesis TODO, MIRROR Observations, Backup Checklist, Research References, and Archived Diagram Notes point toward the investigation. Don’t Forget and Deleted Draft can initially suggest Navya is responsible. The private note provides context for her activity and helps resolve that false lead.

The activity history has six required events:

| Timestamp | Device | Action |
|---|---|---|
| 13 Oct 22:10 | `NAVYA-MBP` | Edited MIRROR Observations |
| 14 Oct 01:47 | `NAVYA-MBP` | Opened Research References |
| 14 Oct 02:19 | `UNKNOWN-DEVICE-7` | Opened Backup Checklist |
| 14 Oct 02:23 | `UNKNOWN-DEVICE-7` | Attempted archive access |
| 14 Oct 02:35 | `NAVYA-MBP` | Created Private Note |
| 14 Oct 02:42 | `NAVYA-MBP` | Disabled sync |

The hidden note should be discoverable through the story. For example, an archived note can say that “the version number remembers the second device” and direct participants to Settings. There, activating the version number twice reveals the private note. Provide an equivalent keyboard interaction and a visible, accessible hint. The gesture should reward following the evidence rather than guessing.

## Evidence data

The app uses these JSON files as its canonical content:

- `notes.json` — note `id`, `title`, `body`, `category`, `created_at`, `updated_at`, `archived`, and `deleted`
- `activity.json` — `timestamp`, `device_id`, `note_id`, and `action`
- `settings.json` — `version`, `last_sync`, and `sync_enabled`

Use stable note IDs and make every activity `note_id` refer to a note. Keep the private note in the evidence data, but out of ordinary note lists until the reveal. Mark archived and deleted notes distinctly so they appear in the correct sections.

## Development status

This repository currently contains the project README only. The app source, data files, and development scripts have not been added yet, so there are no run or build commands at this stage.

## Work split

The work is divided into three tasks:

1. **UI and navigation** — Build the responsive notes-app layout, home/list view, categories, search, navigation, and note detail screen.
2. **Settings and activity** — Build Settings, sync status, and activity history. Implement the clue-based private-note reveal, including a keyboard equivalent, and connect it to the notes data.
3. **Notes and evidence** — Create the 12 notes and canonical JSON data, including archive/trash status, TODO content, and the six activity entries. Keep IDs and timestamps consistent.

Agree on the data shape and note IDs before implementation so the UI and Settings can integrate smoothly.
