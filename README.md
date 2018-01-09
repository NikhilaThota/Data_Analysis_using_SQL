Yammer is a social network for communicating with coworkers. Individuals share documents, updates, and ideas by posting them in groups. Yammer is free to use indefinitely, but companies must pay license fees if they want access to administrative controls, including integration with user management systems like ActiveDirectory. Yammer analysts are trained to constantly consider the value of each individual project; they seek to maximize the return on their time. Analysts typically opt for less precise solutions to problems if it means investing substantially less time as well.They are also taught to consider the impact of everything on the company at large. This includes high-level decision making like choosing which projects to prioritize. It also influences the way analysts think about metrics. Product decisions are always evaluated against core engagement, retention, and growth metrics in addition to product-specific usage metrics (like, for example, the number of times someone views another user’s profile).
The goal of this project is to determine a dip caused in the number of engaged users (Yammer defines engagement as having made some type of server call by interacting with the product) in the last week of July. 
Tables used are:  
a.) Users: Includes user's account. 
- user_id:	A unique ID per user. Can be joined to user_id in either of the other tables.
- created_at:	The time the user was created (first signed up)
- state:	The state of the user (active or pending)
- activated_at:	The time the user was activated, if they are active
- company_id:	The ID of the user's company
- language:	The chosen language of the user

b.) Events: Includes login events, messaging events, search events, events logged as users progress through a signup funnel, events around received emails. 
- user_id:	The ID of the user logging the event. Can be joined to user\_id in either of the other tables.
- occurred_at:	The time the event occurred.
- event_type:	The general event type. There are two values in this dataset: "signup_flow", which refers to anything occuring during the process of a user's authentication, and "engagement", which refers to general product usage after the user has signed up for the first time.
- event_name:	The specific action the user took. Possible values include:
- create_user: User is added to Yammer's database during signup process
- enter_email: User begins the signup process by entering her email address
- enter_info: User enters her name and personal information during signup process
- complete_signup: User completes the entire signup/authentication process
- home_page: User loads the home page
- like_message: User likes another user's message
- login: User logs into Yammer
- search_autocomplete: User selects a search result from the autocomplete list
- search_run: User runs a search query and is taken to the search results page
- search_click_result_X: User clicks search result X on the results page, where X is a number from 1 through 10.
- send_message: User posts a message
- view_inbox: User views messages in her inbox
- location:	The country from which the event was logged (collected through IP address).
- device:	The type of device used to log the event.

c.) Email Events: Contains events specific to the sending of emails. 
- user_id:	The ID of the user to whom the event relates. Can be joined to user_id in either of the other tables.
- occurred_at:	The time the event occurred.
- action:	The name of the event that occurred. "sent_weekly_digest" means that the user was delivered a digest email showing relevant conversations from the previous day. "email_open" means that the user opened the email. "email_clickthrough" means that the user clicked a link in the email.

Advanced SQL queries are used to combine all the tables to extract meaningful information in order ot investrgate the sudden drop in user engagement. 
