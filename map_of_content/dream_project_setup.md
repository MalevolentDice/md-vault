# Requirements for my perfect project
## Development Environment
- Single Deployment (SaaS/Game) or everyone who wants to update has to take the latest valid deployment
- IDE agnostic 
	- CLI tools
	- Every tool can be used in the pipeline
- Develop directly on master
- Formatting/Linting in pipeline. Everyone can use their own local formatting
- libraries/dependencies/container etc. will be updated to the newest version immediately 
	- automatic version increment. When this breaks the pipeline (see feedback) it's highest priority

### Feedback during development
Have a dashboard showing the validity of all pipeline stages after committing in master. Validity of pipeline is always highest priority.

Maybe make sure the entire code pipeline up to e2e tests in stage is executable locally on the developers Laptop (docker - but how to use GitLab CI/CD or GitHub Actions if we want developers to be able to run the pipeline locally?).

## Code path to production
local unit tests -> commit to master -> run integration tests -> create build -> deploy build to stage -> e2e tests in stage -> create deployment -> deploy to prod

### Stage
Stage should always be created from nothing. Don't persist the database. Define types of database migration and create a separate job either in e2e tests or during deployment creation. Will also depend on integration of zero downtime deployment.

## Tests
### Unit Tests
Unit Tests often turn into maintained legacy without benefit to the project. I want every developer to write the tests they require for development and be free to choose if they want them deleted or committed. Everyone is free to change/delete unit tests.
* They are a tool to support your development.
	* Run locally, no requirement
	* No execution in pipeline

### Integration Tests

### e2e tests
