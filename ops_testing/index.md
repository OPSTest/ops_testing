# OPS build E2E Test cases and **Description**s

## Regression automaiton build test cases

**Reference repos**

|GitHub repository|Description|
|-----------------|-----------------|
|[DOCSRepo](https://github.com/OPS-E2E-PPE/E2E_DocsBranch)|The Docs theme test repo for PPE environment|
|[MSDNRepo](https://github.com/OPS-E2E-PPE/E2E_MSDNBranch)|The MSDN theme test repo for PPE environment|
|[TECHNETRepo](https://github.com/OPS-E2E-PPE/E2E_TechnetBranch)|The TechNet theme test repo for PPE environment|
|[VSCOMRepo](https://github.com/OPS-E2E-PPE/E2E_VSCOMBranch)|The VSCom theme test repo for PPE environment|

**Test cases behaviors,description and check points**

Following are the regression automation test cases. You can see the report [here](#report).

1. [Build/Publish] Create a new branch. Area should cover MSDN,VS,DOCS
    
    - **Description**: This should be BVT. Build triggered automatically, build report, output content should be converted in the testing. Users get notification email after publishing completes.
    - **Check Points**:
        * New created branch's content are all published (check the published content/resource/toc (simplify to c/r/t below) number. 
        * New published content page can be visited

2. [Build/Publish] User push some changes on existing branch

    - **Description**:  Incremental build should be covered in this testing. Users get notification email after publishing completes.
    - **Check Points**: 
        * New commit build successfully. 
        * Changes showed on the content page

3. [Build/Publish] User can trigger manual publishing via OPS portal

    - **Description**: With option of force publishing(without). Users get notification email after publishing completes.
    - **Check Points**:
        * Build results should be successful.
        * If it's incremental, then no content should be published.If it's force publish, the c/r/t number should be same with its first publish.

4. [Build/Publish] User can trigger manual publishing via OPS portal

    - **Description**: With option of force publishing(with). Users get notification email after publishing completes.
    - **Check Points**:
        * Build results should be successful.
        * If it's incremental, then no content should be published.If it's force publish, the c/r/t number should be same with its first publish.

5. [Build/Publish] User can delete a protected branch from VSO/GitHub

    - **Description**: Once user deletes a protected branch, the corresponding branch page can still be visited. (such as master and live branch).
    - **Check Points**:
        * Once user deletes the protected branch, the delete action result should fail with friendly error message.
        * Protected branch pages can still be visited although it's no longer existed in VSO/GitHub.
        * The protected branch should be shown in branch selector dropdown box( verify on page)

6. [Build/Publish] User create pull request to merge changes to master/live branch

    - **Description**: This should be BVT. Build triggered automatically, build report, output content, comments, notifications should be converted in the testing.
    - **Check Points**: 
        * PR state in GitHub when the job is initialized.
        * Set PR comment in GitHub when the job completes.
        * Set PR state in GitHub when the job completes.
        * Email notification is sent - Optional.

7. [Build/Publish] User updates an existing pull request

    - **Description**: When a PR is updated by new commits in source branch, a new PR validation build will be triggered. Should cover source branch is in same repo or is in forked repo.
    - **Check Points**: 
        * PR state in GitHub when the job is initialized.
        * Set PR comment in GitHub when the job completes.
        * Set PR state in GitHub when the job completes.
        * Email notification is sent - Optional.

8. [Build/Publish] User did changes in configuration：1.Op.config.json 2. Docfx.json

    -  **Description**: Configuration change will cause.
        * build behavior change.
        * Show/hide validation.
        * Show/Hide component on output page.Detail is in the docs.  
    - **Check Points**:
        * Too complex and need to sync offline.(will update later).

9. [Build/Publish] Build report

    - **Description**: Should check build files count, resource count, warning/error count, output url, etc.
    - **Check Points**:
        * Build/PR will both receive email.
        * PR will always see the build status on the PR page.
        * PR will see the comments once the PR comment is enable.

10. [Build/Publish] I can build PDF when someone pushes changes into the branch or manually triggered from portal

    - **Description**: You can control which branches to publish or generate PDFs from. By default, build is done in all the branches. This property setting is only read from the configuration file in the live branch.
    - **Check Points**: 
        * Download the packges and check if all the pdf has generated.

11. [Local build] Local build

    - **Description**: User runs .openpublishing.build.ps1 in local cloned repository and the script generates build outputs.
    - **Check Points**:
        * Pages has been generated under root/_sites folder
        * The build result is OK

12. [Provision] User add locale in existing repo and do provision for this locale.

    - **Description**: New repo will be created and provisioned.
    - **Check Points**: Topic reference a topic not in loc repo. Should be fallback to default locale.

12. [Provision] User de-provision the repo

    - **Description**:
    - **Check Points**:

13. [Provision] User changes docset config

    - **Description**: If user changes base path, themes, should check published url/page.
    - **Check Points**:


14. |[Cross-repository] Dependency build

    - **Description**: If repoA has dependency on repoB, and the dependency relationship is set. Then if repoB is changed, repoA should also be built.
    - **Check Points**: 

15. [Cross-repository] Token/code snippets locale fallback behavior

    - **Description**: 
    - **Check Points**:
        * If token/code snippets doesn't exist in localized repository but only in fallback repository.
        * The build can still pass The content should be rendered OK except the token/code snippets is same with fallback repository.

16. [Cross-repository] include source files from another repo

    - Similar with the above one

17. [Cross-repository] Syncing between repos 


## Regression mannual build test cases

 > [!NOTE]
 > The regression mannual build test cases need to testing after PPE and Production deploayment every sprint.

**Reference repo**: https://github.com/openpublishtest/azure-docs-pr

**Test cases behaviors,description and check points****

1. Azure en-us repository full build

    - **Description**:
        * Create a new branch from master on repository https://github.com/openpublishtest/azure-docs-pr
        * (no more for this as new branch will always trigger force build and publish).
    - **Check Points**:
        * Build result should be same with https://github.com/Microsoft/azure-docs-pr.
        * Visit published page on your branch to see if Redering is OK.
        * ompare build time with prod.

2. Azure cs-cz repository incremental build

    - **Description**:
        * trigger a build (full) on live branch for repository https://github.com/openpublishtest/azure-docs-pr.cs-cz
        * once the build completed in Step1, trigger another build (incremental) on live branch.
    - **Check Points**:
        * Incremental build result should be succeed or succeed with warning.
        * Visit published page on your branch to see if Redering is OK.

3. .Net repository build

    - **Description**: trigger a build on master branch for repository
      https://github.com/openpublishtest/docs
    - **Check Points**:
        * Build result should be succeed or succeed with warning.
        * Visit published page on your branch to see if Redering is OK
    
4. [RCA_Documentation](https://mseng.visualstudio.com/DefaultCollection/VSChina/_git/RCA_Documentation) repository builds (full and incremental)

    - **Description**: 
        * trigger a build (full) on master branch for repository
          https://mseng.visualstudio.com/DefaultCollection/VSChina/_git/RCA_Documentation
        * once the full build completed in Step1, trigger another build (incremental) on master branch.
    - **Check Points**:
        * Both full and incremental build result should be succeed or succeed with warning.
        * Visit published page on your branch to see if Redering is OK.

5. [OpenPublishing.ManualTesting](https://mseng.visualstudio.com/VSChina/_git/OpenPublishing.ManualTesting) repository builds (full and incremental)

    - **Description**:
        * trigger a build (full) on master branch for repository
          https://mseng.visualstudio.com/VSChina/_git/OpenPublishing.ManualTesting
        * once the full build completed in Step1, trigger another build (incremental)     on master branch.
    - **Check Points**:
        * Both full and incremental build result should be succeed or succeed with warning.
        * Visit published page on your branch to see if Redering is OK.

6. Azure en-us repository performance
    - **Description**:
        * trigger a force build on master branch for repository     https://github.com/openpublishtest/azure-docs-pr
        * once the full build completed in Step1, trigger another build (incremental) on master branch
        * once the full build completed in Step1, create a PR to master branch.
    - **Check Points**:
        * Monitor the build time in Step2 (incremental publish) .
        * Monitor the build time in Step3 (incremental PR).
        * Monitor the trend of build time to see if there is performance downgrade.
        * Furthermore, monitor the time of each step to see if there is performance downgrade.

7.  Invalid token for same warning count
    - **Description**:
        * create a token with warning for repository https://github.com/openpublishtest/azure-docs-pr
        * trigger a full build (force publish).
        * trigger an incremental build.
    - **Check Points**: The warning count should be the same.

8. Warning in PR comments.
    - **Description**:
        * modify a token to contain an invalid link  for repository https://github.com/openpublishtest/azure-docs-pr.
        * create a PR
    - **Check Points**:
        * The report should has this warning.
        * The pr comments in github also has this warning.

9. Extra text will not change warning count
    - **Description**: 
        * trigger an incremental build for repository https://github.com/openpublishtest/azure-docs-pr
        * Modify a file which contains lots of link to other mds to add some extra text.
        * trigger an incremental build.
    - **Check Points**:
        * The warning count should be the same.

10. [LSI 941427](https://mseng.visualstudio.com/VSChina/_workitems?id=941427&fullScreen=true&_a=edit)
    - **Description**:
        * trigger a force publishing on repository https://github.com/openpublishtest/Azure-RMSDocs-pr LSI941427 branch.
        * after the force publishing completes, reopen https://github.com/openpublishtest/Azure-RMSDocs-pr/pull/1
        * wait for the PR validation build completes
    - **Check Points**:
        * In force publishing of LSI941427 branch, the publishing succeeds or succeeds with warnings.
        * The PR validation build on PR #1 passes. There is no error like: Error occurred: System.ArgumentException: An item with the same key has already been added. at System.Collections.Generic.Dictionary 2.Insert(TKey key, TValue value,Boolean add) at Microsoft.OpenPublishing.Build.Applications.ResolveDependencyConsole.Program.ResolveDependency(Options options) at Microsoft.OpenPublishing.Build.Applications.ResolveDependencyConsole.Program.Process(Options options)。

## <a id="report"> </a>Automation cases running report
OPS E2E automation test cases report address：https://vsctestportal.azurewebsites.net/Ops

Now we have two jobs to running the cases:

* E2E test run on production: Triggered every 30 minutes
* E2E test run on PPE: Triggered every 2 hour
