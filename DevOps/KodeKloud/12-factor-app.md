# 12 Factor App Principles

The 12 Factor App is a methodology for building software-as-a-service applications that emphasizes best practices for scalability, maintainability, and deployment. The principles are as follows:

## Codebase: One codebase tracked in version control, many deploys.

1. codebase: any single repo (in a centralized revision control system like Subversion), or any set of repos who share a root commit (in a decentralized revision control system like Git)
2. The codebase should be stored in a version control system (e.g., Git, subversion, mercurial) and should be the single source of truth for the application. Each deployment should be based on the same codebase, ensuring consistency across environments.
3. There is only one codebase per app, but it can be deployed in multiple environments (e.g., staging, production).
4. Deploy: A deploy is a running instance of the app. Each deploy is based on the same codebase, but can be configured differently (e.g., different environment variables, different database connections). 