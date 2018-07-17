---
title: Standards Recommendations
---

- [Home](index.md)
- [Charter](charter.md)

## Standards Recommendations

### Locations

The recommendation for location codes is to use **UN/LOCODE**. Other codes can be used, but must be specified in the request. Additionally, the **UN/LOCODE** version should be specified in the same object as the code.

```
{
    "code":"USLAX",
    "standard":"UNLOCODE",
    "version":"2018-1"
}
```

The recommendation for terminals is to use **SMDG** codes. Non-existent codes can be requested through the [SMDG website](http://www.smdg.org/smdg-code-lists/). Additionally, custom codes can be used as needed, but will be integration specific. If there is no `standard` field, the `terminal_code` will be considered custom.

```
{
    "standard":"SMDG",
    "unlocode":"USLAX",
    "terminal_code":"APMT"
}
```

### Currency

The recommendation for currency is to use **ISO 4217** codes. All currency representations should be an object, with both the currency code and the amount included as attributes.

```
{
    "code":"USD",
    "amount":200.31
}
```

### Dates and Times

Dates and times should be represented using the **ISO 8601** standard format.

```
"2018-07-11T20:26:16+00:00"
```

### Containers

Container sizes and types should use the **ISO 6346** standard codes. Any TEU conversions for containers are considered to be system specific, unless otherwise specified in a custom integration.

```
{
    "type_group":"20GP",
    "size_type":"20G0"
}
```

### Charges

Charge objects should consist of the following fields:
1. The amount, represented using the standard currency object
2. An integration specific charge code
3. A short description
4. An extended description
5. A unit of measure object, with up to 3 attributes
6. The pay party [based on UN/CEFACT Supply Chain Reference Data Model]
7. A calculation method for the charge
8. The date on which the charge should be calculated
9. An object representing the UN/CEFACT freight cost code that represents the charge

```
{
      "amount": {
        "amount": 2.33,
        "currency": "USD"
      },
      "charge_code":"ABC123"
      "short_description": "Handling",
      "extended_description", "Longer handling description",
      "unit_of_measure": {
        "primary_unit": "kg",
        "secondary_unit": "hour",
        "tertiary_unit": "day"
      },
      "pay_party": "Shipper",
      "calculation_method": "Multiply container weight by transit days",
      "calculation_date": "2018-06-06T23:30:23+00:00",
      "un_freight_cost_code": {
        "group": 1,
        "subgroup": 1,
        "detail": 4
      }
    }
 ```

### Equipment Charges


Equipment charges, regionally referred to as Equipment Free Time, Detention, Demurrage, and others, should be described as "Equipment Rental" and "Equipment Storage".

Equipment rental is intended to mean when the equipment is in possession of the shipper.
Equipment storage is intended to mean when the loaded container is in the care of the carrier at a place of receipt or place of delivery.

In the case that no distinction is drawn between the rental and storage (Combined Equipment Free Time), Equipment Rental should be used, and equipment storage should be omitted.

The required fields are:
1. The maximum number of days the equipment can be rented or stored at the specified rate
2. The day type: `CALENDAR` or `BUSINESS`
3. The cost of the equipment rental or storage

```
{
    "days": 12,
    "day_type": "CALENDAR",
    "cost": {
        "amount": 2.33,
        "currency": "USD"
    }
}
```
