# OPS build E2E Test cases and descriptions

## Regression automaiton rendering test cases

**Reference repos**: https://github.com/OPS-E2E-PPE/E2E_DocsBranch

Most of these tests are checking the markdown syntax to make sure they're have the correct behavior on the page. 

**Test cases behaviors,description and check points**

(./ops-build-e2e/ops-build-e2e-testcases.md#report).

|User Behaviors/Area|Description|Check points|
|---------------------------|---------------------------|---------------------------------------|
|[Content/TOC] general: metadata related||1. Check whether all required metadata are set in <head> of built HTML. <br/>2. Check whether global metadata in docfx.json takes effect. <br/>3. Check whether certain metadata overrides global settings, such as update_date.|
|[Content/TOC] conceptual MD|There are many supported syntax in MD contents that should be built correctly.||
|[Content/TOC] YAML header|User defined YAML header should be put into <head> of built HTML.||
|[Content/TOC] special page: index.md||[TOC] Index in toc: When need normalize index, if the url equal with "index", then replace with "./". if the url ends with "index" then remove it. Example:<br/> 1. index -> ./<br/> 2. a/index -> a/ <br/>3. a-index -> a-index (no change)|
|[Content/TOC] special page: customized 404 page||1.Customized 404 page, it should be noindex/nofollow <br/>2.When visit a page not existed under this docset, it should show customized 404 page instead of default one|
|[Content/TOC] conceptual MD - INCLUDE|||
|[Content/TOC] conceptual MD - href|||
|[Content/TOC] special page: hub page|||
|[Content/TOC] special page: redirection|||
|[Content/TOC] managed reference page|||
|[Content/TOC] Rest API page|||
|[Content/TOC] TOC|||
|[Content/TOC] breadcrumb|||
