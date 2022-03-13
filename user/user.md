# USERS TABLE
## ADMIN
### get all users
```sql
SELECT  
	`id`,
	`first_name`,
	`last_name`,
	`email`,
	`status`,
	`active`
	`created_at`,
	`modified_at`
FROM `users`
WHERE `status` != 'ARCHIVED'
```
### create new user
```sql
```
### get single user details
```sql
```
### update user details by user id
```sql
```

## USER
### get user details by user id
```sql
SELECT 
	`id`,
	`first_name`,
	`last_name`,
	`email`,
	`status`,
	`active`
	`created_at`,
	`modified_at`
FROM `users`
WHERE `status`!= 'ARCHIVED'
AND `id` = 1;

```
### update user details by user id
```sql
```
