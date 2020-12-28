# Senario1_maersk

1) The build should trigger as soon as anyone in the dev team checks in code to master branch 
Answer : 
This can be done by enabling the Continuous Integration Trigger.
We can also check the branch for which we want to create the continuous integration trigger. Here it is the "master" branch.
As soon as the dev person commits any changes in the code in the "master" branch, the build gets triggered automatically.

2) There will be test projects which will create and maintained in the solution along the Web and API. The trigger should build all the 3 projects - Web, API and test.The build should not be successful if any test fails.
Answer :

This can be done by integrating the sonarqube tasks in the build pipeline.
Whenever we integrate the testcases in the code, sonarqube uses these testcases to give the code coverage as output.
Sonar has 4 different tasks - Prepare analysis using SonarQube, Run CodeAnalysis, Publish QualityGate Result and Break build on Quality Gate Failure.
The 4th Sonar task is responsible for braking the build if there are any test case failures present.

3)The deployment of code and artifacts should be automated to Dev environment. 

The code can be automatically deployed by enabling the continuous deployment trigger.

We can also select any specific version or the lastest artifact version whcih we want to deploy.
We should enable the After Release option, present in the trigger of the Dev Stage environment so that the artifacts are automatically deployed when the build runs fine and artifacts are generated.

4)Upon successful deployment to the Dev environment, deployment should be easily promoted to QA and Prod through automated process.
Answer: 
For the automatic flow of code from one environment to other environment, we can add trigger to the stages.
Using the After Stage Trigger and in that we need to give the name of the stage (here DEV) after which we want to trigger the QA stage.
And similarly can be done to the QA and PROD stage, in the Prod Satge we can add trigger "After Stage" and can add QA.
 
5) The deployments to QA and Prod should be enabled with Approvals from approvers only.
Answer: 
For deployments to be enabled by using Approver's Approval, we need to add Approver's name to the Post deployment conditions by enabling it in the DEV stage.
Similarly, we need to do the same with QA stage. In the post deployment conditions of the QA stage, we need to add the Approvers name for the PROD stage deployment.



