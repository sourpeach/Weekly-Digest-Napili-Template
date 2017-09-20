# Weekly-Digest-Napili-Template
Custom solution to send weekly digest for forum topics for Napili Template Salesforce Communities

<strong>Problem: </strong>
Salesforce Communities Napili Template offers forum topics as part of it's features. The forums functions like chatter feature in Salesforce. Naturally one will assume that receiving weekly digest for the forum posts will be as easy as clicking a box on the profile in chatter however the forum tocpis in Napili Template is actually not technically part of the Chatter feature. It is also not part of the Chatter Answer as well because forum post in Napili template cannot be accessed throught the Salesforce interface. 

<strong>Solution:</strong>
Query the posts from the database and display it in a Visualforce email template. 

1. Create a Apex Class controller to pull out all the posts you need. To do this a bit of good to know information is that the chatter, chatter answer(Questions) and the Napili template forum posts all sit in the object "FeedItem" but separt
