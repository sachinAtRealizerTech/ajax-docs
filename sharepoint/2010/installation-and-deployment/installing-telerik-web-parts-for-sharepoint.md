---
title: Installing Telerik Web Parts for SharePoint
page_title: Installing Telerik Web Parts for SharePoint | UI for ASP.NET AJAX Documentation
description: Installing Telerik Web Parts for SharePoint
slug: sharepoint/2010/installation-and-deployment/installing-telerik-web-parts-for-sharepoint
tags: installing,telerik,web,parts,for,sharepoint
published: True
position: 0
---

# Installing Telerik Web Parts for SharePoint



## Automatic Installation, Upgrade and Removal

Telerik RadEditor & RadGrid Web Parts for SharePoint 2010 come in a common .wsp solution that contains all the necessary files and deployment information for the Web Parts to be successfully installed on your SharePoint application. In addition, the .wsp is accompanied by an installer that can automatically perform the installation for you. Just download and run the installer application:
>caption 

![](images/installer1.png)
>caption 

![](images/installer3.png)

Behind the scene the installer runs the SP PowerShell deployment commands that automatically deploy the necessary dlls to the GAC, register the corresponding assemblies to the SafeControls section of the SP web.config and add the solution to the SP application. During the installation:

* the following three assemblies are deployed to the GAC: __Telerik.Web.UI.dll, Telerik.Ajax.SharePoint.dll and RadEditorSharePoint.dll.__

* the following entries are added to the SafeControls section of the SP web.config file:

````XML
	    <SafeControl Assembly="Telerik.Web.UI, Version=..., Culture=neutral, PublicKeyToken=121fae78165ba3d4"
	        Namespace="Telerik.Web.UI" TypeName="*" Safe="True" SafeAgainstScript="False" />
	    <SafeControl Assembly="Telerik.Web.UI, Version=..., Culture=neutral, PublicKeyToken=121fae78165ba3d4"
	        Namespace="Telerik.Web.UI.Editor" TypeName="*" Safe="True" SafeAgainstScript="False" />
	    <SafeControl Assembly="Telerik.Web.UI, Version=..., Culture=neutral, PublicKeyToken=121fae78165ba3d4"
	        Namespace="Telerik.Web.UI.Widgets" TypeName="*" Safe="True" SafeAgainstScript="False" />
	    <SafeControl Assembly="Telerik.Web.UI, Version=..., Culture=neutral, PublicKeyToken=121fae78165ba3d4"
	        Namespace="Telerik.Web.Design" TypeName="*" Safe="True" SafeAgainstScript="False" />
	    <SafeControl Assembly="RadEditorSharePoint, Version=6.0.0.0, Culture=neutral, PublicKeyToken=1f131a624888eeed"
	        Namespace="Telerik.SharePoint" TypeName="*" Safe="True" SafeAgainstScript="False" />
	    <SafeControl Assembly="RadEditorSharePoint, Version=6.0.0.0, Culture=neutral, PublicKeyToken=1f131a624888eeed"
	        Namespace="Telerik.SharePoint.FieldEditor" TypeName="*" Safe="True" SafeAgainstScript="False" />
	    <SafeControl Assembly="RadEditorSharePoint, Version=6.0.0.0, Culture=neutral, PublicKeyToken=1f131a624888eeed"
	        Namespace="Telerik.SharePoint.ListFieldEditor" TypeName="*" Safe="True" SafeAgainstScript="False" />
	    <SafeControl Assembly="Telerik.Ajax.Sharepoint, Version=1.0.0.0, Culture=neutral, PublicKeyToken=aa9e5f693af67c7b"
	        Namespace="Telerik.Ajax.SharePoint" TypeName="*" Safe="True" SafeAgainstScript="False" />
````



Once installed and deployed, the Telerik Web Parts can be easily upgraded/removed through the same installer application. The latter automatically detects if the controls have already been deployed and will give you the option to either Repair (Upgrade) or Remove them.

## Manual Installation, Upgrade and Removal

If you prefer to manually perform the above-described process, you can easily do so through the SP PowerShell cmdlets.

1. Install the RadControlsSP solution as follows:__Add-SPSolution -LiteralPath____Install-SPSolution -Identity RadControlsSP.wsp -AllWebApplications -GACDeployment -Force__

1. Upgrade your RadControlsSP solution as follows:__Update-SPSolution –Identity RadControlsSP.wsp –LiteralPath__

1. Removing the RadControlsSP solution is achieved through the following cmdlets. Just keep in mind that the retraction of the solution should be	finished before executing the __Remove-SPSolution__ cmdlet:__Uninstall-SPSolution -Identity RadControlsSP.wsp –AllWebApplications____Remove-SPSolution -Identity RadControlsSP.wsp__

## Enabling SPRadGrid Feature

The Telerik SPRadGrid Web Part is deployed as a site collection feature. Therefore, after the addition and deployment of the web part you need to activate the feature associated with it. To do so, you can either go to __Site Actions -> Site Settings -> Site Collection Administration -> Site Collection Features__ and enable the __SPRadGrid Feature__, or alternatively run the following __SP____PowerShell__ command:

__Enable-SPFeature TelerikSPRadGridWebPart_SPRadGridFeature -Url <__

For an online demonstration of Telerik controls for SharePoint 2010, please, visit out web site at: [http://sharepoint.telerik.com](http://sharepoint.telerik.com)