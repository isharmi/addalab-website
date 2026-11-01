# AddaLab deployment

The website was moved from the extra AddaLab_Mentoring_Netlify_Ready directory to the repository root. All six original website files were preserved byte-for-byte, including styling, content, prices, branding, and the homepage Google Forms registration integration.

The mentoring form already contained name="mentoring-request", method="POST", data-netlify="true", a matching hidden form-name input, netlify-honeypot="bot-field", and a hidden bot-field input. Its action remained /mentoring/thanks/, and mentoring/thanks/index.html was included at that exact location. No JavaScript intercepts this form. No build step or SPA redirect is required.

Manual deployment and testing

1. Use the existing AddaLab project in Netlify. Do not create a new project or change DNS or the custom domain.
2. Extract AddaLab-deploy-ready.zip. Deploy the extracted folder whose immediate contents include index.html, resources.html, robots.txt, sitemap.xml, and mentoring/. Do not select a parent folder. If your manual deployment interface accepts ZIPs directly, the supplied archive already has index.html at its top level.
3. Netlify form detection must be enabled before the deployment that registers the form. Check Forms in the existing project. If detection is disabled, enabling it changes project settings and requires the owner's confirmation; then enable it and redeploy this same folder. Uploading HTML alone cannot enable a disabled server-side form detector. No project settings or deployment were changed during this repair.
4. After deployment, verify /, /resources, /mentoring/, and /mentoring/thanks/ load. In Forms, confirm mentoring-request is listed.
5. Open /mentoring/ and submit one request using your real email and a meaningful description. Complete the required fields and both checkboxes; leave the hidden honeypot empty. Confirm the browser reaches /mentoring/thanks/ and the request appears under mentoring-request in Netlify Forms. If absent, check Spam. The thank-you page alone does not prove a submission was stored.
6. Confirm the homepage registration form still posts to Google Forms. Its URL, field names, hidden iframe, and success behavior were preserved. No test submission was sent to either service during this repair.

Validation and observations

All four HTML pages were inspected. Sixteen local HTML links, form targets, and anchors resolved against the deployment files; the existing TOP button uses its scroll handler. The supplied archive and the final website files were compared byte-for-byte. Archive paths and CRC integrity were checked.

Public read-only checks on 2026-11-01 returned HTTP 200 for /, /mentoring/, and /mentoring/thanks/. The reported live thank-you 404 was therefore not reproducible during this inspection. The live mentoring markup still carried data-netlify="true", suggesting the last deployment may not have processed the form; registration requires checking the existing project's Forms screen after deployment. No authenticated settings changes or production submissions were made.

The original homepage references /addalab-fb-cover-v2.jpg in social-preview metadata. That image was not included in the attachment and its live URL returned 404. The reference was preserved to avoid changing branding. Restoring the original image at that path is a separate remaining asset issue; it does not prevent form handling or page navigation.
