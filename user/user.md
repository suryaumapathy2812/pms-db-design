# USERS TABLE
## ADMIN
### Get all users
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
AND `active` = 1;
```
### Create New User
```sql
INSERT INTO `users` (`fist_name`,`last_name`,`email`) 
VALUES (?,?,?);
```

### Get Single User Details
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
AND `active` = 1
AND `id` = ?;
```
### Update User Details by User Id
```sql
UPDATE `users`
SET `first_name`= ? , `last_name` = ? , `email` = ?
WHERE `id`= ?
```

## USER
### Get User Details by User Id
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
### Update user details by user id
```sql
UPDATE `users`
SET `first_name`= ? , `last_name` = ? , `email` = ?
WHERE `id`= ?
```


### Deactivate User Account
```sql
UPDATE `users`
SET `status`= 'ARCHIVED' , `active` = 0
WHERE `id`= ?
```
