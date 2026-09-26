# CORTEX | Teal-branded survey website

This updated website uses the uploaded original CORTEX logo (teal and charcoal), matching teal/white interface, and the **same 17 questions and Google Apps Script backend** as the prior package.

## Package contents

- `Index.html`: ready to paste into Google Apps Script as an HTML file named `Index`. The optimized logo is embedded as an image data URI, so no public hosting is needed.
- `Code.gs`: unchanged backend; stores live submissions as actual Google Form responses and also links a Google Sheet.
- `cortex-logo.png`: standalone, tightly cropped logo for other uses.
- `questions.json`: the unchanged survey questions.
- `preview.png`: optional screenshot of desktop preview.

## For an existing deployment

1. Open your existing CORTEX Google Apps Script project.
2. Open the **Index** HTML file, replace its contents with the new `Index.html`, and Save. **Keep your existing `Code.gs` and script properties**; there is no need to run setup again for a design-only update.
3. Select **Deploy → Manage deployments → Edit (pencil) → Version: New version → Deploy**. The existing `/exec` URL then serves the refreshed interface.
4. Open the public web app URL and verify branding and one test submission. Label and remove test responses before real research.

## For a new deployment

1. Create a project at https://script.google.com/ and paste `Code.gs` into its script file.
2. Add an HTML file named `Index` and paste the whole content of `Index.html`.
3. Save. Select `setupCortexSurvey_` in the editor and run once, authorizing the required Forms and Sheets permissions. The function logs your Form and Sheet links. Running it again reuses the existing form.
4. **Deploy → New deployment → Web app**, choose **Execute as: Me**, and a respondent access level permitted by your account / Workspace.
5. Open the `/exec` web app URL, check form and Sheet response logging, and then share the URL with respondents.

The offline HTML is a **visual preview only**; it intentionally disables saving. The old 12 sample records were not submitted. Survey answers are real only after respondents submit through your deployed web app. Google Forms gives submissions actual receipt timestamps, not manually chosen historic dates.

Do not create a new form unnecessarily when upgrading only the website appearance. The backend still uses `google.script.run` and `FormResponse.submit()` and no API key or third-party database is required.
