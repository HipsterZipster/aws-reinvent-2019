# MGT304 Automate everything: Options and best practices

You can use an expanding set of services to automate many common management tasks in your AWS environment: patching, configuration updates, software stack deployments, and more. In this session, we explore how you can use AWS management tools for automation, including through the use of self-service runbooks. We discuss the many options available, including AWS CloudFormation, AWS Service Catalog, and AWS Systems Manager.

**Speakers**

- Sanjay Garje - Sr. Technical BDM - Global & Strategic Lead, Amazon Web Services
- Kenneth Walsh - Solutions Architect, Amazon Web Services
- Ketan Patel - Sr. Director - Software Engineering, GoDaddy
- Jared Beauchamp - Senior Development Manager, GoDaddy

**Session Info**

- Session Level:300 - Advanced
- Monday, Dec 2, 3:15 PM - 4:15 PM
- Venetian, Level 2, Venetian Theatre

## Balancing the needs of builders and central cloud IT

- builders: stay agile - innovate with the speed and agility of AWS
- cloud it: establish governance - Govern at scale with central controls

### aws management and governance

- enable
- provision
- operate

### What is day 1 at AWS

- a new team onboarding
- a new workload needs to be deployed in AWS
- new developer/data scientist needs a sandbox aws account

### Automate an AWS landing zone in less than 90 minutes

- aws control tower automates aws landing zone on "Day 1"

### Enable automation from day 1

- Set up an aws landing zone
- Centralize identity and access
- Establish guardrails
- automate compliant account provisioning

### AWS CloudFormation concepts

- template json or yaml
- stack
- change set

### Enable self-service with AWS Service Catalog

- Cloud admins, security, platform teams
- see picture

### Automate Governance at Scale

- hub account - only manage them from the hub
- spoke account

- Benefits of Governance at Scale
- Service catalogs

### Operate with agility and control

- monitor resources and applications - cloudwatch

## Demo overview - automate the sharing of service catalog portfolios

- hub account generates a cloud formation template and then shares it with the spoke accounts
- spoke account - automate the process to instantiate the process
- Checkout workshop for Management Tools - MGT204

---

# GoDaddy

- 78 million domains under management
- 19+ everyday entrepreneurs
- 300k DNS queries per second
- largest global paid MWP provider

## Mission - move to the cloud

- as fast as possible
- increasing app performance
- extending reliability and scalability
- cost governance : tags/template constraints
- Networking - standardized VPC configurations
- Logging and data pipelines - streamlining developer and operational experience
- Systems Manager - Parameter store - configuration-driven deployments
- Session Manager - No SSHD + node terminal access

# GoDaddy Developer Experience team

- sr engineering godaddy
- jared beauchamp
- one stop shop for godaddy developers to learn and onboard their services to AWS

### Demo: The setup

- Who: GoDaddy engineer
- What: food truck ordering app for employees
- When: now
- Step completed: budget
