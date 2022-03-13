# USER TABLE

```sql
DROP TABLE `users`;
```
```sql
CREATE TABLE `users`(
	`id` TINYINT PRIMARY KEY AUTO_INCREMENT,
	`first_name` VARCHAR(50) NOT NULL,
	`last_name` VARCHAR(50) NOT NULL,
	`email` VARCHAR(100) NOT NULL,
	`status` VARCHAR(10) NOT NULL DEFAULT 'CREATED',  # CREATED/ARCHIVED
	`active` BOOLEAN NOT NULL DEFAULT TRUE,
	`created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
	`modified_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
	UNIQUE (`email`)
);
```
```sql
INSERT INTO `users`(`first_name`, `last_name`, `email`) VALUES ( 'Surya', 'Umapathy','suryaumapathy2812@gmail.com'  );
INSERT INTO `users`(`first_name`, `last_name`, `email`) VALUES ( 'Naresh', 'Kumar','nareshkumarh@live.com'  );
INSERT INTO `users`(`first_name`, `last_name`, `email`) VALUES ( 'yasin', 'Md','yasin@yahoo.in'  );
```

# PROJECTS
```sql
DROP TABLE `projects`;
```
```sql
CREATE TABLE `projects`(
	`id` TINYINT PRIMARY KEY AUTO_INCREMENT,
	`name` VARCHAR(50) NOT NULL,
	`description` TEXT NOT NULL,
	
	`status` VARCHAR(10) NOT NULL DEFAULT 'CREATED', # CREATED/ARCHIVED
	`active` BOOLEAN NOT NULL DEFAULT TRUE,

	`created_by` TINYINT NOT NULL,
	`modified_by` TINYINT NOT NULL,

	
	`created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
	`modified_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
	UNIQUE (`name`),
	
	FOREIGN KEY (`created_by`) REFERENCES users(`id`),
	FOREIGN KEY (`modified_by`) REFERENCES users(`id`)
);
```
```sql
INSERT INTO `projects`(`name`, `description`,created_by, modified_by) VALUES ('project_1', 'test project 1',1,1);
INSERT INTO `projects`(`name`, `description`,created_by, modified_by) VALUES ('project_2', 'test project 2',1,1);
INSERT INTO `projects`(`name`, `description`,created_by, modified_by) VALUES ('project_3', 'test project 3',2,2);
INSERT INTO `projects`(`name`, `description`,created_by, modified_by) VALUES ('project_4', 'test project 4',2,2);
```


# REPOSITORIES
```sql
DROP TABLE `repositories`;
```
```sql
CREATE TABLE `repositories`(
	`id` TINYINT PRIMARY KEY AUTO_INCREMENT,
	`username` VARCHAR(50) NOT NULL,
	`repo_name` VARCHAR(100) NOT NULL,
	`repo_url` TEXT NOT NULL,
	 
	`status` VARCHAR(10) NOT NULL DEFAULT 'CREATED', # CREATED/ARCHIVED
	`active` BOOLEAN NOT NULL DEFAULT TRUE,
	
	`created_by` TINYINT NOT NULL,
	`modified_by` TINYINT NOT NULL,
	
	
	`created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
	`modified_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
	UNIQUE (`username`, `repo_name`),
	
	FOREIGN KEY (`created_by`) REFERENCES users(`id`),
	FOREIGN KEY (`modified_by`) REFERENCES users(`id`)
);
```
```sql
INSERT INTO `repositories`(`username`, `repo_name`, `repo_url`,created_by, modified_by) VALUES ('suryaumapathy2812', 'repo_1', 'url_1' ,1,1);
INSERT INTO `repositories`(`username`, `repo_name`, `repo_url`,created_by, modified_by) VALUES ('suryaumapathy2812', 'repo_2', 'url_1',1,1);
INSERT INTO `repositories`(`username`, `repo_name`, `repo_url`,created_by, modified_by) VALUES ('nareshkumar-h', 'repo_3', 'url_3',2,2);
INSERT INTO `repositories`(`username`, `repo_name`, `repo_url`,created_by, modified_by) VALUES ('nareshkumar-h', 'repo_4', 'url_4',2,2);
```

