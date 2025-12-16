Button Read me

What you are seeing in your screenshot is Advanced mode, which is the manual configuration path. From here, you will explicitly define the Slack API call. No Copilot, no AI.

Below are the next exact clicks and fields you should see and fill.

What to do next (from this screen)

Open API Endpoints Click the API Endpoints section on the left so it expands.

Choose the Slack method In API Endpoints, select:

chat.postMessage

If you see a dropdown or “Add endpoint” option, choose chat.postMessage.

Configure the request fields Once chat.postMessage is selected, you should see input fields appear.

Fill them as follows:

Channel

Choose your Slack channel (e.g. #approvals)

Text Please review this request.

This is required by Slack even when blocks are used.

Blocks

Paste this JSON verbatim:

[ { "type": "section", "text": { "type": "mrkdwn", "text": "Please review this request." } }, { "type": "actions", "elements": [ { "type": "button", "text": { "type": "plain_text", "text": "Approve" }, "value": "approve_request", "style": "primary" } ] } ]

Do not add a URL.

Ignore Code You do not need to open or write anything in the Code section.

Run Test Click Run Test (bottom right).

You should now see in Slack:

The message text

A green Approve button

Publish Once confirmed, click Publish.

What this gives you

A real Slack button

Sent via Slack’s native API

Fully compatible with Slack → New Interaction trigger

No AI involvement

Next (after this works)

Create a second Zap:

Trigger

App: Slack

Event: New Interaction

This Zap will fire when the button is clicked. Please edit my existing Custom Slack Action that sends the hiring request message.

Do NOT create a new action. Modify the current one.

I want you to:

Remove the static_select dropdown (the “Select a name” field).

Add 5 URL buttons instead, labeled:

Tasha

Maria

MJ

Sito

Diane

Each button must be a URL button (not interactive), using this format:

?assignee=tasha

?assignee=maria

?assignee=mj

?assignee=sito

?assignee=diane

Keep all existing hiring request data in the message (team, hiring manager, job title, links, salary, etc.).

Place the buttons at the bottom of the message under a label like: “Assign recruiter:”

Use placeholder webhook URLs for now — I will replace them later. Button Order and Styles. Tasha: Primary (blue) Diane: Primary (blue) MJ: Danger (red) Sito: Danger (red) Maria: Danger (red) BUILD IT
