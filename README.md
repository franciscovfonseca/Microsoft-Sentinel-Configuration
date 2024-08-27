<br>

<h1 align="center">Configure Microsoft Sentinel (SIEM)</h1>

<br>

<p align="center">
<img width="1000" src="https://github.com/user-attachments/assets/d8f10eb7-e95b-447e-a679-f1d2c3e63863" alt="Banner"/>
<br />
<br />

In this Lab we're going to **Create 4 different Maps** that highlight where different people from around the World are doing Malicious things to our Environment since it's been online.

<br>

🌍 We're going to Create the following 4 Maps:

| **Map**                   | **Use Case**                                |
| ------------------------------ | ------------------------------------------ |
| 1️              | Failed Authentication against **Windows VMs** (RDP / SMB / General Authentication Failures) |
| 2️                | Failed Authentication against **Linux VMs** (SSH)                |
| 3️     | Failed Authentication to the **Microsoft SQL Server** (inside our Windows VM)                    |
| 4️  | Malicious Inbound Flows for the **Network Security Groups**                    |

<br>

<br>

<details close> 
<summary> <h2>1️⃣ Create Sentinel Workbooks</h2> </summary>
<br>

<br>
  
> We're going to set up **4 different Workbooks in Microsoft Sentinel**.
> 
> These will show different types of **Malicious Traffic** from around the World, targeting our Resources.
> 
> We'll import some pre-built **JSON files** into Microsoft Sentinel in order to Create the Maps.

<br>

<br>

In the **Azure Portal** ➜ go to **Microsoft Sentinel** ➜ select our **Log Analytics Workspace** ```LAW-Cyber-Lab-01```

<br>

