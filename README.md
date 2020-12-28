# Senario1_maersk

We can many features in to our build and release pipelines based on the requirment by using Azure DevOps Portal. I tried to answer few of the requirements as per my knowledge. Do let me know if there are any better approaches to finish the given tasks.

1) The build should trigger as soon as anyone in the dev team checks in code to master branch.

Answer :

This can be done by enabling the Continuous Integration Trigger present in the trigger section of the Build Pipeline.
We can also check the branch for which we want to create the continuous integration trigger. Here it is the "master" branch.

![image](https://user-images.githubusercontent.com/74064643/103216413-00e9d580-48e4-11eb-8229-1309088e78f0.png)

As soon as the dev person commits any changes in the code in the "master" branch, the build gets triggered automatically by genearting the artifacts.


2) There will be test projects which will create and maintained in the solution along the Web and API. The trigger should build all the 3 projects - Web, API and test.The build should not be successful if any test fails.

Answer :

This can be done by integrating the sonarqube tasks in the build pipeline.
Whenever we integrate the testcases in the code, sonarqube uses these testcases to give the code coverage as output.
Sonar has 4 different tasks - Prepare analysis using SonarQube, Run CodeAnalysis, Publish QualityGate Result and Break build on Quality Gate Failure.

![image](https://user-images.githubusercontent.com/74064643/103216281-ae101e00-48e3-11eb-9a5f-4343e5777eb5.png)

The 4th Sonar task is responsible for braking the build if there are any test case failures present.


3) The deployment of code and artifacts should be automated to Dev environment. 

Answer:

The code can be automatically deployed by enabling the continuous deployment trigger.

![image](https://user-images.githubusercontent.com/74064643/103215977-e2cfa580-48e2-11eb-8370-956a051119cf.png)

We can also select any specific version or the lastest artifact version whcih we want to deploy.

![image](https://user-images.githubusercontent.com/74064643/103216177-6db0a000-48e3-11eb-915e-359164677875.png)

We should enable the After Release option, present in the trigger of the Dev Stage environment so that the artifacts are automatically deployed when the build runs fine and artifacts are generated.

![image](https://user-images.githubusercontent.com/74064643/103216086-26c2aa80-48e3-11eb-84d0-02be07e8cb07.png)


4) Upon successful deployment to the Dev environment, deployment should be easily promoted to QA and Prod through automated process.

Answer: 

For the automatic flow of code from one environment to other environment, we can add trigger to the stages.
In the trigger section present in the pre-deployment conditions of QA Stage select the "After Stage Trigger" and in that we need to give the name of the stage (here DEV) after which we want to trigger the QA stage.

![image](https://user-images.githubusercontent.com/74064643/103215788-5fae4f80-48e2-11eb-9959-57775d797b7b.png)

And similarly can be done to the QA and PROD stage, in the Prod Stage we can add trigger "After Stage" and can add stage QA. So the deployment to the PROD stage will be done once the successful deployment is done to the QA stage.


5) The deployments to QA and Prod should be enabled with Approvals from approvers only.

Answer: 

For deployments to be enabled by using Approver's Approval in QA stage, we need to add Approver's name to the Post deployment conditions by enabling it in the DEV stage.

![image](https://user-images.githubusercontent.com/74064643/103215521-946dd700-48e1-11eb-9bfc-fc7814a09ce9.png)

Similarly, we need to do the same with QA stage. In the post deployment conditions of the QA stage, we need to add the Approvers name for the PROD stage deployment.
So that PROD deployment will be enabled once the assigned approver has approved the request for the deployment.

![image](https://user-images.githubusercontent.com/74064643/103215734-3b527300-48e2-11eb-841a-19ec9127e486.png)


Whenever we make any changes to our pipeline, we should always save the changes to reflect the saved changes.

![image](https://user-images.githubusercontent.com/74064643/103217440-96866480-48e6-11eb-85f2-54107a71eb95.png)


