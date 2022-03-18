# Providers

## ADMIN

### Get All Token

```sql
SELECT 
	pt.id AS id,
	u.id AS user_id,
	pt.provider_id AS provider_id,
	p.name AS provider_name,
	
	pt.token AS token,
	pt.client_id AS client_id,
	pt.client_secret AS client_secret,
	
	pt.created_at AS created_at,
	pt.modified_at AS modified_at

FROM `provider_tokens` AS pt
JOIN `providers` AS p
ON pt.provider_id = p.id
JOIN `users` AS u
ON pt.user_id = u.id
```

### Get Token by Provider Id
```sql
SELECT 
	pt.id AS id,
	u.id AS user_id,
	pt.provider_id AS provider_id,
	p.name AS provider_name,
	
	pt.token AS token,
	pt.client_id AS client_id,
	pt.client_secret AS client_secret,
	
	pt.created_at AS created_at,
	pt.modified_at AS modified_at

FROM `provider_tokens` AS pt
JOIN `providers` AS p
ON pt.provider_id = p.id
JOIN `users` AS u
ON pt.user_id = u.id
where p.id = ?
```

### Get Token by Token Id
```sql
SELECT 
	pt.id AS id,
	u.id AS user_id,
	pt.provider_id AS provider_id,
	p.name AS provider_name,
	
	pt.token AS token,
	pt.client_id AS client_id,
	pt.client_secret AS client_secret,
	
	pt.created_at AS created_at,
	pt.modified_at AS modified_at

FROM `provider_tokens` AS pt
JOIN `providers` AS p
ON pt.provider_id = p.id
JOIN `users` AS u
ON pt.user_id = u.id
where pt.id = ?
```



## User

### Get All User Tokens by User Id
```sql
SELECT 
	pt.id AS id,
	u.id AS user_id,
	pt.provider_id AS provider_id,
	p.name AS provider_name,
	
	pt.token AS token,
	pt.client_id AS client_id,
	pt.client_secret AS client_secret,
	
	pt.created_at AS created_at,
	pt.modified_at AS modified_at

FROM `provider_tokens` AS pt
JOIN `providers` AS p
ON pt.provider_id = p.id
JOIN `users` AS u
ON pt.user_id = u.id
WHERE u.id = ?
```

### Get Token by Provider Id

```sql
SELECT 
	pt.id AS id,
	u.id AS user_id,
	pt.provider_id AS provider_id,
	p.name AS provider_name,
	
	pt.token AS token,
	pt.client_id AS client_id,
	pt.client_secret AS client_secret,
	
	pt.created_at AS created_at,
	pt.modified_at AS modified_at

FROM `provider_tokens` AS pt
JOIN `providers` AS p
ON pt.provider_id = p.id
JOIN `users` AS u
ON pt.user_id = u.id
WHERE u.id = ?
AND p.id = ?
```

### Create New Token by User Id and Provider Id
```sql
INSERT INTO `provider_tokens`
	(`provider_id`, `user_id`,`token`, `client_id`, `client_secret`)
VALUES
	(?,?,?,?)
```


### Update Token by User Id and Token Id
```sql
UPDATE `provider_tokens`
SET token = ?, client_id =?, client_secret =?
WHERE id = ? AND user_id = ?
```



