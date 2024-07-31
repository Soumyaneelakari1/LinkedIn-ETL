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




