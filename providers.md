# Providers

## Admin

### Get All Providers
```sql
SELECT 
	p.id AS id,
	p.name AS `name`,
	p.active AS `active`
	p.created_at AS created_at,
	p.modified_at AS modified_at
FROM `providers` AS p
```

### Get Provider
```sql
SELECT 
	p.id AS id,
	p.name AS `name`,
	p.active AS `active`
	p.created_at AS created_at,
	p.modified_at AS modified_at
FROM `providers` AS p
WHERE id = ?
```

### Create Provider
```sql
INSERT INTO `providers` (`name`)
VALUES (?)
```

### Update Provider
```sql
UPDATE `providers`
SET name = ?
WHERE id = ?
```


