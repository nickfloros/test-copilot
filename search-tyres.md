## Search tyres

Returns the tyres the site lists for one tyre size (width/profile/rim), optionally narrowed by the site's speed-rating filter. One page fetch per call; the site returns the full listing on one page (typically 20-30 tyres, no pagination), so total_results is the number of distinct tyres returned. Each tyre carries a stable tyre_id and product_url (pass product_url unchanged to get_tyre), brand, model (pattern name), full size string, speed rating and load index, fully fitted price per tyre in GBP (price, price_type 'fully_fitted') and the mail-order price, EU label values (fuel_efficiency, wet_grip, noise_db, noise_rating), run_flat, season (summer, all_season or winter), the earliest fitting date the site offers and a matching availability_note, and the site's multibuy promotion code when one is advertised. A size the site has no listing for returns a stale_input (input_not_found) error. The speed filter is applied by the site and may include tyres of a higher rating than requested.

### Input
Param | required	| Type |	Description
----- |-----------|----- |-------------- 
rim |required	| string	|Rim diameter in inches, digits only (e.g. 16); a leading R is accepted.
speed	|optional|string|	Optional speed-rating filter. Omit to return all speed ratings for the size.
width|required	|string	|Tyre section width in mm, digits only (e.g. 205).
profile |required |	string	|Tyre aspect ratio / profile, digits only (e.g. 55).

### Response
```json
{
  "type": "object",
  "fields": {
    "size": "requested size as 'width/profile Rrim'",
    "speed": "speed filter applied, or null when omitted",
    "tyres": "array of tyre listings: tyre_id, name, brand, model, size, width, profile, rim, speed_rating, load_index, price (GBP fully fitted, number), price_type, mail_order_price (GBP, number), currency, fuel_efficiency, wet_grip, noise_db (integer), noise_rating, run_flat (boolean), season, earliest_fitting_date (YYYY-MM-DD), availability_note, promotion_code, product_url",
    "total_results": "number of distinct tyres returned (the full listing)"
  },
  "sample": {
    "data": {
      "size": "205/55 R16",
      "speed": null,
      "tyres": [
        {
          "rim": "16",
          "name": "Kumho Ecowing ES31 205/55 R16 V (91)",
          "size": "205/55 R16",
          "brand": "Kumho",
          "model": "Ecowing ES31",
          "price": 69.99,
          "width": 205,
          "season": "summer",
          "profile": 55,
          "tyre_id": "37163882",
          "currency": "GBP",
          "noise_db": 70,
          "run_flat": false,
          "wet_grip": "B",
          "load_index": "91",
          "price_type": "fully_fitted",
          "product_url": "https://www.blackcircles.com/brands/kumho/ecowing-es31/205-55-r16-v-91?tyre=37163882",
          "noise_rating": "B",
          "speed_rating": "V",
          "promotion_code": "2tyre10-4tyre20",
          "fuel_efficiency": "B",
          "mail_order_price": 51.09,
          "availability_note": "Earliest fitting date 2026-09-24",
          "earliest_fitting_date": "2026-09-24"
        },
        {
          "rim": "16",
          "name": "Michelin CrossClimate 3 205/55 R16 V (94)",
          "size": "205/55 R16",
          "brand": "Michelin",
          "model": "CrossClimate 3",
          "price": 109.99,
          "width": 205,
          "season": "all_season",
          "profile": 55,
          "tyre_id": "48318291",
          "currency": "GBP",
          "noise_db": 72,
          "run_flat": false,
          "wet_grip": "B",
          "load_index": "94",
          "price_type": "fully_fitted",
          "product_url": "https://www.blackcircles.com/brands/michelin/crossclimate-3/205-55-r16-v-94?tyre=48318291",
          "noise_rating": "B",
          "speed_rating": "V",
          "promotion_code": "2tyre20-4tyre40",
          "fuel_efficiency": "B",
          "mail_order_price": 91.09,
          "availability_note": "Earliest fitting date 2026-09-24",
          "earliest_fitting_date": "2026-09-24"
        }
      ],
      "total_results": 22
    },
    "status": "success"
  }
}
```
