# Markdown Meeting Notes → Google Doc (Google Colab)

## Brief Description
This project contains a Google Colab notebook that converts the provided markdown meeting notes into a well-formatted Google Doc using the **Google Docs API**.  
It applies:
- Heading 1 for the main title (“Product Team Sync”)
- Heading 2 for section headers (“Attendees”, “Agenda”, etc.)
- Heading 3 for sub-section headers (under “Agenda”)
- Nested bullet hierarchy with indentation
- Markdown task checkboxes (`- [ ]`) as **Google Docs checkboxes**
- Distinct styling for assignee mentions (`@name`) (bold + color)
- Distinct styling for footer lines (“Meeting recorded by…”, “Duration…”)

## Required Dependencies
Installed inside Colab:
- `google-api-python-client`
- `google-auth`
- `google-auth-httplib2`
- `google-auth-oauthlib`

## Setup Instructions
1. Open `meeting_notes_to_gdoc.ipynb` in Google Colab.
2. Run the dependency installation cell:
   - `pip install google-api-python-client google-auth google-auth-httplib2 google-auth-oauthlib`
3. Run the authentication cell and approve permissions when prompted.
4. Run the conversion cell. The notebook prints a Google Docs link to the generated document.

> If you see an error about the Google Docs API not being enabled, enable **Google Docs API** in Google Cloud Console for the Google project referenced in the error message.

## How to Run in Colab
- Run the notebook cells **top-to-bottom**:
  1) Install dependencies  
  2) Authenticate and initialize the Docs API client (`docs_service`)  
  3) Provide markdown input (`MARKDOWN_NOTES`)  
  4) Run the converter to generate a new Google Doc  
- The final cell prints:
  - A Google Docs URL for the created document
  - A small verification output confirming `HEADING_1 / HEADING_2 / HEADING_3` on key lines

## Notes / Implementation Decisions
- The markdown title `Product Team Sync - May 15, 2023` is split so:
  - **Heading 1** = `Product Team Sync`
  - The date appears as an italic subtitle line.
- Indentation is derived from leading spaces in markdown. Nesting level is converted into Google Docs indentation (`18pt` per level).
- Headings are applied **after** list formatting to ensure the final Google Doc uses true `HEADING_1/2/3` named styles.
