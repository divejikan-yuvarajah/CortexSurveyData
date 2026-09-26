# CORTEX | Teal-branded survey website

Public survey site: **https://cortex-surveydata.vercel.app/**

The live site is hosted on Vercel from this repository. It shows the teal CORTEX survey (17 questions). Saving answers still requires the Google Apps Script web app (`Code.gs` plus this page). On Vercel the form runs in preview mode and does not store responses.

## Package contents

- `index.html`: the survey page. Vercel serves this file at the site root. To use it in Google Apps Script, paste it into an HTML file named `Index`. The logo is embedded as an image data URI.
- `cortex-logo.png`: standalone, tightly cropped logo for other uses.

## Vercel

The production URL is https://cortex-surveydata.vercel.app/. Pushes to `main` on https://github.com/divejikan-yuvarajah/CortexSurveyData redeploy that site. The entry file must stay named `index.html` (lowercase). Vercel does not serve `Index.html` at `/`.

## For an existing Google Apps Script deployment

1. Open your existing CORTEX Google Apps Script project.
2. Open the **Index** HTML file, replace its contents with `index.html`, and Save. **Keep your existing `Code.gs` and script properties**; there is no need to run setup again for a design-only update.
3. Select **Deploy → Manage deployments → Edit (pencil) → Version: New version → Deploy**. The existing `/exec` URL then serves the refreshed interface.
4. Open the public web app URL and verify branding and one test submission. Label and remove test responses before real research.

## For a new Google Apps Script deployment

1. Create a project at https://script.google.com/ and paste `Code.gs` into its script file.
2. Add an HTML file named `Index` and paste the whole content of `index.html`.
3. Save. Select `setupCortexSurvey_` in the editor and run once, authorizing the required Forms and Sheets permissions. The function logs your Form and Sheet links. Running it again reuses the existing form.
4. **Deploy → New deployment → Web app**, choose **Execute as: Me**, and a respondent access level permitted by your account / Workspace.
5. Open the `/exec` web app URL, check form and Sheet response logging, and then share the URL with respondents.

The Vercel site is a **visual preview only**; it intentionally disables saving. Survey answers are stored only after respondents submit through the deployed Google Apps Script web app. Google Forms gives submissions actual receipt timestamps, not manually chosen historic dates.

Do not create a new form unnecessarily when upgrading only the website appearance. The backend still uses `google.script.run` and `FormResponse.submit()` and no API key or third-party database is required.
