select * from users limit 20;
select * from progress limit 20;

/* What are the Top 25 schools (.edu domains)? */
select email_domain as Top25schools, count(user_id) as users from users group by 1 order by 2 desc limit 25;

/* How many .edu learners are located in New York? */
select count(user_id) NewYorkLearnes from users where city='New York';

/* How many of these Codecademy learners are using the mobile app?*/
select count(*) MobileAppLearnes from users where mobile_app='mobile-user' and mobile_app is not NULL; 

/* Query for the sign up counts for each hour*/
select strftime('%H', sign_up_at) as Hour, count(*) as countForHour from users group by 1;

/*Do different schools (.edu domains) prefer different courses?*/
select u.email_domain, 
count(p.learn_cpp),
count(p1.learn_sql),
count(p2.learn_html),
count(p3.learn_javascript),
count(p4.learn_java)
from users u 
left join progress p on u.user_id = p.user_id and length(p.learn_cpp)>1
left join progress p1 on u.user_id = p1.user_id and length(p1.learn_sql)>1
left join progress p2 on u.user_id = p2.user_id and length(p2.learn_html)>1 
left join progress p3 on u.user_id = p3.user_id and length(p3.learn_javascript)>1
left join progress p4 on u.user_id = p4.user_id and length(p4.learn_java)>1
group by 1 
order by 1 limit 25;

/* What courses are the New Yorkers and Chicago students taking?*/
select u.city, 
count(p.learn_cpp),
count(p1.learn_sql),
count(p2.learn_html),
count(p3.learn_javascript),
count(p4.learn_java)
from users u
left join progress p on u.user_id = p.user_id and length(p.learn_cpp)>1
left join progress p1 on u.user_id = p1.user_id and length(p1.learn_sql)>1 
left join progress p2 on u.user_id = p2.user_id and length(p2.learn_html)>1 
left join progress p3 on u.user_id = p3.user_id and length(p3.learn_javascript)>1 
left join progress p4 on u.user_id = p4.user_id and length(p4.learn_java)>1 
group by 1
having u.city='New York' or u.city='Chicago'
order by 1 desc;
