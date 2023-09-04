[API docs](.) /

# Automation Tutorial

This tutorial will show you how to send your first triggered email with a Automation campaign.

### Add a provider and sender
1. Follow [this guideline](../Articles/how-to/add-a-provider) to add a **Provider**.
2. Follow [this guideline](../Articles/how-to/add-a-sender) to add a **Sender**.

### Create a template
1. Login to your SendDolphin account.
2. Choose **Template** from the left menu.
3. Choose **Add template** from the top-right corner.
4. On the **Add template** page, do following:
    * Enter a mail subject.
    * Design a mail body with the drag-n-drop designer.
    * Once done designing the mail body, choose **Publish** button on the top menu bar.
    * Choose the **Exit** button on the top-left corner of the screen to back to the previous page.
5. On the template list, click on the **Edit** icon under the **Nickname** column to rename the template.

### Create a contact list
1. On your SendDolphin account, choose **Contacts** from the left menu.
2. Choose **Add list** from the bottom of the page.
3. On the **Add list** page, enter a name for the list.
4. Choose **Save**, then you will be rediected to the previous page.
5. On the **Contacts** page, you can see the ID of the list you have just created.

### Create an Automation campaign
1. On your SendDolphin account, choose **Automations** from the left menu.
2. Choose **Create campaign** from the top-right corner.
3. On the **Create campaign** page, do following:
    * Name the campaign in the **Campaign name** block.
    * Choose a sender in the **Sender** block.
    * Choose the list you have just added in the **When a contact add to the list** block.
    * In the **Wait (hours)** block, enter 0 as the wait hour. Choose the template you have just added as the mail template under **Send**.
    * Choose **Save** and go back to the previous page.

### Get your API token
1. On your SendDolphin account, choose **API** from the left menu.
2. Click on the **eye** icon to view and copy the API token.

### Call the [Add-contact-to-list API](./contact-add-to-list).
```bash
curl \
  -H "Authorization: Bearer Your.API.Token-HERE" \
  -H 'Content-Type: application/json' \
  -X POST \
  -d '{"email": "example@domian.com", "list_ids":{"The.Contact.List.ID-HERE":1}}' \
  https://senddolphin.com/restful/api/v3/contact
  ```

  ```
  Replace the `The.Contact.List.ID-HERE` with the ID of contact list you have just created.
  ```

### Check the Inbox
Ad email should be delivered into the inbox of "example@domian.com" as you provided in the Add-contact-to-list API call.

