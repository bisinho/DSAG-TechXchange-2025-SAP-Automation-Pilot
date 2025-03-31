# Exercise 3 - Extend Your CI/CD Pipeline With Additional Stages

In this exercise, you will extend your job in SAP Continuous Integration and Delivery with the **Additional Unit Tests** and **Release** stages.

## Exercise 3.0 - (Optional) Enable Additional Unit Tests

1. In the **Jobs** tab in SAP Continuous Integration and Delivery, choose the job you created in [Exercise 1](../ex1#exercise-13-create-and-trigger-a-job-in-sap-continuous-integration-and-delivery).
2. Click on **Edit**.
3. In the **Stages** tab of your job details, switch on **Additional Unit Tests** using the toggle.
4. In the **npm Script** text box, enter `test:odata`.

    ![03_01_0000](../ex3/images/03_01_0000.png)

When you run this build now, the **Additional Unit Tests** would fail because the npm script `test:odata` does not exist yet. To fix this issue, provide a script in package.json in your project and commit the changes to GitHub. Proceed as follows:

1. In your GitHub repository, go to the `package.json` file.
2. Choose the pencil icon to edit the file.

    ![git_edit](../ex3/images/git_edit.png)

3. Add a new line below line 16:
    `"test:odata": "npm install --save-dev @sap/cds-dk && npx cds-typer '*' && jest",`

    ![git_commit](../ex3/images/git_commit.png)

4. Replace `Update package.json` in the text box with a meaningful commit message, for example, `Add test script for odata`.
5. Click **Commit changes** to save the changes.

## Exercise 3.1 - Enable the Release Stage

To enable the **Release** stage in your SAP Continuous Integration and Delivery job, you need the name of the node for the upload to SAP Cloud Transport Management as well as a service key to authenticate your pipeline against it. We will provide these values to you.

1. In the **Release** stage in your job details, switch on **Cloud Transport Management** using the toggle.
2. Leave the drop down to `Export from` and enter the name of the node for the upload to SAP Cloud Transport Management, which in this case is `DEV`.
3. For **Service Key**, click on the value help button. As a result, the **Select Credentials** window pops up. Then click the plus button which opens the **Create Credential** popup.
4. In another browser window, open the SAP BTP cockpit and navigate to the subaccount in which you’ve created an instance for SAP Cloud Transport Management.
5. Navigate to **Services** → **Instances and Subscriptions**.
6. Click on the Overflow Button (**...**) of your SAP Cloud Transport Management instance.
7. Click on **Create Service Key**

    ![create_servicekey](../ex3/images/create_servicekey.png)

8. Give your key a name and click on **Create**.
9. Next to the name of your service key, click on the Overflow Button (**...**) and then on **View**.
10. Click on **Copy JSON** to copy the entire service key.
11. Back in SAP Continuous Integration and Delivery, paste the copied service key into the **Service Key** text box of the **Create Credentials** pop-up window.
12. Enter a name for the service key, for example `tms-service-key`, then choose **Create**.

    ![03_02_0000](../ex3/images/03_02_0000.png)

## Exercise 3.2 - Run the Pipeline Manually

1. In the **Jobs** tab in SAP Continuous Integration and Delivery, choose your job and trigger it by choosing **Run** in the top-right corner.
2. After a few seconds, a new tile appears in the **Builds** view of your job. You should see that the build has failed in the **Additional Unit Tests** stage. Choose the respective build tile to view its detailed log.

## Exercise 3.4 - Verify the Success of Your Pipeline

1. Return to your job in SAP Continuous Integration and Delivery.
2. If you created a webhook in [Exercise 1](../ex1#exercise-12-optional-create-a-webhook), a build of your connected job is triggered automatically after committing the code changes in GitHub. If you didn't create a webhook, choose **Run** to start your job.

As a result, a build is triggered and a new build tile appears in the **Builds** section of your job. Your job should now be successful, and not only run unit tests, but also perform an upload to SAP Cloud Transport Management.

## Summary

Congratulations! You've extended your CI/CD job with the **Additional Unit Tests** and **Release** stages.

Continue to [Exercise 4 - Perform imports with SAP Cloud Transport Management](../ex4/README.md).
