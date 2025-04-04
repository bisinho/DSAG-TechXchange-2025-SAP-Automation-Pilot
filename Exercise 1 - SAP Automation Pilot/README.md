# SAP Automation Pilot: Cloud Foundry Application Recovery with Gen AI

## Overview of the use case: Cloud Foundry Application Recovery with SAP Automation Pilot and Gen AI

This hands-on workshop guides you through automating the recovery of a Cloud Foundry application using SAP Automation Pilot and Generative AI. You will generate, execute, and extend an automation command that detects application issues, performs recovery, and provides troubleshooting information.

## Prerequisites

- Access to SAP Automation Pilot
- A Cloud Foundry application
- SAP AI Core credentials and a GPT-4o deployment

**Note:** These prerequisites will be provided to you during the DSAG TechXchange 2025 event.

## Step 0: Begin!

Log in to your Automation Pilot subscription and explore the UI. Take a moment to familiarize yourself with the service and its capabilities.

## Step 1: Generate the Recovery Procedure with Gen AI

Automation Pilot provides a wide range of ready-to-use automations. However, it also allows you to create custom automations for specific scenarios using its low-code/no-code features.

Alternatively, you can use the built-in AI Assistant to generate and bootstrap automations from a simple prompt—an advanced no-code experience.

1. Go to the **Commands** page.
2. Click on the **Generate** button.
3. Provide a catalog and name for your command.
4. Use the following prompt:

```
Get the state of the Cloud Foundry application. If its state is not "STARTED", start the application. Ensure that any relevant output or status messages are displayed.
```

This will generate a command that checks the application status and starts it if necessary.

## Step 2: Test the Generated Command

The AI-generated automation might be partially complete. Always verify that it works as expected.

To test it:

1. Manually stop your Cloud Foundry application.
2. Trigger the generated command.

### Required Parameters

- `region`: BTP region of your CF app (e.g., `cf-eu10-004`)
- `subAccount`: Name of your CF organization
- `resourceGroup`: Name of your CF space
- `resourceName`: Name of your CF application
- `user`: Technical user with the Space Developer role
- `password`: Password for the technical user
- `identityProvider`: e.g., `sap.ids`

### Expected Behavior

- The automation should detect that the application is stopped.
- It should attempt to start the application.
- Output should display useful status information.

## Step 3: Extend Troubleshooting with Gen AI

Add a new step to the command to retrieve the application's audit events.

1. Under the **Configuration** section, click **Generate** to add a new step.
2. Provide a name for the step.
3. Use this prompt:

```
Get Cloud Foundry application events
```

This will fetch relevant audit events for troubleshooting.

## Step 4: Extend Troubleshooting Manually

Add another step manually to retrieve recent logs for the CF application.

1. Under the **Configuration** section, click **Add** to create a new step.
2. Provide a name for the step.
3. Select the `GetCloudAlmCfAppLogs` command from the dropdown.

## Step 5: Display Troubleshooting Information

Now that the command retrieves both audit events and logs, let's configure the output to display them.

1. Go to the **Contract** section.
2. Add two output keys: `events` and `logs`.
3. Then, go to the **Output** step under **Configuration**.
4. Use dynamic expressions to extract and display the data from the previous steps.

## Step 6: Run the Extended Command

Stop your application and run the updated command again.

### Expected Behavior

- The application is detected as stopped.
- It is restarted automatically.
- Audit events and logs are collected.
- Troubleshooting information is displayed in the output.

## Step 7: Analyze Troubleshooting Data with Gen AI

We'll now use SAP AI Core's Generative AI Hub to analyze the logs and events for insights.

### Add AI Core Credentials

1. Go to the **Input** step under **Configuration**.
2. Add a new **Additional Value**.
3. Choose the input `AICoreData` (contains the service key and GPT-4o deployment ID).

### Add the GPT-4o Analysis Step

1. Click **Add** to create a final step.
2. Provide a name for the step.
3. Select the `GenerateGpt4OmniCompletion` command.

### Configure the Step

Set the following parameters:

- **deploymentId:** From `AICoreData`
- **serviceKey:** From `AICoreData`
- **systemPrompt:**
```
You are an AI assistant with expertise in CAP NodeJS applications.
You will receive application logs from a CAP NodeJS application that uses HANA Cloud as its database.
Your task is to analyze these logs and provide a summary highlighting the application's current state and any potential issues.
```
- **prompt:** Use dynamic expressions to include logs and optionally audit events.

### Add the Output Key

Create a new output key to display the AI-generated result.

## Step 8: Execute the Final Command

Stop your Cloud Foundry application one last time and run the fully configured command.

### Observe the Output

- Application recovery status
- Audit events and logs
- AI-generated analysis and recommendations

## Conclusion

Congratulations! You've successfully built and executed an end-to-end automation for recovering a Cloud Foundry application using SAP Automation Pilot and Gen AI. Your automation now detects issues, performs recovery, and delivers actionable insights using AI-powered analysis.

You're now ready to explore even more complex automation scenarios with SAP Automation Pilot!
---
<br><br>
This concludes the Enablement Day session for SAP Automation Pilot. Make sure to check out additional resources and support options provided. Thank you for participating! Awesome work 😎
