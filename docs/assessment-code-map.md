# DYDD Assessment Code Map

This folder organizes the PDFMonkey report templates and Make mapping/payload code for the three DYDD assessments.

## Structure

- `assessments/spiritual-gifts/pdfmonkey-report.html` — main PDFMonkey report template for the Spiritual Gifts report.
- `assessments/spiritual-gifts/make-direct-mapping.html` — older/direct Make field-mapped HTML version from the uploaded note.
- `assessments/designid/pdfmonkey-report.html` — PDFMonkey report template for DesignID.
- `assessments/designid/make-json-payload.json` — Make JSON payload/mapping for DesignID.
- `assessments/designpd/pdfmonkey-report.html` — PDFMonkey report template for DesignPD.
- `assessments/designpd/make-json-payload.json` — Make JSON payload/mapping for DesignPD.
- `raw/DYDD_Assessment_codes.txt` — original uploaded assessment-code note, preserved as received.

## Notes

The Make payload files include Make-style placeholders such as `{{10.Name}}` and `{{20.`0`}}`. They are stored as source templates, not as strict static JSON for direct parsing outside Make.

The Spiritual Gifts upload labels one section as JSON, but the content is actually an HTML report template with direct Make field references. It is stored as `make-direct-mapping.html` to keep the repo naming accurate.
