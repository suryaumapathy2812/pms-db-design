## ProjectController

```
GET:		        api/v1/projects
POST:		        api/v1/projects/create
GET: 		        api/v1/projects/:project_id
PUT/PATCH:      api/v1/projects/:project_id
DELETE: 	      api/v1/projects/:project_id
```

## RepositoryController

```
GET: 		        api/v1/projects/:project_id/repositories
POST:		        api/v1/projects/:project_id/repositories/create
GET:		        api/v1/projects/:project_id/repositories/:repo_id
PUT/PATCH:      api/v1/projects/:project_id/repositories/:repo_id
DELETE:		      api/v1/projects/:project_id/repositories/:repo_id
```


## UserController

```
GET:		        api/v1/users
POST:		        api/v1/users/create
GET:		        api/v1/users/:user_id
PUT/PATCH:    	api/v1/users/:user_id
DELETE:		      api/v1/users/:user_id
```

## TokenController

```
GET:		        api/v1/users/:user_id/tokens
POST:		        api/v1/users/:user_id/tokens/create
GET:		        api/v1/users/:user_id/tokens/:token_id
PUT/PATCH:    	api/v1/users/:user_id/tokens/:token_id
DELETE:		      api/v1/users/:user_id/tokens/:token_id
```
