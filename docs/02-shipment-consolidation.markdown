---
layout: default
title: Shipment consolidation
nav_order: 2
---

# Shipment consolidation
This section covers the requirements for successful shipment consolidation modeling. To ensure that the
output from Transportation Planner meets your needs, you must have a clear idea of the business
requirements that you want to achieve, and also to express them in terms of optimizer data, entities,
and features. Work with a Blue Yonder consultant to ensure that your business requirements are
effectively modeled in Transportation Planner.

## Create tariffs
Setting up your tariff structure is crucial to achieve good shipment consolidation results from
Transportation Planner. This should be done with the help of a Blue Yonder consultant. For more
information, see "Tariffs and rating overview"

## Understand how to influence shipment consolidation results
In addition to setting up realistic and accurate tariffs that reflect your business, to use Transportation
Planner effectively, you should also understand the ways in which you can influence shipment
consolidation results.

### Shipment consolidation constraints
Constraints are limitations that you place on how Transportation Planner performs shipment
consolidation. Transportation Planner minimizes transportation costs based on the business rules and
tariff structures. However, your real world business requirements usually have additional factors, such as
a carrier’s capacity limitations, limits on unloading capacity at a particular hub at any time, and so on.

In general, you create constraints by enabling the applicable constraint function in the strategy file (for
example, EnforceHubConstraints) and specifying the constraint parameters (for example, maximum
inbound loads = 10). You define the constraint parameters in Transportation Manager (with the
exception of hub constraints). Alternately, you can define them in a constraint file, and point to that
constraint file in either the Setup.xml file or in the optimizer options. You must then define penalties
associated with the constraint parameters, either at the global level (in the OptParameters.txt file), or at
a more granular level (such as carrier or tariff/service level). Transportation Planner uses these assigned
penalties in its internal plan costs to compare the various optimization possibilities; the penalty amounts
are not actually added to the total plan cost that is visible in the optimization results.

{: .note }
Penalties at a more granular level override those defined at a higher level. Also, if a load
violates more than one set of constraints, it may incur more than one set of penalties.

After setting constraints, you can further influence how Transportation Planner plans load by increasing
or decreasing specific penalties. You can soften one constraint by decreasing its associated penalty and
harden another constraint by increasing its associated penalty.

{: .note }
When you modify your constraint files, generate your rating engine before you re-optimize, as
you have redefined the rating parameters.

#### Constraint file format
The fields in the constraint files are separated with a comma (,) delimiter. The field order in these files is fixed.

#### Specify constraint files
You can set the paths for the constraint files that Transportation Planner uses.

{: .note }
The constraint files that are available to you depend on the rating engine that you have
selected for use with Transportation Planner.

#### Specify constraint files for optimizer with Transportation Manager requests
Typically, you define constraints directly in the Transportation Manager data model. However, you can
override any constraints that are defined in Transportation Manager:
1. Enable constraint overrides in Transportation Manager.
2. Specify the locations of the constraint files the optimizer should use, in ConstraintsOverride.txt.

{: .note }
Constraint files override those defined in Transportation Manager. The ConstraintOverride.txt file overrides any other constraints or constraint files.

#### Specify constraint files in the Transportation Planner user interface
1. Select the Setup page.
2. Select the server where constraints are specified and click Server Configuration. The Edit Server
Configuration page is displayed.
3. Click the Main tab.
4. Enter the full path of the constraint file, or use Browse to navigate to the file in the appropriate
field.

#### Specify constraint files in optimizer for XML plans
1. Open the Setup.xml file. By default, this file is located in the C:\by\tp\2021.1.0.0\sce or
/opt/by/tp/2021.1.0.0/scedirectory.
2. Add a line that defines the type of constraint you are imposing and the constraint file that should
be used. For example:

```xml
<HubConstraintsFile>HubConstraints.txt</HubConstraintsFile>
```