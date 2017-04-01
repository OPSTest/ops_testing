# OPS build E2E Test cases and descriptions

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

|User Behaviors/Area|Description|Check points|
|---------------------------|---------------------------|---------------------------------------|
|[Build/Publish] Create a new branch. Area should cover MSDN,VS,DOCS.|Build triggered automatically, build report, output content should be converted in the testing. Users get notification email after publishing completes.|1. New created branch's content are all published (check the published content/resource/toc (simplify to c/r/t below) number.<br/>2. New published content page can be visited|
|[Build/Publish] User push some changes on existing branch.| Incremental build should be covered in this testing. Users get notification email after publishing completes.|1. New commit build successfully.<br/>2. Changes showed on the content page|
|[Build/Publish] User can trigger manual publishing via OPS portal.|With option of force publishing(without). Users get notification email after publishing completes.|1. Build results should be successful.<br/>2. If it's incremental, then no content should be published.If it's force publish, the c/r/t number should be same with its first publish|
|[Build/Publish] User can trigger manual publishing via OPS portal.|With option of force publishing(with). Users get notification email after publishing completes.|1. Build results should be successful.<br/>2. If it's incremental, then no content should be published.If it's force publish, the c/r/t number should be same with its first publish|
|[Build/Publish] User can delete a protected branch from VSO/GitHub|Once user deletes a protected branch, the corresponding branch page can still be visited. (such as master and live branch)|1. Once user deletes the protected branch, the delete action result should fail with friendly error message. <br/>2. Protected branch pages can still be visited although it's no longer existed in VSO/GitHub. <br/>3. The protected branch should be shown in branch selector dropdown box( verify on page)|
|[Build/Publish] User create pull request to merge changes to master/live branch|This should be BVT. Build triggered automatically, build report, output content, comments, notifications should be converted in the testing.|1. Set PR state in GitHub when the job is initialized. <br/>2. Set PR comment in GitHub when the job completes <br/>3. Set PR state in GitHub when the job completes <br/>4. Email notification is sent - Optional|
|[Build/Publish] User updates an existing pull request|When a PR is updated by new commits in source branch, a new PR validation build will be triggered. Should cover source branch is in same repo or is in forked repo.|same above|
|[Build/Publish] User did changes in configuration:<br/>1.Op.config.json<br/>2. Docfx.json|Configuration change will cause:<br/>1. build behavior change. <br/>2. Show/hide validation <br/>3. Show/Hide component on output page.Detail is in the docs.||
|[Build/Publish] Build report|Should check build files count, resource count, warning/error count, output url, etc.|1. Build/PR will both receive email <br/>2. PR will always see the build status on the PR page <br/>3. PR will see the comments once the PR comment is enable|
|[Build/Publish] I can build PDF when someone pushes changes into the branch or manually triggered from portal||Download the packges and check if all the pdf has generated|
|[Local build] Local build|User runs .openpublishing.build.ps1 in local cloned repository and the script generates build outputs.|1. Pages has been generated under root/_sites folder <br/>2. The build result is OK|
|[Provision] User add locale in existing repo and do provision for this locale.|New repo will be created and provisioned.|Topic reference a topic not in loc repo. Should be fallback to default locale.|
|[Provision] User de-provision the repo|||
|[Provision] User changes docset config|If user changes base path, themes, should check published url/page||
|[Cross-repository] Dependency build|If repoA has dependency on repoB, and the dependency relationship is set. Then if repoB is changed, repoA should also be built.||
|[Cross-repository] Token/code snippets locale fallback behavior||1.If token/code snippets doesn't exist in localized repository but only in fallback repository. <br/>2.The build can still pass The content should be rendered OK except the token/code snippets is same with fallback repository|
|[Cross-repository] include source files from another rep||Similar with the above one|
|[Cross-repository] Syncing between repos|||

## Regression mannual build test cases

 > [!NOTE]
 > The regression mannual build test cases need to testing after PPE and Production deploayment every sprint.

**Reference repo**: https://github.com/openpublishtest/azure-docs-pr

**Test cases behaviors,description and check points**

