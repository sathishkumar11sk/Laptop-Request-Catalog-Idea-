💻 Laptop Request Project – ServiceNow 📘 Overview

The Laptop Request Project is developed in ServiceNow to automate and simplify the process of requesting laptops within an organization. It demonstrates the use of Service Catalog, Variables, UI Policies, UI Actions, and Update Sets to create an interactive and dynamic service request form.

🎯 Objectives

Automate the laptop request process using the Service Catalog.

Create a dynamic catalog item that displays fields based on user input.

Use Catalog UI Policies and UI Actions for better interactivity.

Package and migrate configurations between ServiceNow instances using Update Sets.

⚙️ Implementation Steps 🧩 Step 1: Create an Update Set

Open ServiceNow.

Navigate to All → System Update Sets → Local Update Sets.

Click New and fill in the details:

Name: Laptop Request

Click Submit and then Make Current to activate the update set.

🧰 Step 2: Create a Catalog Item

Go to All → Service Catalog → Maintain Items.

Click New and enter the following:

Name: Laptop Request

Catalog: Service Catalog

Category: Hardware

Short Description: Use this item to request a new laptop

Click Save.

📋 Step 3: Add Variables

Scroll down to the Variables related list and click New. Create the following variables:

Variable Type Name Order Laptop Model Single Line Text laptop_model 100 Justification Multi Line Text justification 200 Additional Accessories Checkbox additional_accessories 300 Accessories Details Multi Line Text accessories_details 400

After adding all variables, save the catalog item form.

🧠 Step 4: Create a Catalog UI Policy

Go to Service Catalog → Maintain Items.

Search and open Laptop Request.

Scroll down to Catalog UI Policies → New.

Enter the details:

Short Description: Show accessories details

When to Apply:

Field: additional_accessories

Operator: is

Value: true

Click Save (do not submit yet).

⚙️ Step 5: Create a Catalog UI Policy Action

Scroll to Catalog UI Policy Actions → New.

Fill in the details:

Variable Name: accessories_details

Order: 100

Mandatory: True

Visible: True

Click Save, and then save the Catalog UI Policy form again.

🧾 Step 6: Create a UI Action (Reset Form)

Go to All → System Definition → UI Actions → New.

Fill the following details:

Table: shopping_cart (sc_cart)

Order: 100

Action Name: Reset form

Client: ✅ Checked

Add the following script:

function resetForm() {

g_form.clearForm(); // Clears all fields in the form

alert("The form has been reset.");
}

Click Save.

📦 Step 7: Complete and Export Update Set

Go to All → System Update Sets → Local Update Sets.

Open the created update set (Laptop Request).

Set State to Complete.

In the related list Updates tab, verify all recorded changes.

Click Export to XML to download the update set file.

🔁 Step 8: Import and Commit Update Set in Another Instance

Open another ServiceNow instance in Incognito Mode.

Go to All → System Update Sets → Retrieved Update Sets.

Click Import Update Set from XML.

Upload the downloaded XML file.

Open the imported update set (Laptop Request Project).

Click Preview Update Set → Commit Update Set.

Check the related tab Updates to verify all imported configurations.

✅ Step 9: Verify the Catalog Item

Go to All → Service Catalog → Catalogs → Hardware Category.

Search for Laptop Request and open it.

Verify the functionality:

Only three variables appear initially.

When Additional Accessories is checked, the Accessories Details field becomes visible and mandatory.

📂 Project Deliverables

Catalog Item and Variables

Catalog UI Policy and UI Policy Actions

Custom UI Action (Reset Form)

Update Set XML File

Project Documentation (README file)

🏁 Conclusion

The Laptop Request Catalog Item Project effectively automates the laptop request process using ServiceNow’s Service Catalog. It demonstrates how UI Policies, Variables, and Update Sets can be used to design interactive and efficient workflows. By migrating the update set between instances, this project showcases ServiceNow’s flexibility in maintaining consistency across environments, ultimately improving efficiency and user satisfaction.
