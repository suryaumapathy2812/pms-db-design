# REPOSITORIES TABLE

## ADMIN
### get all repositories
```sql
SELECT 
	ur.id AS id,
	u.id AS user_id,
	r.id AS repo_id,
	r.username AS `username`,
	r.repo_name AS `repo_name`,
	ur.user_role AS `role`,

	ur.created_at,
	ur.modified_at
	
FROM `user_repositories` AS ur
JOIN `users` AS u
ON ur.user_id = u.id
JOIN `repositories` AS r
ON ur.repo_id = r.id
ORDER BY ur.`id`;
```
### get all repositories with details
```sql
```
### get single repository by repo id
```sql
```
### get single repository details by repo id
```sql
```
### update single repository details  by repo id
```sql
```


USER
### get all repositories by user id
```sql
SELECT 
	ur.id AS id,
	u.id AS user_id,
	r.id AS repo_id,
	r.username AS `username`,
	r.repo_name AS `repo_name`,
	ur.user_role AS `role`,

	ur.created_at,
	ur.modified_at
	
FROM `user_repositories` AS ur
JOIN `users` AS u
ON ur.user_id = u.id
JOIN `repositories` AS r
ON ur.repo_id = r.id
WHERE u.id = 1
ORDER BY ur.`id`

```
### get all repositories details by user id
```sql
```
### get single repository by user id and repo id
```sql
```
### get single repository details by user id and repo id
```sql
```
### update single repository details by user id and repo id
```sql
```
### create new repository by user id
```sql
```

### Get all repository users
```sql
SELECT 
	ur.id AS id,
	r.id AS repo_id,
	r.username AS `username`,
	r.repo_name AS `repo_name`,
	u.id AS user_id,
	ur.user_role AS `role`,

	ur.created_at,
	ur.modified_at
	
FROM `user_repositories` AS ur
JOIN `users` AS u
ON ur.user_id = u.id
JOIN `repositories` AS r
ON ur.repo_id = r.id
WHERE r.id = 1
ORDER BY ur.`id`
```

### Get all repos by user id and project id
