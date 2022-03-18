# REPOSITORIES TABLE

## ADMIN
### Get All repositories
```sql
SELECT 
	pr.id AS id,
	pr.project_id AS project_id,
	pr.repo_id AS repo_id,
	
	r.username AS repo_username,
	r.repo_name AS repo_name,
	r.repo_url AS repo_url,
	
	r.created_at AS created_at,
	r.modified_at AS modified_at
		
FROM `project_repositories` AS pr
JOIN `projects` AS p
ON pr.project_id = p.id
JOIN `repositories` AS r
ON pr.repo_id = r.id
ORDER BY `id`
```
### Get All Repositories by Project Id
```sql
SELECT 
	pr.id AS id,
	pr.project_id AS project_id,
	pr.repo_id AS repo_id,
	
	r.username AS repo_username,
	r.repo_name AS repo_name,
	r.repo_url AS repo_url,
	
	r.created_at AS created_at,
	r.modified_at AS modified_at
		
FROM `project_repositories` AS pr
JOIN `projects` AS p
ON pr.project_id = p.id
JOIN `repositories` AS r
ON pr.repo_id = r.id
WHERE p.id = ?
ORDER BY `id`
```
### Get repository by Project Id and Repo Id
```sql
SELECT 
	pr.id AS id,
	pr.project_id AS project_id,
	pr.repo_id AS repo_id,
	
	r.username AS repo_username,
	r.repo_name AS repo_name,
	r.repo_url AS repo_url,

	up.user_id AS user_id,
	up.user_role AS user_role,
	
	r.created_at AS created_at,
	r.modified_at AS modified_at
		
FROM `project_repositories` AS pr
JOIN `projects` AS p
ON pr.project_id = p.id
JOIN `repositories` AS r
ON pr.repo_id = r.id
JOIN `user_projects` AS up
ON pr.project_id = up.project_id
JOIN `users` AS u
ON up.user_id = u.id
WHERE p.id = ?
AND r.id = ?
```


## USER
### Get All Project Repositories by Project Id and User Id
```sql
SELECT 
	pr.id AS id,
	pr.project_id AS project_id,
	pr.repo_id AS repo_id,
	
	r.username AS repo_username,
	r.repo_name AS repo_name,
	r.repo_url AS repo_url,

	up.user_id AS user_id,
	up.user_role AS user_role,
	
	r.created_at AS created_at,
	r.modified_at AS modified_at
		
FROM `project_repositories` AS pr
JOIN `projects` AS p
ON pr.project_id = p.id
JOIN `repositories` AS r
ON pr.repo_id = r.id
JOIN `user_projects` AS up
ON pr.project_id = up.project_id
JOIN `users` AS u
ON up.user_id = u.id
WHERE p.id = ?
AND u.id = ?
ORDER BY `id`
```

### Get Project Repository by Project Id, User Id and Repository Id
```sql
SELECT 
	pr.id AS id,
	pr.project_id AS project_id,
	pr.repo_id AS repo_id,
	
	r.username AS repo_username,
	r.repo_name AS repo_name,
	r.repo_url AS repo_url,

	up.user_id AS user_id,
	up.user_role AS user_role,
	
	r.created_at AS created_at,
	r.modified_at AS modified_at
		
FROM `project_repositories` AS pr
JOIN `projects` AS p
ON pr.project_id = p.id
JOIN `repositories` AS r
ON pr.repo_id = r.id
JOIN `user_projects` AS up
ON pr.project_id = up.project_id
JOIN `users` AS u
ON up.user_id = u.id
WHERE p.id = ?
AND u.id = ?
AND r.id = ?
ORDER BY `id`
```

### Create New Repository by User Id and Project Id 
```sql
INSERT INTO `repositories`
	(`username`, `repo_name`, `repo_url`, `created_by`, `modified_by` )
VALUES
	(?,?,?,?,?);
	
	
INSERT INTO `project_repositories`
	(`project_id`, `repo_id`, `created_by`,`modified_by`)
VALUES
	(?,?,?,?);
```

### Update Repository by Repository Id
```sql
UPDATE `repositories`
SET `username` = ? , `repo_name` = ?, `repo_url` = ?
WHERE id = ?
```
