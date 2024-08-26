<br>

<h1 align="center">Configure Microsoft Sentinel (SIEM)</h1>

<br>

<p align="center">
<img width="1000" src="https://github.com/user-attachments/assets/069c7c79-c76d-4cba-a81f-a99db273d261" alt="Banner"/>
<br />
<br />

In this Lab we're going to **Create 4 different Maps** that highlight where different people from around the World are doing Malicious things to our Environment since it's been online.

<br>

We're going to Create the following 4 Maps:

1. Failed Authentication against **Windows WMs** (RDP / SMB / General Authentication Failures)

2. Failed Authentication against **Linux VM** (SSH)

3. Failed Authentication to the **Microsoft SQL Server** (inside our Windows VM)

4. Malicious Inbound Flows for the **Network Security Groups**

<br>

<br>

<details close> 
<summary> <h2>1️⃣ Create Sentinel Workbooks</h2> </summary>
<br>

<br>
  
> We're going to **Create 4 different Workbooks in Microsoft Sentinel**.
> 
> These will show different types of **Malicious Traffic** from around the World, targeting our Resources.
> 
> We'll import some pre-built **JSON files** into Microsoft Sentinel in order to Create the Maps.

<br>

<br>

In the **Azure Portal** ➜ go to **Microsoft Sentinel** ➜ select our **Log Analytics Workspace** ```LAW-Cyber-Lab-01```

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<br>

💡The Maps are Created inside of Workbooks:

So click on the **Workbooks** blade ➜ and then ➕ **Add Workbook**

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<h2></h2>

<br>

<details close> 
  
**<summary> 📝 Step-by-step Guide on How to Create the Sentinel Maps Inside the Workbooks</summary>**

<br>

We'll first create the **Workbook** & the **Map** for the ***Linux SSH Authentication Failures***

After clicking on ➕ **Add Workbook** ➜ you can see there's a Default Workbook that Sentinel made.

Click ✏️ **Edit**

<br>

