# Training Workshop Kit

> [Docker ](Dockerfile) : Open platform for developers and sysadmins to build, ship, and run distributed applications as containers, whether on laptops, data center VMs, or the cloud.

> [CircleCI ](https://circleci.foc.zone/gh/Servicing/dolphin-api) : Continuous Integration (CI) and Continuous Deployments (CD) tool

> [AWS Elastic Container Service (ECS) ](https://aws.amazon.com/ecs/) : Orchestration of Docker containers on EC2 instances. This runs the code, auto-scales containers and the EC2's they run on up and down, as well as handling the infrastructure side of deploying new code.

> [HAL9000 ](https://hal9000/applications/933/status) : QL in-house application that handles deployments and releases to various environments (including AWS). It also handles a lot of the encrypted configuration values which are passed to the code as Environment Variables.

> [Terraform ](https://www.terraform.io/) : Terraform is Infrastructure-As-Code (IAC) that can build out highly QL-specific infrastructure components in a repeatable way. Instead of a lot of click-and-configure, we can run terraform scripts to create approved infrastructure stacks on-demand in minutes.

# Prerequisites

**These are the prereqs which are needed prior to coming to a workshop. The following should be completed and ready to go:**

- Docker installed locally ( **Install through Software Center (PC) or Self Service (Mac)** - If you install from Docker web site, you will be missing key network policies needed )
    * If using a Windows PC, make sure right-click the Docker icon in your system tray and make sure it's set to use LINUX containers. In other words, it should set "Switch to Windows containers", which means it's currently on Linux containers.
- VSCode or similar file editor ( https://code.visualstudio.com/download )
- AWSCLI installed ( https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html )
- Request AWS account access to Training Lab Account (418023852230). Navigate to myaccess/ in your browser, click "Add/Remove Access", and search for `AWS-SSO-TrainingIAC-NonProd-ServerEngineer`. Click the checkbox and request it for your dash account. Then click "Review and Submit", then "Submit".
- Terraform ( https://www.terraform.io/ )
    * If using a Windows PC, wherever you download Terraform to, make sure to add that path to your PATH variable. See here for how: https://docs.alfresco.com/4.2/tasks/fot-addpath.html
- Create demo repository under your personal GIT account ( 999999-YOUR_NAME-iac )
- If you've never used HAL before, go to hal9000/ in your browser and login with your dash account. This will create your account in HAL.
- Clone example GIT project locally ( see below )

## Setting up GIT

1. Clone this repo locally to your laptop ( https://git.rockfin.com/training-iac/training-starter-kit.git )

2. Rename the folder to this naming standard: **999999-YOURNAME-iac**, where YOURNAME is your AD network login (first initial, last name). Then, delete the **.git** folder at the root; this allows you to associate this folder with a different git repo. This will become the base for the Git repo for your application's infrastructure.

3. Make a repo with the same name as what you called the folder in step 2 under your personal Git organization. https://git.rockfin.com/YOUR-NAME/999999-YOURNAME-iac. For example, https://git.rockfin.com/jsmith/999999-jsmith-iac

4. Follow the instructions given to you post-creation in your browser to upload your modified clone of the starter-kit to your applications new IAC repo. The one difference is instead of "git add README.md", type "git add -A" instead to add everything.

You are all set if you have a custom-named version of the starter kit uploaded and ready to go in your personal (QL-owned) GIT org.
# 999999-SWang2-iac
