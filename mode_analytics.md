# Always name a table 
# Here we want to make sure that we are grouping by that one. This strategy of selecting what we are grouping by is probably a good idea. 

SELECT DATE_TRUNC('week', e.occured_at), 
	COUNT(DISTINCT (e.user_id)) AS weekly_active_users
FROM tutorial.yammer_events e
WHERE e.event_type = 'engagement'
AND e.event_name = 'login'
GROUP BY 1
ORDER BY 1 

# In MYSQL DATE_TRUNC('week', e.occured_at) is equivielant to YEARWEEK(e.occured_at). 
# Event Types are engagement and signup flow

SELECT DATE_TRUNC('week', e.occured_at),
COUNT(*)
FROM tutorial.yammer.events e
WHERE 

# We can select unique pairs with

SELECT DISTINCT a, b FROM pairs;

<!-- event_name	event_type
create_user	signup_flow
search_click_result_3	engagement
search_click_result_1	engagement
search_click_result_2	engagement
home_page	engagement
search_click_result_5	engagement
search_click_result_7	engagement
search_click_result_9	engagement
search_click_result_10	engagement
search_click_result_8	engagement
search_click_result_6	engagement
send_message	engagement
view_inbox	engagement
login	engagement
enter_info	signup_flow
search_run	engagement
like_message	engagement
search_autocomplete	engagement
complete_signup	signup_flow
search_click_result_4	engagement
enter_email	signup_flow -->


# Click THrough Rate here

SELECT week, weekly_opens

<!-- Dealing with division by 0 -->
 weekly_opens/CASE WHEN weekly_emails = 0 THEN 1 ELSE weekly_emails END::FLOAT AS weekly_open_rate,

