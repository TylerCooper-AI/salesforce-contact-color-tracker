# 🚀 GitHub + Salesforce Web Interface Deployment Guide

## Why This Approach is Better for Beginners

Instead of using command line tools, we'll use:
- **GitHub** to store and track your code
- **Salesforce's web interface** to manually create the same functionality
- **Visual learning** - you'll see exactly what each component does

## Step 1: Create GitHub Repository

### Option A: Using GitHub Website (Easiest)
1. Go to [github.com](https://github.com) and sign in
2. Click the **"+"** button in the top right corner
3. Select **"New repository"**
4. Name it: `salesforce-contact-color-tracker`
5. Make it **Public** (so you can share it)
6. **Don't** check "Add a README file" (we already have one)
7. Click **"Create repository"**

### Option B: Using Terminal (if you prefer)
```bash
# Create repository on GitHub (you'll need a GitHub account)
gh repo create salesforce-contact-color-tracker --public

# Push your code to GitHub
git remote add origin https://github.com/YOUR_USERNAME/salesforce-contact-color-tracker.git
git branch -M main
git push -u origin main
```

## Step 2: Access Your Salesforce Sandbox

1. Go to your Salesforce sandbox URL (usually something like `https://yourcompany--sandbox.salesforce.com`)
2. Log in with your sandbox credentials
3. You should see the Salesforce interface

## Step 3: Create the Custom Field (Manual Method)

### What We're Building
A dropdown field on Contact records that lets users select their favorite color.

### Step-by-Step Instructions

1. **Navigate to Setup**
   - Click the gear icon (⚙️) in the top right
   - Select **"Setup"**

2. **Go to Object Manager**
   - In the left sidebar, under **"Platform Tools"**
   - Click **"Object Manager"**

3. **Find the Contact Object**
   - In the search box, type **"Contact"**
   - Click on **"Contact"**

4. **Create a New Field**
   - Click **"Fields & Relationships"** tab
   - Click **"New"** button

5. **Configure the Field**
   - **Data Type**: Select **"Picklist"**
   - Click **"Next"**

6. **Field Details**
   - **Field Label**: `Favorite Color`
   - **Field Name**: `Favorite_Color__c` (this will auto-populate)
   - **Help Text**: `Select the contact's favorite color`
   - Click **"Next"**

7. **Picklist Values**
   - Click **"New"** to add each color:
     - **Value**: `Red` → **Label**: `Red`
     - **Value**: `Blue` → **Label**: `Blue`
     - **Value**: `Green` → **Label**: `Green`
     - **Value**: `Yellow` → **Label**: `Yellow`
     - **Value**: `Purple` → **Label**: `Purple`
   - Click **"Next"**

8. **Field-Level Security**
   - Check **"Visible"** for all profiles
   - Click **"Next"**

9. **Page Layouts**
   - Check **"Contact Layout"** to add to the main contact page
   - Click **"Next"**

10. **Review and Save**
    - Review your settings
    - Click **"Save"**

## Step 4: Create the Validation Rule

### What We're Building
A rule that prevents users from saving a contact without selecting a favorite color.

### Step-by-Step Instructions

1. **Go to Validation Rules**
   - Still in the Contact object
   - Click **"Validation Rules"** tab
   - Click **"New"**

2. **Configure the Rule**
   - **Rule Name**: `Require_Favorite_Color`
   - **Description**: `Requires that a favorite color is selected when creating a new contact`
   - **Error Condition Formula**: `ISBLANK(Favorite_Color__c)`
   - **Error Message**: `Please select a favorite color for this contact.`
   - **Error Location**: `Favorite Color`

3. **Save the Rule**
   - Click **"Save"**

## Step 5: Create the Flow (Automation)

### What We're Building
An automation that creates personalized greetings based on the selected color.

### Step-by-Step Instructions

1. **Navigate to Flows**
   - In Setup, search for **"Flows"**
   - Click **"Flows"** under Process Automation

2. **Create New Flow**
   - Click **"New Flow"**
   - Select **"Record-Triggered Flow"**
   - Click **"Next"**

3. **Configure Trigger**
   - **Object**: `Contact`
   - **Trigger**: `A record is created or updated`
   - **Conditions**: `Favorite_Color__c` is not null
   - Click **"Next"**

4. **Add Decision Element**
   - From the toolbox, drag **"Decision"** to the canvas
   - Name it: `Check Color`
   - **Outcome Label**: `Red`
   - **Outcome API Name**: `Red`
   - **Condition**: `{!$Record.Favorite_Color__c} Equals Red`

5. **Add More Outcomes**
   - Click **"Add Outcome"** for each color:
     - Blue: `{!$Record.Favorite_Color__c} Equals Blue`
     - Green: `{!$Record.Favorite_Color__c} Equals Green`
     - Default: Check **"Default Outcome"**

6. **Add Assignment Elements**
   - For each outcome, add an **"Assignment"** element
   - **Variable**: `{!$Record.Description}`
   - **Value**: The appropriate greeting message

7. **Greeting Messages**
   - **Red**: `Hello! I see your favorite color is Red - that's a bold and energetic choice! 🔴`
   - **Blue**: `Hello! I see your favorite color is Blue - that's a calm and trustworthy choice! 🔵`
   - **Green**: `Hello! I see your favorite color is Green - that's a natural and balanced choice! 🟢`
   - **Default**: `Hello! Thanks for sharing your favorite color with us! 🎨`

8. **Save and Activate**
   - Click **"Save"**
   - Name it: `Color Greeting Flow`
   - Click **"Activate"**

## Step 6: Test Your Creation

1. **Go to Contacts**
   - Click **"Contacts"** in the app launcher
   - Click **"New"**

2. **Fill Out the Form**
   - **First Name**: `Test`
   - **Last Name**: `Contact`
   - **Favorite Color**: Select any color
   - Click **"Save"**

3. **Check the Results**
   - Look at the **Description** field
   - You should see your personalized greeting!

## What You've Learned

✅ **Custom Fields**: How to add new data fields to Salesforce objects
✅ **Validation Rules**: How to ensure data quality
✅ **Flows**: How to create simple automation
✅ **GitHub**: How to store and track your code
✅ **Salesforce Web Interface**: How to build without coding

## Next Steps

1. **Experiment**: Try different colors and see different greetings
2. **Modify**: Change the greeting messages
3. **Extend**: Add more colors to the picklist
4. **Share**: Show your GitHub repository to others

## Troubleshooting

- **Field not showing**: Check that it's added to the page layout
- **Validation not working**: Make sure the rule is active
- **Flow not running**: Check that it's activated and the trigger conditions are correct

This approach teaches you the same concepts but through the visual interface, making it easier to understand what each component does!
