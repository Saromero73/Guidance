# EffectiveTFVC branching strategies for DevOps
_____________________________________
Definitions : 
*DevOps: People, process and products to enable continuous delivery of value.*

*Nirvana Scenario: Ideal / perferct situation.*
If you would like to see GIT guide [click here](http://goo.gl/nQMUfK) 

*Assumptions : users are familiar with team foundation centralize version control. *

Team Foundation Server Centralized version control (TFVC) gives teams’ options to maintain code and make application teams effective,  by providing collaboration and sharing code in a consistent manner.
Team members should be able to publish, review and build changes using TFSVC, adoption of a good branch strategy that fosters *DevOps culture* will help your team have the best experience promoting collaboration flow, increase productivity, and spending more time developing code and less time managing code.

## Keep it simple.
When adopting DevOps keep your branch strategy simple by building your strategy from the following concepts:
________________________________________
1.	Always begin with a simple approach later you can add more.
1.  Use **Version /feature** branches for bug fixes (RC support branch) or new features.
1.	Merge **Version /feature** branches into the main branch often, have gated check ins and code reviews.
1.	Keep high quality, build every check in, merge defect fixes to main branch often.
1.  Define deployment pipelines that includes automation testing.

*Remember*  Automating bad practices, only speed up failures, it does not promote continuos delivery of value.

## Prerequisites 
Before adapting a branch strategy, define a source control structure that identifies shipable units / Release Unit. 
Plan your source control structure by keeping in mind the shippable units.

## How to decide in the right branch strategy.
The type of branch strategy depends on the types of applications you have to support:

- Single version Applications (web sites/ corporate line of business applications)
- Multiple version support applications (Word, Excel, comercial applications)

### Single version Applications
These are applications that at any given time you will only have to support 1 production version. this does not mean you may not have parallel development for subsequent features/ releases.

- Step 1 begin simple 
![initial branch diagram](images/Branchinitial.png)

Branch | Build  | pipelines | Notes
-------|--------|-----------|---------------------------------------------------------
Main   | CI_Bld | Dev       | in the nirvana case this will happen for eery check in.

The model is created to integrate with existing tools, like Jenkings.
estabilization happens in SupportV1.00 once the estabilization is completed then you can merge to main again.

*Adopting right practices in version control makes a big difference between a nightmare or a smooth sailing.*

- Step 2 add branches for Release Candidate (RC) support.
When a release cycle is completed, branch it to create the release candidate, and continue next version development in main. Defects corrections for V1.0 are implemented in the corresponding branch and merge to main as soon as it is tested and confirmed as new release candidate (RC) to keep main with minimal technical debt.
![Verion 1.0 is released](images/Branchv1.0.png)

Branch | Build  | pipelines | Notes
----------|--------|-----------|---------------------------------------------------------
Main   | CI_Bld | Dev       | in Nirvana scenario this will happen for eery check in.
SupportV1.00| RCV1_Bld | Dev->QA->STG->UAT->Prod |

### Multiple Version Applications / Feaure isolation.
This section refers to development teams that have to support multiple released versions in production. I.E.
MS Word, Excell, etc.
This strategy also work for line of business (corporate) applications with full year releases scheduled, these systems require work in future releases before the current release is in full RC mode.
 
Begin with step 1 and 2, when additional development needs arise add additional branches. 
Remember always build every check in and if possible run automated tests to mantain high quality.

Step 3 if applicable 
When a new development cycle or a new feature development begins and you have a RC version still in testing open a new branch for that released.

#### Caution 
Branches are cheap to create, however in centralize version control each additional branch creates work to keep them in sync with the main development.

## Nirvana Goals
1. Build every check in.
1. Define deployment pipelines for each branch.
1. Strive to use feature flags for new development and keep it as close to the main as possible.

## best practices when naming branches
Use a consistent naming convention for your feature branches to identify the work done in the branch. You can also include other information in the branch name, such as who created the branch.
Some suggestions for naming your feature branches:
username/description
username/workitem
bugfix/description
features/feature-name
hotfix/description
Use feature flags to manage long-running branches

## Sumarizing.
- Organize you code in shippable units.
- Always begin simple. 
- Add complexity as your needs arise.
- Use consistent naming strategy for your branches.
- Build every check in.
- Define deployment pipelines for each branch and include automated testing. 

________________________________________
