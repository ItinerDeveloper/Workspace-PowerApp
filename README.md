# Custom Connector Creation Guide for PowerApps

This guide provides a step-by-step walkthrough on how to create a custom connector in PowerApps using a Swagger API documentation and how to create a connection instance of this connector.

## Prerequisites

1. Access to PowerApps.
2. A valid Swagger API documentation file (provided in this guide as `ws.swagger.json`).
3. API Key for authentication.

## Steps to Creating a Custom Connector

### Step 1: Prepare Swagger API Documentation

Ensure you have the Swagger API documentation file (`ws.swagger.json`) ready. This file will be used to create the custom connector.

### Step 2: Create a New Custom Connector

1. **Sign in to PowerApps:**
   - Navigate to [PowerApps](https://make.powerapps.com).
   - Sign in with your credentials.

2. **Navigate to Custom Connectors:**
   - On the left navigation pane, select **Custom Connectors**.

3. **Create a New Custom Connector:**
   - Click **New custom connector** and select **Import an OpenAPI file**.

4. **Import the Swagger API Documentation:**
   - Name your connector, e.g., "Itiner Workspace Integration".
   - Click on **Import** and select the `ws.swagger.json` file.

### Step 3: Configure the Custom Connector

1. **Configure General Information:**
   - Review the information imported from the Swagger file.
   - Adjust the **Host** and **Base URL** if needed (these should be populated from the Swagger file).

2. **Define the Actions:**
   - Click on the **Definition** tab.
   - Review the actions and parameters imported from the Swagger file.

3. **Test the Connector:**
   - Click on the **Test** tab.
   - Create a new connection using the API key required by your API.
   - Test the available actions to ensure they work as expected.

### Step 4: Create a Connection Instance

1. **Navigate to Connections:**
   - On the left navigation pane, select **Connections**.

2. **Add a New Connection:**
   - Click **New connection**.
   - Find your custom connector from the list and select it.

3. **Authenticate:**
   - You will need to have an integration user in Itiner WS, that has an API key generated for them
   - Enter the API key when prompted in the following format: "Bearer [Your API KEY]"
   - Click **Create** to create a new connection instance.

## Usage in PowerApps

1. **Create a New App:**
   - Navigate to **Apps** > **Create an app**.

2. **Add Data Source:**
   - In your app, click on **Data** > **Add data**.
   - Select your custom connector from the list.
   - Enter the API key when prompted in the following format: "Bearer [Your API KEY]"

3. **Use the Connector:**
   - Use the actions defined in your custom connector within your app. For example, to start a workflow, you can call the `StartWorkflow` action with the required parameters.
   - Here’s an example of how you might use the custom connector to start a workflow:

		```PowerApps
		// Assuming you have added the custom connector and named it "ItinerConnector"
		ItinerConnector.StartWorkflow({
			'X-Custom-APIKey': "YOUR_API_KEY",
			ItinerTemplateUniqueName: "T001",
			ItinerStarterUserName: "User1",
			ItinerManagerUserName: "Manager1",
			ItinerDefaultUserName: "DefaultUser",
			Variables: {
				// Add your variables here
			}
		}); ```


## Conclusion

You have successfully created a custom connector in PowerApps using Swagger API documentation and created a connection instance. You can now integrate your application with other applications through PowerApps using this connector.

For more detailed information, refer to the official [Microsoft PowerApps documentation](https://docs.microsoft.com/en-us/powerapps/maker/canvas-apps/custom-connectors/define-openapi-definition).
