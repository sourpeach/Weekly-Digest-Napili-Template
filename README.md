# Weekly-Digest-Napili-Template
Custom solution to send weekly digest for forum topics for Napili Template Salesforce Communities

<strong>Problem: </strong>
Salesforce Communities Napili Template offers forum topics as part of its features. The forums functions like chatter feature in Salesforce. Naturally one will assume that receiving weekly digest for the forum topics will be as easy as clicking a box on the profile in chatter however the forum tocpis in Napili Template is actually not technically part of the Chatter interface. It is also not part of the Chatter Answer as well because forum post in Napili template cannot be accessed throught the Salesforce interface. 

<strong>Solution:</strong>
Query the posts from the database and display it in a Visualforce email template. 

1. Create a Apex Class controller(TopicWeeklyDigestController.apxc) to extract out all the posts you need. To do this a bit of 'good to know' information is that the chatter, chatter answer(Questions) and the Napili template forum posts all sit in the object "FeedItem" but categorized in different "Type". The type for the Napili template forum topic is 'QuestionPost' however this type is shared with Questions or ChatterAnswer. For this specific Salesforce org the Chatter Answer was not enabled, therefore query type 'QuestionPost' worked. For Salesforce org that has ChatterAnswer further filter might be needed in their query to separate the Chatter Answer vs Forum Post.

2. Create a Visualforce component(WeeklyDigestComp.vfc) to display all the post content(variables). The code sample shown was to mimic the chatter post format as closely as possible.

3. Embed the Visualforce component into a visualforce email template.
```html
<messaging:emailTemplate subject="Your Visualforce email subject" recipientType="User" > 
    <messaging:htmlEmailBody >
    <c:WeeklyDigestComp /> <!--Visualforce component-->
    </messaging:htmlEmailBody>
</messaging:emailTemplate>
```
4. Finally not included in this repository is the batch processing apex class that sends out the email and scheduling the emails to be sent out on a weekly basis. 