# USER PROJECTS
```sql
DROP TABLE `user_projects`;
```
```sql
CREATE TABLE `user_projects`(
	`id` TINYINT PRIMARY KEY AUTO_INCREMENT,
	`user_id` TINYINT NOT NULL,
	`project_id` TINYINT NOT NULL,
	
	`user_role` VARCHAR(15) NOT NULL, # owner/collaborator
	
	`created_by` TINYINT NOT NULL,
	`modified_by` TINYINT NOT NULL,
	
	`created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
	`modified_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
	UNIQUE (`user_id`, `project_id`),
	UNIQUE (`project_id`, `user_role`),

	FOREIGN KEY (`user_id`) REFERENCES users(`id`),
	FOREIGN KEY (`project_id`) REFERENCES projects(`id`),	
	
	FOREIGN KEY (`created_by`) REFERENCES users(`id`),
	FOREIGN KEY (`modified_by`) REFERENCES users(`id`)
);
```
```sql
# OWNERS
INSERT INTO `user_projects`(`user_id`, `project_id`, `user_role`,created_by, modified_by) VALUES ( 1,1,'OWNER',1,1 ); 
INSERT INTO `user_projects`(`user_id`, `project_id`, `user_role`,created_by, modified_by) VALUES ( 1,2,'OWNER',1,1 ); 
INSERT INTO `user_projects`(`user_id`, `project_id`, `user_role`,created_by, modified_by) VALUES ( 2,3,'OWNER',2,2 ); 
INSERT INTO `user_projects`(`user_id`, `project_id`, `user_role`,created_by, modified_by) VALUES ( 2,4,'OWNER',2,2 ); 
# COLLABORATORS
INSERT INTO `user_projects`(`user_id`, `project_id`, `user_role`,created_by, modified_by) VALUES ( 1,3,'COLLABORATOR',2,2 ); 
INSERT INTO `user_projects`(`user_id`, `project_id`, `user_role`,created_by, modified_by) VALUES ( 1,4,'COLLABORATOR',2,2 );
INSERT INTO `user_projects`(`user_id`, `project_id`, `user_role`,created_by, modified_by) VALUES ( 2,1,'COLLABORATOR',1,1 ); 
INSERT INTO `user_projects`(`user_id`, `project_id`, `user_role`,created_by, modified_by) VALUES ( 2,2,'COLLABORATOR',1,1 );  
```

# USER REPOSITORIES

```sql
DROP TABLE `user_repositories`;
```
```sql
CREATE TABLE `user_repositories`(
	`id` TINYINT PRIMARY KEY AUTO_INCREMENT,
	`user_id` TINYINT NOT NULL,
	`repo_id` TINYINT NOT NULL,

	`user_role` VARCHAR(15) NOT NULL, # owner/collaborator	
	
	`created_by` TINYINT NOT NULL,
	`modified_by` TINYINT NOT NULL,
	
	`created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
	`modified_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
	UNIQUE (`user_id`, `repo_id`),
	UNIQUE (`repo_id`, `user_role`),

	FOREIGN KEY (`user_id`) REFERENCES users(`id`),
	FOREIGN KEY (`repo_id`) REFERENCES repositories(`id`),
	
	FOREIGN KEY (`created_by`) REFERENCES users(`id`),
	FOREIGN KEY (`modified_by`) REFERENCES users(`id`)
);
```
```sql
# OWNERS
INSERT INTO `user_repositories`(`user_id`, `repo_id`, `user_role`,created_by, modified_by) VALUES ( 1,1,'OWNER',1,1 ); 
INSERT INTO `user_repositories`(`user_id`, `repo_id`, `user_role`,created_by, modified_by) VALUES ( 1,2,'OWNER',1,1 ); 
INSERT INTO `user_repositories`(`user_id`, `repo_id`, `user_role`,created_by, modified_by) VALUES ( 2,3,'OWNER',2,2 ); 
INSERT INTO `user_repositories`(`user_id`, `repo_id`, `user_role`,created_by, modified_by) VALUES ( 2,4,'OWNER',2,2 ); 
# COLLABORATORS
INSERT INTO `user_repositories`(`user_id`, `repo_id`, `user_role`,created_by, modified_by) VALUES ( 1,3,'COLLABORATOR',2,2 ); 
INSERT INTO `user_repositories`(`user_id`, `repo_id`, `user_role`,created_by, modified_by) VALUES ( 1,4,'COLLABORATOR',2,2 ); 
INSERT INTO `user_repositories`(`user_id`, `repo_id`, `user_role`,created_by, modified_by) VALUES ( 2,1,'COLLABORATOR',1,1 ); 
INSERT INTO `user_repositories`(`user_id`, `repo_id`, `user_role`,created_by, modified_by) VALUES ( 2,2,'COLLABORATOR',1,1 ); 
```

# PROJECT REPOSITORIES
```sql
DROP TABLE `project_repositories`;
```
```sql
CREATE TABLE `project_repositories`(
	`id` TINYINT PRIMARY KEY AUTO_INCREMENT,
	`project_id` TINYINT NOT NULL,
	`repo_id` TINYINT NOT NULL,
	
	`created_by` TINYINT NOT NULL,
	`modified_by` TINYINT NOT NULL,


	`created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
	`modified_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
	UNIQUE (`project_id`, `repo_id`),

	FOREIGN KEY (`project_id`) REFERENCES projects(`id`),
	FOREIGN KEY (`repo_id`) REFERENCES repositories(`id`),
	
	FOREIGN KEY (`created_by`) REFERENCES users(`id`),
	FOREIGN KEY (`modified_by`) REFERENCES users(`id`)
);
```
```sql
INSERT INTO `project_repositories`(`project_id`, `repo_id`,created_by, modified_by) VALUES (1,1,1,1);
INSERT INTO `project_repositories`(`project_id`, `repo_id`,created_by, modified_by) VALUES (2,2,1,1);
INSERT INTO `project_repositories`(`project_id`, `repo_id`,created_by, modified_by) VALUES (3,3,2,2);
INSERT INTO `project_repositories`(`project_id`, `repo_id`,created_by, modified_by) VALUES (4,4,2,2);
```



