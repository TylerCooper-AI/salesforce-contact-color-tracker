# 🎨 Salesforce Contact Color Tracker

A beginner-friendly Salesforce project that teaches the basics of custom fields, validation rules, and automation flows.

## What This Project Teaches You

### 1. **Custom Fields** 📝
- **What it is**: A new data field you add to existing Salesforce objects
- **What we built**: A "Favorite Color" dropdown on Contact records
- **Why it matters**: Allows you to store custom data specific to your business needs
- **File**: `Favorite_Color__c.field-meta.xml`

### 2. **Validation Rules** ✅
- **What it is**: Rules that prevent users from saving records with invalid data
- **What we built**: Ensures every contact must have a favorite color selected
- **Why it matters**: Keeps your data clean and consistent
- **File**: `Require_Favorite_Color.validationRule-meta.xml`

### 3. **Flows (Automation)** 🤖
- **What it is**: Visual automation that runs when certain conditions are met
- **What we built**: Automatically creates personalized greetings based on color choice
- **Why it matters**: Saves time and ensures consistent processes
- **File**: `Color_Greeting_Flow.flow-meta.xml`

## How It Works

1. **User creates a new Contact**
2. **System requires them to select a favorite color** (validation rule)
3. **When they save, the Flow automatically runs**
4. **Flow checks the color and creates a personalized greeting**
5. **Greeting appears in the Contact's Description field**

## Example Greetings
- **Red**: "Hello! I see your favorite color is Red - that's a bold and energetic choice! 🔴"
- **Blue**: "Hello! I see your favorite color is Blue - that's a calm and trustworthy choice! 🔵"
- **Green**: "Hello! I see your favorite color is Green - that's a natural and balanced choice! 🟢"

## Key Learning Concepts

### Metadata-Driven Development
- Everything in Salesforce is defined by XML metadata files
- These files describe what you want to build
- Salesforce CLI reads these files and creates the actual functionality

### Object-Oriented Thinking
- Contacts are "objects" (like a digital form)
- Fields are "properties" of that object
- Rules and flows are "behaviors" of that object

### Declarative vs. Programmatic
- **Declarative**: You describe what you want (using clicks, not code)
- **Programmatic**: You write code to build what you want
- This project uses declarative development (easier for beginners!)

## Next Steps
Once you've deployed this project:
1. Try creating different contacts with different colors
2. See how the validation rule prevents saving without a color
3. Watch the flow automatically create greetings
4. Experiment with adding new colors to the picklist
5. Try modifying the greeting messages

## File Structure
```
salesforce-contact-color-tracker/
├── force-app/main/default/
│   ├── objects/Contact/fields/
│   │   └── Favorite_Color__c.field-meta.xml
│   ├── validationRules/
│   │   └── Contact.Require_Favorite_Color.validationRule-meta.xml
│   └── flows/
│       └── Color_Greeting_Flow.flow-meta.xml
├── sfdx-project.json
├── DEPLOYMENT_GUIDE.md
└── README.md
```

This project demonstrates the fundamental building blocks of Salesforce customization - perfect for understanding how the platform works!
