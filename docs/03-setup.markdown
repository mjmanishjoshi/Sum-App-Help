---
layout: default
title: Getting Started
nav_order: 3
# bundle exec jekyll serve --livereload
# https://www.lipsum.com/
# https://yeoman.io/
# https://fakerjs.dev/guide/
# https://www.npmjs.com/package/casual
---

# Getting Started
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras tortor lorem, pretium non eleifend a, dictum quis nisi. Suspendisse tincidunt nec ligula eget elementum. Aenean porta magna magna. Duis quis mollis ligula, sit amet sagittis urna. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Suspendisse potenti. Donec eu sagittis nulla, at sodales tortor. Quisque leo augue, porta vitae scelerisque a, luctus in dolor. Cras pellentesque sodales sem, at rhoncus magna iaculis in. Etiam efficitur magna ac ante fermentum, at placerat massa volutpat.

## Locations
Locations are the actual locations for the facilities in your network. Each location represents all places to
be used in a scenario, so you must define all locations before you can build a model.

{: .note }
Locations support for distinct Inbound and Outbound Business Hours? See [Business Hours]({% link docs/03-setup.markdown %}#business-hours) for more details.

```json
[
  {
    "documentActionCode": "ADD",
    "locationId": "...",
    "basicLocation": {
      "locationTypeCode": "CONSIGNEE",
      "locationName": "...",
      "address": {
        ...
      },
      "contact": {
        ...
      },
      "operatingHours": {
        ...
      }
    }
  }
]
```

## Docks

## Business Hours
Business Hours represent the hours that a location or hub is open for
business. You can define business hour exceptions for specific dates in the Business Hours
Exceptions.

{: .note }
Business Hours categories? Rush Hour Definition?

```json
{
    "operatingHours": {
        "utcOffset": ...,
        "daylightSavingsOffset": ...,
        "timeZoneCode": "...",
        "regularOperatingHours": [
            {
                "dayOfTheWeekCode": "MONDAY",
                "isOperational": true,
                "openingTime": "08:00:00",
                "closingTime": "23:00:00"
            },
            {
                "dayOfTheWeekCode": "TUESDAY",
                "isOperational": true,
                "openingTime": "08:00:00",
                "closingTime": "23:00:00"
            },
            {
                "dayOfTheWeekCode": "WEDNESDAY",
                "isOperational": true,
                "openingTime": "08:00:00",
                "closingTime": "23:00:00"
            },
            {
                "dayOfTheWeekCode": "THURSDAY",
                "isOperational": true,
                "openingTime": "08:00:00",
                "closingTime": "23:00:00"
            },
            {
                "dayOfTheWeekCode": "FRIDAY",
                "isOperational": true,
                "openingTime": "08:00:00",
                "closingTime": "23:00:00"
            },
            {
                "dayOfTheWeekCode": "SATURDAY",
                "isOperational": false
            },
            {
                "dayOfTheWeekCode": "SUNDAY",
                "isOperational": false
            }
        ],
        "specialOperatingHours": [{
            "specialDate": "2023-12-25",
            "isOperational": false
        }]
    }
}
```

## Commodities
You can associate commodity codes with shipment records and also use them to define
commodity exclusions. You can use commodity exclusions to prevent shipments of particular
commodity types from being put on the same load during optimization.

```json
[
  {
    "documentActionCode": "ADD",
    "commodityId": "...",
    "freightClassCode": "FAK",
    "hazardousClass": "1.1",
    "commodityExclusion": [
      {
        "commodityId": {
          ...
        },
        "transportEquipmentTypeCode": {
          ...
        },
        "equipmentCompartmentId": "..."
      }
    ]
  }
]
```

## Equipments
Define equipment type used in transporting a load. An eqiupment type contains following information -
* Equipment dimensions e.g. length, width, height
* Usage constraints e.g. loading weight, loading volume
* Load configuration details for 3D load plan
* Scheduling information
* Commodity restrictions

```json
[
  {
    "documentActionCode": "ADD",
    "transportEquipmentId": "...",
    "equipmentCategory": "EQMTCAT_TRCTR_TRLR",
    "length": {
      ...
    },
    ...
    "usageThresholdValues": [
      {
        "measurementType": "WEIGHT",
        "minimumAllowableValue": 0,
        "maximumAllowableValue": 15000,
      }
    ],
    "commodityRestrictions": [
      {
        "commodityCode": "...",
        "restrictionCode": "IER_EXCLUDE"
      }
    ]
  }
]
```

# Shipments

# Contract Rates

## Tariff Service Equipments
## Lanes
## Restrictions