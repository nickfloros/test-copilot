## lookup_vehicle

Looks up a UK vehicle by registration number and returns the vehicle the site identifies (make, model, full description, colour, MOT status/date as shown) together with the list of tyre sizes the site offers for it. Each tyre size carries width, profile, rim diameter, speed rating, load index, the vehicle's original-equipment speed rating, and the fitting position (front_and_rear, front or rear) parsed from the site's label. The site does not publish a model year. One page fetch plus one lookup request per call. A registration the site cannot resolve returns a stale_input (input_not_found) error.

### Input
|Param| 	|Type|	Description
|------|------|----|-------------
|registration| $\color{#ff0000}\textsf{required}$ |string	|UK vehicle registration number (e.g. AB12CDE). Letters and digits; spaces are ignored.

### Response
```
{
  "type": "object",
  "fields": {
    "make": "vehicle make in the site's lower-case form",
    "model": "vehicle model/trim in the site's lower-case form",
    "colour": "vehicle colour",
    "mot_date": "MOT expiry/due date as displayed text; null when not shown",
    "mot_status": "MOT label shown by the site (e.g. 'MOT expired' or 'MOT due'); null when not shown",
    "tyre_sizes": "array of tyre size options: size_code (site code usable as selected_size), width (integer mm), profile (integer), rim (string inches), speed_rating, load_index, original_speed_rating, position (front_and_rear|front|rear|null), position_text, label",
    "description": "full vehicle description as displayed (make, model, trim)",
    "registration": "registration as shown by the site"
  },
  "sample": {
    "data": {
      "make": "ford",
      "model": "focus ghia tdci",
      "colour": "Silver",
      "mot_date": "18 October 2008",
      "mot_status": "MOT expired",
      "tyre_sizes": [
        {
          "rim": "16",
          "label": "205/55R16 H 91 Fitted to front and rear",
          "width": 205,
          "profile": 55,
          "position": "front_and_rear",
          "size_code": "205_55_16_H_91",
          "load_index": "91",
          "speed_rating": "H",
          "position_text": "Fitted to front and rear",
          "original_speed_rating": "W"
        }
      ],
      "description": "FORD FOCUS GHIA TDCI",
      "registration": "SP55ZXL"
    },
    "status": "success"
  }
}
```