![azure portal](https://github.com/user-attachments/assets/7049e934-297e-4fd1-aaad-5deef6344015)

<br>

💡The Maps are Created inside of Workbooks:

So click on the **Workbooks** blade ➜ and then ➕ **Add Workbook**

<br>

![azure portal](https://github.com/user-attachments/assets/c806a604-7bf6-4f32-b5dc-1da9416cd576)

<h2></h2>

<br>

<details close> 
  
**<summary> 📝 Step-by-step Guide on How to Create the Sentinel Maps Inside the Workbooks</summary>**

<br>

We'll first create the **Workbook** & the **Map** for the ***Linux SSH Authentication Failures***

After clicking on ➕ **Add Workbook** ➜ you can see there's a Default Workbook that Sentinel made.

Click ✏️ **Edit**

<br>

![azure portal](https://github.com/user-attachments/assets/04809ee5-30cf-4be9-9657-96b40d8570c5)

<br>

There's 2 Elements in the default workbook ➜ so we'll 🗑️ **Remove** them both

<br>

![azure portal](https://github.com/user-attachments/assets/bd89e261-7b56-40a3-b5f4-67527548db14)

<br>

![azure portal](https://github.com/user-attachments/assets/0713cab8-6708-4559-a1b7-95f32931aa2c)

<br>

Then we're going to click on ➕ **Add** ➜ and we're going to 𝄜 **Add query** based element

<br>

![azure portal](https://github.com/user-attachments/assets/00d4e479-6c2b-4a15-9f74-318c9859f61d)

<br>

We'll then click the **</> Advanced Editor blade**

<br>

![azure portal](https://github.com/user-attachments/assets/63fdc5d4-3d7c-446a-b534-83432bebd22d)

<br>

Now go to [this GitHub link](https://github.com/joshmadakor1/Cyber-Course-v2/blob/main/Sentinel-Maps(JSON)/linux-ssh-auth-fail.json) to get the **JSON** for the **Linux SSH Failed Authentication Map**.

Copy the **JSON** text.

<br>

![azure portal](https://github.com/user-attachments/assets/e0fd9e66-7334-4611-a0c6-5bdba55f5b11)

<br>

Back in the Azure Portal ➜ erase the default text ➜ and paste the **JSON** from the GitHub link

Then click ✔️ **Done Editing** down bellow

<br>

![azure portal](https://github.com/user-attachments/assets/9aaa0e83-9d8a-490a-aa5a-410737e21ecb)

<br>

Lastly, we'll click on the 💾 **Save** button:

- **Name the Workbook** ➜ ```linux-ssh-auth-fail```

- Make sure you select our **Log Analytics Workspace** ➜ ```LAW-Cyber-Lab-01```

- Place the Workbook at he same **Location** as our other Resources ➜ ```(US) East US```

Click **"Apply"**

<br>

![azure portal](https://github.com/user-attachments/assets/200974a3-3b28-41d9-82ff-a819e9a5c657)

<br>

✅ The **Workbook** and the corresponding **Sentinel Map** for the **Linux SSH Authentication Failures** were successfuully created.

<br>

![azure portal](https://github.com/user-attachments/assets/ddd23b87-fec7-464c-8e3c-72e6b77bcb01)

<br>

We'll then continue Creating the rest of the Workbooks & Maps for the rest of the Resources.

We'll click on ➕ **Add Workbook** ➜ follow the same process ➜  and use the other JSON codes from [this link](https://github.com/joshmadakor1/Cyber-Course-v2/tree/main/Sentinel-Maps(JSON))

<br>

  </details>

<h2></h2>

<br>

✅ All 4 Workbooks & Maps were successfully created:

<br>

![azure portal](https://github.com/user-attachments/assets/ddc1fe5d-41d6-40da-bd05-4a4944713158)

<br>

<details close> 
  
**<summary> 💡 We can then Test the Query ➜ to see if Events will be plotted on the Maps.</summary>**

<br>

From inside the **Workbook** ➜ click on ✏️ **Edit** ➜ and then **↑ Edit**

<br>

![azure portal](https://github.com/user-attachments/assets/10465b3c-25fb-460a-b6c3-29498b002aed)

<br>

![azure portal](https://github.com/user-attachments/assets/5262c279-be91-4257-a9fd-ad75076439f5)

<br>

And then we can see the actual **"Log Analytics Workspace Logs Query"** that's being used to plot stuff on the Map.

💡 If we click on the **"Map Settings"** button we can see all the **Settings** used in conjuction with the **Query** to create the **Attack Map**:

<br>

![azure portal](https://github.com/user-attachments/assets/9eadd94c-5998-48e0-8579-9e58355ef924)

<br>

We'll copy this Query from under the ⚙️ **Settings"** blade:

<br>

![azure portal](https://github.com/user-attachments/assets/9baa1292-e81b-4f7c-b3a4-a2923e843608)

<br>

We'll then go to our Log Analytics Workspace ```LAW-Cyber-Lab-01``` ➜ and **Paste It** to **Query the Logs**

<br>

  </details>

<br>

For example ➜ this is the Query from the **Windows RDP/SMB Authentication Failures** Workbook in LAW:

<br>

![azure portal](https://github.com/user-attachments/assets/ed015807-3c97-4def-8d0d-a58b227104b6)

<br>

By doing this, you can test changes to the Query.

✅ This way we make sure it's **Working and Generating Desired Results** ➜ before having to Update the Sentinel Workbooks.

<br>

  </details>

<h2></h2>

<details close> 
<summary> <h2>2️⃣ Alert Creation</h2> </summary>
<br>

> We're now going to **Create our Microsoft Sentinel Analytics Query Rules**.
> 
> These are going to be used to **Create Alerts** ➜ and then ultimately used to **Spin up Incidents** for certain Events taking place in our Environment.

<br>

Back in the **Azure Portal** ➜ go to **Microsoft Sentinel** ➜ and click on the **Analytics** blade

<br>

![azure portal](https://github.com/user-attachments/assets/13b81385-ded0-4e2c-810e-4e2505bdf7c5)

<br>

We're then going to Import all of our [Sentinel Analytics Rules](https://github.com/joshmadakor1/Cyber-Course-v2/blob/main/Sentinel-Analytics-Rules/Sentinel-Analytics-Rules(KQL%20Alert%20Queries).json).

Download the **Raw JSON File** and Save it.

<br>

![azure portal](https://github.com/user-attachments/assets/92f28c08-18f1-4323-bab9-ac3961a8162c)

<br>

Back in **Microsoft Sentinel** ➜ click on **Import** to upload the **JSON File**.

<br>

![azure portal](https://github.com/user-attachments/assets/445adcb4-2ec1-465b-8ff0-c018bed65d88)

<br>

✅ We can confirm that all of our **13 Analytics Query Rules** were **Successfully Deployed**!

<br>

![azure portal](https://github.com/user-attachments/assets/7ac23696-17d7-4ea9-9be4-28f628173da0)

<br>

  </details>

<h2></h2>

<details close> 
<summary> <h2>3️⃣ Understanding and Triggering Sentinel Alerts</h2> </summary>
<br>

<br>

>   <details close> 
>   
> **<summary> 📝 Explanation</summary>**
> 
> In this final stage of the lab ➜ we're going to explore some of the **Custom Analytics Rules / Alerts** that we created in **Sentinel**.
> 
> We'll look at the **Queries** that make those Events ➜ and try to go through and **Manually Trigger** at least 6 of them.
>   
> This will allow us to understand how the **Analytics Rules & the KQL Queries actually work.
> 
>   </details>

<br>

To Test your **Alerts & Incident Rule Configuration**:

- We'll **Simulate some Attacks on the VMs** and see if they show up in Sentinel (Generate Alerts & Incidents).

<br>

<br>

### ➡️ Here are some Tests to Run:

<br>

#### ❶ Trigger AAD Brute Force Success:

- Simulate **Brute-Force Success against Azure AD** with your Attacker Account ➜ from within the ```attack-vm```.

- In an Incognito Window ➜ Open the **Azure Portal** ➜ and Fail 10 Consecutive Logins ➜ followed by 1 Successful Login.


<br>

<h2></h2>

<br>

#### ❷ Trigger MS SQL Brute Force Attempt:

- We'll use the ```attack-vm``` for this one.

- Open **SSMS** and Simulate **Brute Force Attempt against the SQL Server** by failing 10 Consecutive Logins.

<br>

<h2></h2>

<br>

#### ❸ Trigger Malware Outbreak:

- From within the ```windows-vm``` ➜ Generate a **Malware Alert** by using ***PowerShell*** to create 1 or more **EICAR Files**.

- [Malware-Generator-EICAR.ps1](https://github.com/joshmadakor1/Cyber-Course/blob/main/Attack-Scripts/Malware-Generator-EICAR.ps1)

<br>

>   <details close> 
>   
> **<summary> 💡</summary>**
> 
> This can also be done Manually by creating a Text File with an **EICAR String** in it.
> 
>   </details>

<br>

<h2></h2>

<br>

#### ❹ Trigger Possible Privilege Escalation (AKV Critical Credential Retrieval or Update):

- Manually Read our **Key Vault Secret** ```Tenant-Global-Admin-Password``` in the Azure Portal.

- Observe the **Incidents** in Microsoft Sentinel.

<br>

<h2></h2>

<br>

#### ❺ Trigger Windows Host Firewall Tampering:

- Manually Enable & Disable the ```windows-vm``` **Firewall**.

- Observe the **Incidents** in Microsoft Sentinel.

<br>

<h2></h2>

<br>

#### ❻ Trigger Excessive Password Resets:

- Reset a **User's Password** in the Azure Portal 10 times.

- Observe the **Incidents** in Microsoft Sentinel.

<br>

<h2></h2>

<br>

After each Attack ➜ wait 10-20 minutes ➜ then check **Sentinel** to see if you have any **Incidents**.

<br>

>   <details close> 
>   
> **<summary> 💡 Note</summary>**
> 
> This can also help you with incident investigation later on in the lab.
> 
>   </details>

<br>

### ➡️ Incidents in Sentinel AFTER Simulating Some Attacks:

<br>

![azure portal](https://github.com/user-attachments/assets/bc25121d-158f-4702-bd45-f96bc5095f36)

<br>

  </details>

<h2></h2>

<br>

<br>

<br>

<br>

<br>

<br>

<br>
  
<br>
