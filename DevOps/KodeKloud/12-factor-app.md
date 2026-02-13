# 12 Factor App Principles

The 12 Factor App is a methodology for building software-as-a-service applications that emphasizes best practices for scalability, maintainability, and deployment. The principles are as follows:

## 1. Codebase: One codebase tracked in version control, many deploys.

1. codebase: any single repo (in a centralized revision control system like Subversion), or any set of repos who share a root commit (in a decentralized revision control system like Git)
2. The codebase should be stored in a version control system (e.g., Git, subversion, mercurial) and should be the single source of truth for the application. Each deployment should be based on the same codebase, ensuring consistency across environments.
3. There is only one codebase per app, but it can be deployed in multiple environments (e.g., staging, production).
4. Deploy: A deploy is a running instance of the app. Each deploy is based on the same codebase, but can be configured differently (e.g., different environment variables, different database connections). 

## 2. Dependencies: Explicitly declare and isolate dependencies.

1. The application should explicitly declare all dependencies (e.g., libraries, frameworks) in a manifest file (e.g., requirements.txt for Python, package.json for Node.js, composer.json for PHP). This ensures that the application can be easily set up and run in any environment.
2. The application should use a dependency isolation tool (e.g., virtualenv for Python, npm for Node.js, composer for PHP) to ensure that dependencies are isolated from the system and other applications. This prevents conflicts between different applications and allows for easier management of dependencies.
3. In php, dependency declaration and isolation is typically achieved using Composer, which manages dependencies and their versions in a composer.json file. In Python, this is often done using pip and virtualenv, where dependencies are listed in a requirements.txt file. In Node.js, npm is used to manage dependencies, with the package.json file serving as the manifest for the application’s dependencies.
4. One benefit of explicit dependency declaration is that it simplifies setup for developers new to the app. The new developer can check out the app’s codebase onto their development machine, requiring only the language runtime and dependency manager installed as prerequisites. They will be able to set up everything needed to run the app’s code with a deterministic build command. This is in contrast to an app that relies on implicit dependencies, which may require a developer to manually install and configure various libraries and tools, leading to potential issues with version conflicts and missing dependencies. By explicitly declaring dependencies, the app becomes more portable and easier to maintain across different environments.
5. Twelve-factor apps also do not rely on the implicit existence of any system tools. For example, `curl` is a common command-line tool for making HTTP requests, but it may not be available in all environments. If the app needs to shell out to a system tool, that tool should be vendored into the app.

## 3. Config: Store config in the environment.

1. **Strict Code/Config Separation:** "Config" is anything that changes between environments (DB passwords, API keys, hostnames). If you can't open-source your code right now without leaking a secret, your config is wrongly mixed with your code.
2. **Use Environment Variables:** Avoid hardcoded constants or uncommitted config files (like `.yaml` or `.ini`). Use **Environment Variables** (env vars) because they are universal, language-agnostic, and won't accidentally get checked into Git.
3. **Avoid "Environment" Grouping:** Don't group settings into "Dev" or "Prod" buckets inside the code. Treat every config variable as an independent, granular switch. This prevents a "combinatorial explosion" of config files as you add more testing or staging tiers.

## 4. Backing Services: Treat backing services as attached resources.

1. **Everything is a Resource:** Treat any service the app talks to over a network (databases, message queues, APIs) as an "attached resource." The app shouldn't care if the service is running on the same server or a third-party cloud.
2. **Loose Coupling via Config:** Never hardcode connection details. Use URLs and credentials stored in your **Configuration** so you can swap a local database for a cloud-managed one (like Amazon RDS) just by changing a config string.
3. **Plug-and-Play Flexibility:** Resources should be easy to attach or detach. If a database fails, you should be able to point the app to a new one (a "new attachment") without redeploying or rewriting a single line of code.

## 5. Build, Release, Run: Strictly separate build and run stages.

1. **The Three-Step Transformation:** Code becomes a **Build** (compiled code + dependencies), which is combined with **Config** to create a **Release**, which is finally executed in the **Run** stage. Each step must be distinct and sequential.
2. **Immutable Releases:** Every release must have a unique ID (like `v102` or a timestamp) and can **never** be changed once created. If you need to fix a bug, you create a *new* build and a *new* release; you never "patch" code directly on the server.
3. **Fail Fast in Build, Stay Simple in Run:** Keep the "Run" stage as simple as possible so it doesn't break during a midnight reboot. Move complex tasks (like compiling or fetching packages) to the "Build" stage where developers can see and fix errors immediately.

![alt text](<Screenshot from 2026-02-13 01-08-53.png>)

## 6. Processes: Execute the app as one or more stateless processes.

1. **Zero Memory Persistence:** Never assume the app will "remember" anything from a previous request. Since processes can restart or move to new servers at any time, local memory and disk are strictly temporary.
2. **No Sticky Sessions:** Avoid "sticky sessions" (tying a user to one specific server). Store session data in a shared "backing service" like Redis or a database so any running process can pick up where the last one left off.
3. **Build-Time Preparation:** Don't generate or cache permanent files (like compressed CSS/JS) while the app is running. Handle those tasks during the **Build Stage** so the running process stays lean and stateless.

## 7. Port Binding: Export services via port binding.

1. **Self-Contained Services:** Your app shouldn't need an external web server "injector" to run. It should be totally self-contained, using a library (like Express for Node, Flask for Python, , or **FrankenPHP/PHP-FPM** for PHP) to listen on a specific port (e.g., `:8080`) all by itself.
2. **Unified Interface:** By binding to a port, your app presents a simple "contract" to the world. Whether it's a web service, a database, or a chat server, the way to talk to it is always the same: a Hostname and a Port.
3. **Apps as Backing Services:** Because your app exports itself via a port, it can easily become a "Backing Service" for another app. One app just needs the URL and Port of the other to start communicating, making microservices possible.

## 8. Concurrency: Scale out via the process model.

1. **Divide and Conquer:** Break the app into different **process types** (e.g., `web` for HTTP, `worker` for background tasks). This allows you to scale specific parts of the app independently based on demand.
2. **Scale Horizontally:** Instead of making one process bigger (vertical scaling), add more identical processes across multiple machines (horizontal scaling). This works because processes are "share-nothing" and partitioned.
3. Your application shouldn't try to manage its own health or "background" itself (daemonizing). Instead, you rely on a Process Manager (like Docker, Kubernetes, or systemd). If a process crashes, the manager restarts it; if you need to scale, the manager spins up new ones. Your app's only job is to run in the foreground and do its work. **The Golden Rule for DevOps:**
Run your app in the foreground. Let the system (Kubernetes/Docker) put it in the background for you.

## 9. Disposability: Maximize robustness with fast startup and graceful shutdown.

1. **Fast Startup:** Processes should be ready to work in seconds. Quick boot times make "Elastic Scaling" (adding more servers during a traffic spike) actually work and help the system recover instantly if a process crashes.
2. **Graceful Shutdown (SIGTERM):** When told to stop, a web process should finish the current request before exiting, and a worker process should put its current task back on the queue. This ensures no data is lost and no users get a "404 Error" mid-request.
3. **Crash-Only Design:** Build the app to handle "sudden death" (like a power failure). By using idempotent operations (tasks that can be safely repeated), your app can recover from a hard crash just as easily as a clean shutdown.