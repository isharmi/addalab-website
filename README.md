# AddaLab deployment

The website was moved from the extra AddaLab_Mentoring_Netlify_Ready directory to the repository root. All six original website files were preserved byte-for-byte, including styling, content, prices, branding, and the homepage Google Forms registration integration.

The mentoring form already contained name="mentoring-request", method="POST", data-netlify="true", a matching hidden form-name input, netlify-honeypot="bot-field", and a hidden bot-field input. Its action remained /mentoring/thanks/, and mentoring/thanks/index.html was included at that exact location. No JavaScript intercepts this form. No build step or SPA redirect is required.

Manual deployment and testing

1. Use the existing AddaLab project in Netlify. Do not create a new project or change DNS or the custom domain.
2. Extract AddaLab-deploy-ready.zip. Deploy the extracted folder whose immediate contents include index.html, resources.html, robots.txt, sitemap.xml, and mentoring/. Do not select a parent folder. If your manual deployment interface accepts ZIPs directly, the supplied archive already has index.html at its top level.
3. Netlify form detection must be enabled before the deployment that registers the form. The existing project configuration reports form detection enabled. Keep it enabled for the manual deployment; uploading HTML alone cannot enable a disabled server-side form detector. No deployment was performed while preparing this update.
4. After deployment, verify /, /resources, /mentoring/, and /mentoring/thanks/ load. In Forms, confirm mentoring-request is listed.
5. Open /mentoring/ and submit one request using your real email and a meaningful description. Complete the required fields and both checkboxes; leave the hidden honeypot empty. Confirm the browser reaches /mentoring/thanks/ and the request appears under mentoring-request in Netlify Forms. If absent, check Spam. The thank-you page alone does not prove a submission was stored.
6. Confirm the homepage registration form still posts to Google Forms. Its URL, field names, hidden iframe, and success behavior were preserved. No test submission was sent to either service during this repair.

Validation and observations

All four HTML pages were inspected. Sixteen local HTML links, form targets, and anchors resolved against the deployment files; the existing TOP button uses its scroll handler. The supplied archive and the final website files were compared byte-for-byte. Archive paths and CRC integrity were checked.

Public read-only checks on 2026-11-01 returned HTTP 200 for /, /mentoring/, and /mentoring/thanks/. The reported live thank-you 404 was therefore not reproducible during this inspection. The live mentoring markup still carried data-netlify="true", suggesting the last deployment may not have processed the form; registration requires checking the existing project's Forms screen after deployment. No authenticated settings changes or production submissions were made.

The original homepage references /addalab-fb-cover-v2.jpg in social-preview metadata. That image was not included in the attachment and its live URL returned 404. The reference was preserved to avoid changing branding. Restoring the original image at that path is a separate remaining asset issue; it does not prevent form handling or page navigation.


WhatsApp integration update

The mentoring application now requires Student WhatsApp Number in international format: + followed by the country code and number, with 7–15 digits total and no spaces. The field is named student-whatsapp and is included in the existing mentoring-request Netlify form. A privacy note limits use of the number to discussing the student's mentoring request.

All four pages include an accessible floating WhatsApp chat link to +8801822604437 with the prefilled message: "Hello AddaLab, I would like to know more about your ML mentoring service." Existing WhatsApp text links use the same message. The shared whatsapp.css file is required and is included in the updated ZIP. Existing prices, page content, Google Forms registration, and the mentoring form's POST action, form name, honeypot, and consent fields were preserved.

The updated AddaLab-deploy-ready.zip contains only the deployable website files, with index.html at its root. Deploy manually only after approval. After deployment, check that a real mentoring request includes student-whatsapp in Netlify Forms; no live submissions were sent during preparation.
