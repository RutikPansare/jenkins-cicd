Jenkins CI/CD Pipeline


Environment:
Ubuntu 26.04.1
Docker 29.9.3
Jenkins 2.541.3
Git plugin 5.11.0
Pipeline plugin 608.v67378e9d3db_1

Pipeline stages:
Checkout code from GitHub.
Validate index.html.
Create webapp.tar.gz.
Copy package to the deployment folder.

Configuration:
Branch: main
Trigger: SCM polling
Concurrent builds: Disabled
GitHub credentials stored in Jenkins.

Testing:
Successful pipeline execution.
Tested incorrect repository URL.
Tested incorrect HTML file path.
Restored configuration and verified successful execution.

