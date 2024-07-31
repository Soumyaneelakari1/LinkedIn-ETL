# LinkedIn-ETL-

## Problem Statement
The LinkedIn platform contains extensive and diverse data related to user profiles, connections, posts, comments, likes, shares, and more. Managing, integrating, and analyzing this vast amount of data effectively is challenging, but crucial for deriving actionable insights and enabling real-time decision-making. Leveraging Informatica PowerCenter's ETL capabilities can streamline data processing, ensure data quality, and provide comprehensive analytics and reporting for LinkedIn.

## Objectives
1.Analyze user activity patterns to develop strategies that increase user interaction and reduce churn.<br>
2.Identify the types of content that generate the most engagement and tailor content creation efforts accordingly.<br>
3.Analyze education and career data to provide insights into typical career pathways.<br>
4.Study user connection patterns to enhance features that facilitate networking and collaboration.<br>

## ER Diagram
![image](https://github.com/user-attachments/assets/5e181bc4-03e5-4f6e-94d5-c18031888c25)

## Dataset Description
Users: This table stores basic information about users such as their name, email, password, and registration date.<br><br>
Profiles: Each user has a unique profile, which contains information such as their current job title, industry, location, and summary. The profile table also includes a foreign key linking it to the user who owns it.<br><br>
Connections: This table stores information about the relationships between users, including the user ID of the person making the connection and the user ID of the person they are connecting with. This table also has a status column to indicate whether the connection is pending, accepted, or blocked.<br><br>
Education: This table stores information about the user’s education like school name, degree, field of study, and start and end date. This table also includes a foreign key linking it to the user who owns it.<br><br>
Experience: This table storese information about the user’s work experience company name, job title, location, and start and end date. This table would also include a foreign key linking it to the user who owns it.<br><br>
Skills: This table stores information about the user’s skills. This table would also include a foreign key linking it to the user who owns it.<br><br>
Posts: This table stores information about posts made by users, including the user ID of the person who made the post, the post’s content, and the date it was posted.<br><br>
Comments: This table stores information about comments made on posts, including the user ID of the person who made the comment, the comment’s content, and the date it was posted. It also includes a foreign key linking it to the post it is commenting on.<br><br>
Likes: This table stores information about likes on posts, including the user ID of the person who made the like and the date it was posted. It  also includes a foreign key linking it to the post it is liking on.<br><br>
Shares: This table stores information about shares on posts, including the user ID of the person who made the share and the date it was posted. It also includes a foreign key linking it to the post it is sharing.<br><br>
Groups: This table stores information about groups created by users, including the group name, description, and the user ID of the person who created the group.<br><br>
Group_members: This table stores information about the relationship between groups and users, including the user ID of the person and the group ID they are joining. It also has a status column to indicate whether the request is pending, accepted, or blocked.<br><br>

## Transformations Applied

**1.Users Who Have a Combination of Specific Skills**
![image](https://github.com/user-attachments/assets/a30c9b4e-21d0-4d85-800b-208ffb2f9fc1)

In this transformation, data is extracted from the USERS and SKILLS tables. The Source Qualifier transformations SQ_USERS and SQ_SKILLS prepare the data for further processing. The SQ_USERS source qualifier extracts user information such as USER_ID, EMAIL, PASSWORD, NAME, LOCATION, and JOIN_DATE. The SQ_SKILLS source qualifier extracts skill information including SKILL_ID, USER_ID, and SKILL_NAME.
Two Filter transformations are applied: java filter and python. The java filter transformation filters data to pass through only the rows where the SKILL_NAME matches "Java". The python transformation filters data to pass through only the rows where the SKILL_NAME matches "Python". 
![image](https://github.com/user-attachments/assets/a52e7c0b-9f0c-4c79-96b8-775353d59a13)

Next, Joiner transformations (Joiner and J11) are used to join the filtered data from the USERS and SKILLS tables based on the USER_ID. The Joiner transformation combines data where the SKILL_NAME is "Java", while the J11 transformation combines data where the SKILL_NAME is "Python".
Finally, the relevant data (USER_ID and NAME) from the joined results is loaded into the TARGET_COMB_SKILLS target table, ensuring that only the relevant user information with their respective skills is displayed. This process ensures that the target table TARGET_COMB_SKILLS contains a list of users and their skills, filtered for specific skills like Java and Python.

**2.Top Industries by User Count**
By identifying the industries with the highest user count on LinkedIn, the agency can allocate their marketing resources more effectively, focusing on sectors with the largest potential audience. 
![image](https://github.com/user-attachments/assets/dfd9a1da-9c69-4a0c-a162-ed5bef6c2044)

 
In this transformation, data is extracted from the EXPERIENCE table. The Source Qualifier transformation, SQ_EXPERIENCE, prepares the data for further processing. The Aggregator transformation, AGG, groups the data by COMPANY_NAME and counts the number of users (USER_ID) associated with each company using the expression COUNT(USER_ID). The Rank transformation, R2, then ranks these companies based on the user count in descending order, utilizing the expression COUNT(USER_ID) to assign a RANKINDEX to each company. Finally, the relevant data (COMPANY_NAME and EMPLOYEE_COUNT) is loaded into the TARGET_TOPCOMPANIES target table, ensuring that the top companies by user count are identified and displayed.

**3. Recommend posts to users based on their skills.**
When companies post job openings seeking skills like CSS, Java, and Python, LinkedIn's algorithm prioritizes these posts in the user's feed, ensuring they don't miss relevant career opportunities. Additionally, invitations to webinars, workshops, and conferences related to their skills are highlighted, providing opportunities for networking and staying updated with industry trends.
 ![image](https://github.com/user-attachments/assets/39a7c069-853b-44de-ac2d-9d9601b59ad2)



In this transformation, data is extracted from the SKILLS and POSTS tables. The Source Qualifier transformation joins these tables based on USER_ID and prepares the combined data for further processing. The Filter transformation applies a condition using the expression IIF(INSTR(POSTS.CONTENT, SKILLS.SKILL_NAME) > 0, TRUE, FALSE) to ensure that only posts containing the mentioned skills, such as CSS, are passed through. If a post's content includes "CSS" and the user has CSS listed as a skill, the relevant data (USER_ID, SKILL_NAME, SKILL_ID, and CONTENT) is then loaded into the POSTS_RES target table, ensuring that only relevant posts are displayed for each user's skills.


## Conclusion

The insights derived from our LinkedIn-like system data provide invaluable guidance for strategic decision-making and operational improvements. By analyzing user interactions and behaviors within the platform, we gain a deeper understanding of user preferences and engagement patterns. This knowledge allows us to optimize features and functionalities to better meet user needs, thereby enhancing overall user satisfaction and retention.

