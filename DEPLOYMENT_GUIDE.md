# Salesforce Contact Color Tracker - Deployment Guide

## What We Built
This project adds a simple color tracking system to your Salesforce Contacts:
- **Custom Field**: "Favorite Color" dropdown on Contact records
- **Validation Rule**: Ensures a color is selected when creating contacts
- **Flow**: Automatically creates personalized greetings based on color choice

## Prerequisites
1. **Salesforce CLI** installed on your computer
2. **VS Code** with Salesforce extensions (or any code editor)
3. **Access to your Salesforce sandbox**

## Step 1: Install Salesforce CLI
1. Go to https://developer.salesforce.com/tools/sfdxcli
2. Download and install the CLI for your operating system
3. Open Terminal/Command Prompt and verify installation:
   ```bash
   sf --version
   ```

## Step 2: Authenticate with Your Sandbox
1. Open Terminal/Command Prompt
2. Navigate to the project folder:
   ```bash
   cd /Users/tyler.cooper/salesforce-contact-color-tracker
   ```
3. Authenticate with your sandbox:
   ```bash
   sf org login web --alias MySandbox --instance-url https://test.salesforce.com
   ```
4. Follow the browser prompts to log in

## Step 3: Deploy the Changes
1. Deploy all components to your sandbox:
   ```bash
   sf project deploy start --target-org MySandbox
   ```

## Step 4: Test Your Changes
1. Go to your Salesforce sandbox
2. Navigate to Contacts
3. Create a new Contact
4. You should see:
   - A "Favorite Color" dropdown field
   - An error if you try to save without selecting a color
   - A personalized greeting in the Description field based on your color choice

## Troubleshooting
- If deployment fails, check the error messages in Terminal
- Make sure you're authenticated to the correct org
- Verify you have the necessary permissions in your sandbox

## What Each File Does
- `Favorite_Color__c.field-meta.xml`: Creates the color dropdown field
- `Require_Favorite_Color.validationRule-meta.xml`: Ensures color is selected
- `Color_Greeting_Flow.flow-meta.xml`: Creates personalized greetings
- `sfdx-project.json`: Tells Salesforce CLI about your project
