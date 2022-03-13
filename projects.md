# PROJECTS TABLE
## ADMIN
### get all projects
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
### get all projects details
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
### get single project by project id
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
### get single project details by project id
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
###  update single project details by project id
```sql
```

## USER
### get all user projects by user id
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
### get user projects details by user id
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
### update single project by user id and project id
```sql
```
### create new project by user id
```sql
```
