---
layout: acs-aem-commons_feature
title: Brand Portal Sync 
description: Sync AEM assets with Brand Portal from AEM Workflow
sub-feature: true
date: 2017-08-13
initial-release: 3.10.0
tags: new
---

## Purpose

As of the introduction of this feature, AEM can only un/publish to/from AEM Assets Brand Portal using the buttons in the AEM Assets Web UI.

This workflow process facilitates un/publishing assets to/from Brand Portal from AEM Workflow. 

This is useful when assets should only be published to Brand Portal after a review process; the final step of the review workflow can now be "Publish to Brand Portal".

## How to Use

### Create a Workflow process step

Create a new Workflow Process step that points to this workflow process implementation. 

![Workflow - Brand Portal Sync](images/workflow-process-configuration.png)


### Process Args Options

The Process Args are to be set to either `ACTIVATE` or `DEACTVIATE` based on the desired replication action.

If left blank, defaults to `ACTIVATE`;

## Setting `mpConfig` on the Asset Folder

In order to publish to Brand Portal, the asset to be un/published must be a descendant of an Assets Folder that has an `mpConfig` property set, pointing to the Brand Portal cloud service configuration.
    
    `/content/dam/.../[sling:OrderedFolder]/jcr:content/mpConfig=/etc/cloudservices/mediaportal/brand-portal`
    
AEM does not support the additional of author-able Asset Folder properties OOTB, so the `mpConfig` property must be

* Set manually by development/operations via node manipulation (ideally part of the application project)
* Select the top-level folder from the AEM Assets Web UI and click `Publish to Brand Portal` to set this property. Note that doing this will ALSO publish any descendant assets to Brand Portal.
* Use [ACS AEM Commons Asset Folder Properties](/acs-aem-commons/features/assets-folder-properties-support/index.html) feature to add an author-able `mpConfig` property to Assets Folder properties.  
         