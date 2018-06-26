# .Description

Generate an interactive HTML report on your Office 365 environement. This report also allows you to interact with the data set within the report and configure how you want it ordered. 

[HTML Report Example](http://thelazyadministrator.com/wp-content/uploads/2018/06/22-6-2018-O365TenantReport.html)

![Dashboard](http://thelazyadministrator.com/wp-content/uploads/2018/06/dash.png)

# .Report Overview

## Dashboard

The Dashboard contains some basic information about the Office 365 tenant including the following:

- Company information
- Global Administrators
- Strong Password Enforcement
- Recent E-Mails
- Domains


One of the greatest benefits of this report is that we can interact with the data whenever we would like. If you notice the reports “Recent E-Mails” contains a search bar. If we had more recent E-mails we can either go to the next page of results by click “Next” or we can search for a keyword which will filter the existing data.

## Groups

![Groups](http://thelazyadministrator.com/wp-content/uploads/2018/06/Groups-e1529959616355.png)

The Groups report shows us the name of each group, the type of group, members and the E-mail address of each group. Below is an interactive char that gives us an overview of what types of groups are found in our tenant. As we see above, my tenant is made up of mostly Distribution Groups.

## Licenses

![Licenses](http://thelazyadministrator.com/wp-content/uploads/2018/06/licenses-e1529959644835.png)

The Licenses report displays each license in the tenant and their total counts, assigned count and unassigned count. Using a PowerShell HashTable we are able to convert the SkuID of the license and convert it to a much friendlier name. If the HashTable doesn’t have the SkuId it will default back to the SKU.

Below that we have two interactive charts that show total licenses by type of license and another chart that show licenses assigned by type. In this tenant, we have much more E3 licenses assigned than we do Office ProPlus.

## Users

![Licenses](http://thelazyadministrator.com/wp-content/uploads/2018/06/userdash.png)

The Users report displays a wealth of information. Here you will have the Name of all your users, their UserPrincipalName, which license each user has assigned to them, the last login, If the user is disabled or not, and finally all of their alias e-mail addresses.

You can also report on users last logon timestamp by changing the $IncludeLastLogonTimestamp variable to $True

The data table will display the first 15 results, we can have it display 15, 25, 50, 100 or All the results by using the drop-down on the top left corner. We can filter the current data by using the search bar in the top right-hand corner.

The chart displays licensed users and unlicensed users. In my tenant, I have a little more users without a license than I do with them.

## Shared Mailboxes

![Shared Mailboxes](http://thelazyadministrator.com/wp-content/uploads/2018/06/SharedMBX.png)

Shared Mailboxes will display the name of each Shared Mailbox, the primary email, and all other alias e-mail addresses.

Contacts


The Contacts report has two separate reports contained within it. The first report is the Mail Contact report which will display the name of each Mail Contact and their external e-mail address. The second report is the Mail Users report which will display the name of each Mail User, the primary e-m, il and all other alias e-mail addresses.

Resources


Similarly to the Contact report, the Resources report has two reports within it. The first one is Room Mailboxes and will display each Room Mailbox Name, Primary E-Mail, and all other alias e-mail addresses.

The second report is Equipment Mailboxes and will display each Equipment Mailbox Name, Primary E-Mail and all other alias e-mail addresses.

Features
Charts
The report contains rich interactive charts. When you hover over it you will see the values.



Filter Data
Using Data Tables we can filter the dataset to find exactly what we need. In my example below I want to see all groups that Brad Robertson is a member of. If I have a lot of groups I may not want to spend the time trying to find his name.



By just typing “Brad” I can see the only group he is a member of is a Distribution List named “Managers”. You can even see that as we start typing the data is already being filtered out before we even finish.

Ordering
By default all the data you will automatically be ordered alphabetically by name. But if you want to order it by something else you can by clicking on that property. In my example, I want to find all users that are currently locked-out or disabled. By clicking on the “Disabled” property in the user’s report I can see which users show a “True”. It will filter against all users, even though by default I am only showing the first 15 results.



Friendly License Names
By using a HashTable we can convert the AccountSKU to a much more friendly name. If the HashTable does not have a friendly name for the SKU it will fail back and use the SKU



How to Run the Script
If you don’t’ need to modify anything with the report at all then this will be incredibly simple to run because it only requires 2 modules and if you have Office 365, odds are you already have one of them.

Once you have the 2 modules installed, copy or download the script and you can just run it as is (but you may want to modify the first 3 lines where it specifies the left image, right image and output path). It will prompt you for Office 365 credentials so it can connect to Office 365 to extract the data.

Modules
You need two modules to run this report

ReportHTML
MSOnline
Permissions
No special permissions are required. You don’t need to set up a registered app or API access. It’s best to use your tenant administrator account which is most likely the account you use anyways when managing Office 365 via PowerShell.

Etc..
You will most likely want to modify the first 3 lines of the script, these determine the left logo, right logo and the directory you save the report in. Once the script has finished running it will launch the HTML report automatically as well.



The great part of having an HTML report is when you send it to your customer or manager, they can interact with it the same way you do. There are no extra files needed, everything is embedded within the HTML file.

If you want to play more with the ReportHTML module I recommend checking out this website. It takes a little bit to learn how everything is formatted but once you grasp the formatting you will realize how easy making HTML reports using the module is.

You can find this report also on GitHub here. As I modify the report I will update this article and the GitHub repository.