[!div class="mx-tdBreakAll"]
|User Behaviors/Area|Description|Check points|
|---------------------------|---------------------------|---------------------------------------|
|Azure en-us repository full build|Step1. Create a new branch from master on repository https://github.com/openpublishtest/azure-docs-pr. <br/>Step2. … (no more for this as new branch will always trigger force build and publish)|1.Build result should be same with https://github.com/Microsoft/azure-docs-pr <br/>2. Visit published page on your branch to see if Redering is OK.<br/>3. Compare build time with prod|
|zure cs-cz repository incremental build|Step1. trigger a build (full) on live branch for repository.https://github.com/openpublishtest/azure-docs-pr.cs-cz. <br/>Step2. once the build completed in Step1, trigger another build (incremental) on live branch.|1. Incremental build result should be succeed or succeed with warning.<br/>2. Visit published page on your branch to see if Redering is OK|
|.Net repository build|Step1.  trigger a build on master branch for repositoryhttps://github.com/openpublishtest/docs| 1.Build result should be succeed or succeed with warning.<br/>2. Visit published page on your branch to see if Redering is OK|
|[RCA_Documentation](https://mseng.visualstudio.com/DefaultCollection/VSChina/_git/RCA_Documentation) repository builds (full and incremental)|Step1. trigger a build (full) on master branch for repository.https://mseng.visualstudio.com/DefaultCollection/VSChina/_git/RCA_Documentation.<br/>Step2. once the full build completed in Step1, trigger another build (incremental) on master branch.|1. Both full and incremental build result should be succeed or succeed with warning.<br/>2. Visit published page on your branch to see if Redering is OK|
|[OpenPublishing.ManualTesting](https://mseng.visualstudio.com/VSChina/_git/OpenPublishing.ManualTesting) repository builds (full and incremental)|Step1.  trigger a build (full) on master branch for repositoryhttps://mseng.visualstudio.com/VSChina/_git/OpenPublishing.ManualTesting.<br/>Step2. once the full build completed in Step1, trigger another build (incremental) on master branch.|1. Both full and incremental build result should be succeed or succeed with warning.<br/>2. Visit published page on your branch to see if Redering is OK|
|Azure en-us repository performance|Step1. trigger a force build on master branch for repository https://github.com/openpublishtest/azure-docs-pr.<br/>Step2. once the full build completed in Step1, trigger another build (incremental) on master branch.<br/>Step3. once the full build completed in Step1, create a PR to master branch.|1. Monitor the build time in Step2 (incremental publish).<br/>2. Monitor the build time in Step3 (incremental PR).<br/>3. Monitor the trend of build time to see if there is performance downgrade.<br/>4. Furthermore, monitor the time of each step to see if there is performance downgrade.|
|Invalid token for same warning count|Step1.  create a token with warning for repository https://github.com/openpublishtest/azure-docs-pr.<br/>Step2. trigger a full build (force publish).<br/>Step3. trigger an incremental build.|1. The warning count should be the same.|
|Warning in PR comments|Step1. modify a token to contain an invalid link  for repository https://github.com/openpublishtest/azure-docs-pr.<br/>Step2. create a PR.|1. The report should has this warning<br/>2. The pr comments in github also has this warning.|
|Extra text will not change warning count|Step1.  trigger an incremental build for repository https://github.com/openpublishtest/azure-docs-pr.<br/>Step2.  Modify a file which contains lots of link to other mds to add some extra text.<br/>Step3. trigger an incremental build.|The warning count should be the same.|
|[LSI 941427](https://mseng.visualstudio.com/VSChina/_workitems?id=941427&fullScreen=true&_a=edit)|Step1: trigger a force publishing on repository https://github.com/openpublishtest/Azure-RMSDocs-pr LSI941427 branch.<br/>Step2: after the force publishing completes, reopen https://github.com/openpublishtest/Azure-RMSDocs-pr/pull/1<br/>Step3: wait for the PR validation build completes|1. In force publishing of LSI941427 branch, the publishing succeeds or succeeds with warnings.<br/>2. The PR validation build on PR #1 passes. There is no error like: Error occurred: System.ArgumentException: An item with the same key has already been added. at System.Collections.Generic.Dictionary`2.Insert(TKey key, TValue value, Boolean add) at Microsoft.OpenPublishing.Build.Applications.ResolveDependencyConsole.Program.ResolveDependency(Options options) at Microsoft.OpenPublishing.Build.Applications.ResolveDependencyConsole.Program.Process(Options options)|


## <a id="report"> </a>Automation cases running report
OPS E2E automation test cases report address：https://vsctestportal.azurewebsites.net/Ops

Now we have two jobs to running the cases:

* E2E test run on production: Triggered every 30 minutes
* E2E test run on PPE: Triggered every 2 hour