![azure portal](https://github.com/user-attachments/assets/9d44e9cd-77b8-41f4-93a7-2067a752e545)

<br>

There's 2 Elements in the default workbook ➜ so we'll 🗑️ **Remove** them both

<br>

![azure portal](https://github.com/user-attachments/assets/343aafd9-44d7-4b59-bcda-b031db117d2b)

<br>

![azure portal](https://github.com/user-attachments/assets/202e60b2-e41e-4278-a423-c2b64b411707)

<br>

Then we're going to click on ➕ **Add** ➜ and we're going to 𝄜 **Add query** based element

<br>

![azure portal](https://github.com/user-attachments/assets/4ab29302-b055-44cb-ba8e-7cb881f5b0c7)

<br>

We'll then click the **</> Advanced Editor blade**

<br>

![azure portal](https://github.com/user-attachments/assets/d413801a-f244-417b-b0e1-98123d4fc183)

<br>

Now go to [this GitHub link](https://github.com/joshmadakor1/Cyber-Course-v2/blob/main/Sentinel-Maps(JSON)/linux-ssh-auth-fail.json) to get the **JSON** for the **Linux SSH Failed Authentication Map**.

Copy the **JSON** text.

<br>

![azure portal](https://github.com/user-attachments/assets/f3af9386-d113-4c36-ac3f-02f2729f170a)

<br>

Back in the Azure Portal ➜ erase the default text ➜ and paste the **JSON** from the GitHub link

Then click ✔️ **Done Editing** down bellow

<br>

![azure portal](https://github.com/user-attachments/assets/17ab1229-7a1b-46d8-bc07-a5eb7fa9069e)

<br>

Lastly, we'll click on the 💾 **Save** button:

- **Name the Workbook** ➜ ```linux-ssh-auth-fail```

- Make sure you select our **Log Analytics Workspace** ➜ ```LAW-Cyber-Lab-01```

- Place the Workbook at he same **Location** as our other Resources ➜ ```(US) East US```

Click **"Apply"**

<br>

![azure portal](https://github.com/user-attachments/assets/da6e470e-b63b-401d-8b97-c9d2883ad25a)

<br>

✅ The **Workbook** and the corresponding **Sentinel Map** for the **Linux SSH Authentication Failures** were successfuully created.

<br>

![azure portal](https://github.com/user-attachments/assets/63f4d693-f9a9-44b1-99cd-70b408a5b8a1)

<br>

We'll then continue Creating the rest of the Workbooks & Maps for the rest of the Resources.

We'll click on ➕ **Add Workbook** ➜ follow the same process ➜  and use the other JSON codes from [this link](https://github.com/joshmadakor1/Cyber-Course-v2/tree/main/Sentinel-Maps(JSON))

<br>

  </details>

<h2></h2>

<br>

✅ All 4 Workbooks & Maps were successfully created:

<br>

![azure portal](https://github.com/user-attachments/assets/425a8c12-e647-40d9-aa56-4fa965ea75da)

<br>

<details close> 
  
**<summary> 💡 We can then Test the Query ➜ to see if Events will be plotted on the Maps.</summary>**

<br>

From inside the **Workbook** ➜ click on ✏️ **Edit** ➜ and then **↑ Edit**

<br>

![azure portal](https://github.com/user-attachments/assets/d115a623-3ec5-4584-993f-ec5ea9f48bf4)

<br>

![azure portal](https://github.com/user-attachments/assets/d5b9d372-f6b4-49f2-8674-12adb50aa0a2)

<br>

And then we can see the actual **"Log Analytics Workspace Logs Query"** that's being used to plot stuff on the Map.

💡 If we click on the **"Map Settings"** button we can see all the **Settings** used in conjuction with the **Query** to create the **Attack Map**:

<br>

![azure portal](https://github.com/user-attachments/assets/0c976a36-0991-4679-aea1-22588d9b24f6)

<br>

We'll copy this Query from under the ⚙️ **Settings"** blade:

<br>

![azure portal](https://github.com/user-attachments/assets/0c976a36-0991-4679-aea1-22588d9b24f6)

<br>

We'll then go to our Log Analytics Workspace ```LAW-Cyber-Lab-01``` ➜ and **Paste It** to **Query the Logs**

<br>

  </details>

<br>

For example ➜ this is the Query from the **Windows RDP/SMB Authentication Failures** Workbook in LAW:

<br>

![azure portal](https://github.com/user-attachments/assets/25d8d89c-1a6c-4158-8400-35c46995a395)

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

![azure portal](https://github.com/user-attachments/assets/577a0b79-d93b-466e-a365-9d1f6107a07e)

<br>

We're then going to Import all of our [Sentinel Analytics Rules](https://github.com/joshmadakor1/Cyber-Course-v2/blob/main/Sentinel-Analytics-Rules/Sentinel-Analytics-Rules(KQL%20Alert%20Queries).json).

Download the **Raw JSON File** and Save it.

<br>

![azure portal](https://github.com/user-attachments/assets/f075d305-ac55-47d5-85d0-a0e80f4b7022)

<br>

Back in **Microsoft Sentinel** ➜ click on **Import** to upload the **JSON File**.

<br>

![azure portal](https://github.com/user-attachments/assets/8085ebbc-055d-48e6-bce8-e7147d0b8ef3)

<br>

✅ We can confirm that all of our **13 Analytics Query Rules** were **Successfully Deployed**!

<br>

![azure portal](https://github.com/user-attachments/assets/26168fbd-25bd-4b1f-b5cd-23cce068badd)

<br>

  </details>

<h2></h2>

<details close> 
<summary> <h2>3️⃣ Attack Traffic Generation (Simulated Attacks)</h2> </summary>
<br>

<br>

>   <details close> 
>   
> **<summary> 📝 Explanation</summary>**
> 
> In this final stage of the lab ➜ we're going to explore some of the **Custom Analytics Rules / Alerts** that we created in **Sentinel**.
> 
> We'll look at the **Queries** that make those Events ➜ and try to go through and manually trigger at least 6 of them.
>   
> This will allow us to understand how the Analytics Rules & the KQL actually work.
> 
>   </details>

<br>

To test your alerts and incidents rule configuration ➜ simulate some attacks on the VMs and see if they show up in Sentinel (generate alerts and incidents).

⚠️ We have to make sure these work before the first observation period.

<br>

Here are some Tests to Run:

<br>

#### ❶ Trigger AAD Brute Force Success:

- Simulate brute force success against Azure AD with your attacker account (from attack-vm).

- Either use PowerShell or an incognito window to fail 10-11 consecutive logins, followed by one successful login.

<br>

<h2></h2>

<br>

#### ❷ Trigger MSSQL Brute Force Attempt:

- We'll use the ```attack-vm``` for this one.

- Use ***PowerShell*** or ***SSMS*** to simulate **Brute Force Attempt against your SQL Server** by failing 10 Consecutive Logins.

<br>

<h2></h2>

<br>

#### ❸ Trigger Malware Outbreak:

- In ```windows-vm``` generate a **Malware Alert** by using ***PowerShell*** to create 1 or more **EICAR Files**.

- 💡 You can also do this Manually by creating a Text File with an **EICAR String** in it.

<br>

<h2></h2>

<br>

#### ❹ Trigger Possible Privilege Escalation (AKV Critical Credential Retrieval or Update):

- Manually read our **Key Vault Secret** ```Tenant-Global-Admin-Password``` in the Azure portal.

<br>

<h2></h2>

<br>

#### ❺ Trigger Windows Host Firewall Tampering:

- Manually Enable & Disable the ```windows-vm``` **Firewall**.

<br>

<h2></h2>

<br>

#### ❻ Trigger Excessive Password Resets:

- Reset a **User's Password** in the Azure portal 10 times.

<br>

<h2></h2>

<br>

After each attach, wait 10-20 minutes ➜ then check Sentinel to see if you have any incidents.

<br>

>   <details close> 
>   
> **<summary> 💡 Note</summary>**
> 
> This can also help you with incident investigation later on in the lab.
> 
>   </details>

<br>

### ➡️ Incidents in Sentinel after Simulating Some Attacks:

<br>

![azure portal](https://github.com/user-attachments/assets/00cef135-106c-4f4e-a5d0-f68e2b345c14)

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
