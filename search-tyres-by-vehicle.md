## search_tyres_by_vehicle


Searches for tyres by UK vehicle registration number and postcode. First looks up the vehicle to determine compatible tyre sizes, then returns tyre listings for the first available size. Results include fully fitted prices, EU tyre label ratings (fuel efficiency, wet grip, noise), season type, and run-flat status. Returns a single composite result containing vehicle details and all matching tyres (typically 15-25 per size).

### input
|Param	|required|Type|	Description
|-------|--------|----|-------------
postcode|required|	string|	UK postcode for local fitting availability and pricing (e.g. EH1 1BE, L1 8JQ).
registration|required|	string	|UK vehicle registration number (e.g. SP55ZXL, BD51SMR). Letters and numbers only, no spaces required.

### Response

```json
{
  "type": "object",
  "fields": {
    "tyres": "array of matching tyre listings with pricing and specifications",
    "vehicle": "object containing registration, vehicle name, colour, and MOT expiry",
    "tyre_sizes": "array of available tyre size options with value codes and labels",
    "selected_size": "string code of the tyre size used for the search"
  },
  "sample": {
    "data": {
      "tyres": [
        {
          "name": "Michelin CrossClimate 3 205/55 R16 V (91)",
          "price": 109.99,
          "season": "all_season",
          "tyre_id": "48318247",
          "featured": true,
          "noise_db": 72,
          "run_flat": false,
          "wet_grip": "B",
          "noise_rating": "B",
          "fuel_efficiency": "C"
        }
      ],
      "vehicle": {
        "colour": "Silver",
        "vehicle": "FORD FOCUS GHIA TDCI",
        "mot_expiry": "18 October 2008",
        "registration": "SP55ZXL"
      },
      "tyre_sizes": [
        {
          "label": "205/55R16 H 91 Fitted to front and rear",
          "value": "205_55_16_H_91"
        }
      ],
      "selected_size": "205_55_16_H_91"
    },
    "status": "success"
  }
}
```
