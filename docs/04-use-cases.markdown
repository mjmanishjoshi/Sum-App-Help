---
layout: default
title: Use Cases
nav_order: 4
---

# Delivery time constraints
Planning to ensure shipments are to be (un)loaded between allowed operating hours on the locations

## Setup
* [Business Hours]({% link docs/03-setup.markdown %}#business-hours)

# Dangerouse goods constraints
Food and Dangerous Goods should not be planned on the same trip. 

{: .note-title }
> Out of Scope
>
> * **Load Edit:** Planners should be able to override the constraint while editing load manually

## Related
* [Exclusion groups]({% link docs/04-use-cases.markdown %}#exclusion-groups)

## Setup
* [Commodities]({% link docs/03-setup.markdown %}#commodities)
* [Shipments]({% link docs/03-setup.markdown %}#shipments)

# Exclusion groups
You are shipping goods for a supermarket chain from a distribution center to retail stores, and want to
create loads that, if possible, do not mix perishable goods and non-perishable goods.

{: .note }
> Shipment Group Assignment?

# Equipment constraints
* Total weight / volume of goods shall not exceed equipment capacities
* Allowed total weight / volume may further vary per country

{: .note }
>To setup country specific allowed total weight, planner shall define -
>* Country specific equipment types with their restrictions e.g. 53FT_US, 53FT_DE
>* Define zones at country level e.g. ALLUS, ALLDE
>* Define lanes e.g. origin: ALLUS, destination: ALLUS, equipment: 53FT_US

## Setup
* [Equipments]({% link docs/03-setup.markdown %}#equipments)
* [Contract Rates]({% link docs/03-setup.markdown %}#contract-rates)

# Finite scheduling
* Load start and end date shall be computed based on stop sequence, transit times, loading and unloading times

{: .note-title }
> Out of Scope
>
> * Scheduling based on delivery schedules from external sources
> * Real-time integrations and carrier systems may alter the itinerary or dates
associated with a delivery schedule associated with a load or booking. 
> * A temporary itinerary and
time table entry will be created to allow scheduling to process the load or trip. 

# Execution mode scheduling