---
layout: default-layout
noTitleIndex: true
needAutoGenerateSidebar: true
title: Are admin right required to install the end-user component?
keywords: Dynamic Web TWAIN, Project Deployment and End-user Installation, sdmin right, install
breadcrumbText: Are admin right required to install the end-user component?
description: Are admin right required to install the end-user component?
permalink: /faq/admin-right-needed-to-install.html
---

View all FAQs about [Project Deployment and End-user Installation](
https://www.dynamsoft.com/web-twain/docs/faq/#project-deployment-and-end-user-installation)

# Are admin rights required to install the end-user component?

Yes, the Dynamsoft Service installer is a `.msi` file which requires administrator rights to install as the install target is `C:\Windows\SysWOW64\`. Once the Dynamsoft Service is installed with admin rights, every user on that machine can has access to the Dynamsoft Service. 

If your organization does not allow end users to have admin rights, you can contact [Dynamsoft Support]({{site.about}}getsupport.html) to get a special "Personal Installer" that does not require admin rights.

The "Personal Installer", will install to the user's `C:\Users\{UserName}\AppData\Roaming\` folder. Please be aware that only one user per machine is able to have the service installed via this method. The service cannot be installed to multiple user profiles, and only the user that installs the Services in this manner will have access to the Dynamsoft Service.
