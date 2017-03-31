# OPS build E2E Test cases and descriptions

## Automaiton build test cases

**Reference repos**

|GitHub repository|Description|
|-----------------|---------------|
|[openpublishing-test](https://github.com/Microsoft/openpublishing-test)||
|[DocsRepo](https://github.com/OPS-E2E-PPE/E2E_DocsBranch)|The Docs theme test repo for PPE environment|
|[MSDNRepo](https://github.com/OPS-E2E-PPE/E2E_MSDNBranch)|The MSDN theme test repo for PPE environment|
|[TechNetRepo](https://github.com/OPS-E2E-PPE/E2E_TechnetBranch)|The TechNet theme test repo for PPE environment|
|[VSCOMRepo](https://github.com/OPS-E2E-PPE/E2E_VSCOMBranch)|The VSCom theme test repo for PPE environment|



**E2E test cases behaviors,description and check points**

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

