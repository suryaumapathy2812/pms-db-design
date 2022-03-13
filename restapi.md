## ProjectController ( /api/v1/projects)


#####  Get Project Details ( GET )

```java
@GetMapping("/{projectId}")
	public Project show(@PathVariable("projectId") Integer projectId) { }
```

##### Get Project Modules
```java
@GetMapping("/{projectId}/modules")
	public List<ProjectModule> modules(@PathVariable("projectId") Integer projectId) { }
```

##### Enroll User into project
```java
@PostMapping("/{projectId}/users/{userId}")
	public void enrollProject(@PathVariable("projectId") String projectId, @PathVariable("userId") String userId) { }
```

## ProjectRepositories ( /api/v1/projectrepositories )

##### Get Repos
```java
@GetMapping
	public Object getRepos(@RequestParam(name = "category", required = false) String category,
			@RequestParam(name = "created_by", required = false) String createdBy,
			@RequestParam(name = "projectId", required = false) Integer projectId) {
      }
```

##### Search

```java
@GetMapping("search")
	public ProjectRepository getRepo(@RequestParam(name = "id", required = false) Integer id,
			@RequestParam(name = "account", required = false) String account,
			@RequestParam(name = "repoName", required = false) String repoName) {
      }
```

##### Update Status

```java
@PatchMapping("{id}")
	public void updateStatus(@PathVariable("id") Integer id, @RequestParam("status") Boolean status) {
  }
```

##### Add Repo
```java
@PostMapping
	public void addRepo(@RequestBody ProjectRepository projectRepository) {
  }
```

##### Add User
```java
@PutMapping("{id}/users")
public void addUser(@PathVariable("id") Integer id,
  @RequestParam(name = "username", required = true) String username) {
  }
```


			
  
  
