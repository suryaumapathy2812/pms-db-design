# PROJECTS TABLE
## ADMIN
### Get All Projects
```sql
SELECT 
	up.id AS id, 
	u.id AS user_id,
	p.id AS project_id,
	p.name AS project_name,
	up.user_role AS `role`
FROM `user_projects` AS up
JOIN `users` AS u
ON up.user_id = u.id
JOIN `projects` AS p
ON up.project_id = p.id
ORDER BY up.`id`;

```
### Get All Projects Details
```sql
SELECT 
	up.id AS `id`,
	p.id AS `project_id`,
	p.name AS `name`,
	p.description AS `description`,
	p.status AS `status`,
	p.active AS `active`,
	up.user_role AS `role`,
	p.created_by AS `created_by`,
	p.modified_by AS `modified_by`,
	p.created_at AS `created_at`,
	p.modified_at AS`modified_at`

FROM `user_projects` AS up
JOIN `projects` AS p
ON up.project_id = p.id
JOIN `users` AS u
ON up.user_id = u.id

ORDER BY `id`
```
### Get Single Project by Project Id
```sql
# get user's single project details
SELECT 
	up.id AS `id`,
	p.id AS `project_id`,
	p.name AS `name`,
	p.description AS `description`,
	p.status AS `status`,
	p.active AS `active`,
	up.user_role AS `role`,
	p.created_by AS `created_by`,
	p.modified_by AS `modified_by`,
	p.created_at AS `created_at`,
	p.modified_at AS`modified_at`

FROM `user_projects` AS up
JOIN `projects` AS p
ON up.project_id = p.id
JOIN `users` AS u
ON up.user_id = u.id

WHERE p.id = 1

ORDER BY `id`
```
### Get Single Project Details by Project Id
```sql
# get user's single project details
SELECT 
	up.id AS `id`,
	p.id AS `project_id`,
	p.name AS `name`,
	p.description AS `description`,
	p.status AS `status`,
	p.active AS `active`,
	up.user_role AS `role`,
	p.created_by AS `created_by`,
	p.modified_by AS `modified_by`,
	p.created_at AS `created_at`,
	p.modified_at AS`modified_at`

FROM `user_projects` AS up
JOIN `projects` AS p
ON up.project_id = p.id
JOIN `users` AS u
ON up.user_id = u.id

WHERE p.id = 1

ORDER BY `id`
```
###  Update Single Project Details by Project Id and User Id
```sql
UPDATE `projects`
SET `name` = ? , `description` = ? , `modified_by` = ?
WHERE `id` = ?;
```

## USER
### Get All User Projects by User Id
```sql
SELECT 
	up.id AS id, 
	u.id AS user_id,
	p.id AS project_id,
	p.name AS project_name,
	up.user_role AS `role`,

	up.created_at,
	up.modified_at	
	
FROM `user_projects` AS up
JOIN `users` AS u
ON up.user_id = u.id
JOIN `projects` AS p
ON up.project_id = p.id
WHERE u.id = 1
ORDER BY up.`id`;
```
### Get User Projects Details by User Id
```sql
SELECT 
	up.id AS `id`,
	p.id AS `project_id`,
	p.name AS `name`,
	p.description AS `description`,
	p.status AS `status`,
	p.active AS `active`,
	up.user_role AS `role`,
	p.created_by AS `created_by`,
	p.modified_by AS `modified_by`,
	p.created_at AS `created_at`,
	p.modified_at AS`modified_at`

FROM `user_projects` AS up
JOIN `projects` AS p
ON up.project_id = p.id
JOIN `users` AS u
ON up.user_id = u.id
WHERE u.id = 1
ORDER BY `id`
```
### get single project by user id and project id
```sql
# get user's single project details
SELECT 
	up.id AS `id`,
	p.id AS `project_id`,
	p.name AS `name`,
	p.description AS `description`,
	p.status AS `status`,
	p.active AS `active`,
	up.user_role AS `role`,
	p.created_by AS `created_by`,
	p.modified_by AS `modified_by`,
	p.created_at AS `created_at`,
	p.modified_at AS`modified_at`

FROM `user_projects` AS up
JOIN `projects` AS p
ON up.project_id = p.id
JOIN `users` AS u
ON up.user_id = u.id

WHERE u.id = 1
AND p.id = 1

ORDER BY `id`
```

### Create New Project by User Id
```sql
INSERT INTO `projects`
	(`name`, `description`,`created_by`,`modified_by`)
VALUES
	(?,?,?,?);
	
INSERT INTO `user_projects`
	(`user_id`, `project_id`, `user_role`, `created_by`, `modified_by`)
VALUES
	(?,?,?,?,?)
```

### update Project Details by Project Id and User Id
```sql
UPDATE `projects`
SET `name` = ? , `description` = ? , `modified_by` = ?
WHERE `id` = ?;
```

### Update User Role for a Project by Project Id and User Id
```sql
UPDATE `user_projects`
SET `user_role` = ?
WHERE `user_id` = ?, `project_id` = ?;
```


### Get all project users
```sql
SELECT 
	up.id AS id, 
	u.id AS user_id,
	p.id AS project_id,
	p.name AS project_name,
	up.user_role AS `role`,

	up.created_at,
	up.modified_at	
	
FROM `user_projects` AS up
JOIN `users` AS u
ON up.user_id = u.id
JOIN `projects` AS p
ON up.project_id = p.id
WHERE u.id = 1
ORDER BY up.`id`;
```

