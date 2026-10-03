## get_tyre

Returns one tyre's current listing from its product page so the price can be confirmed: the same fields as a search_tyres row (tyre_id, brand, model, size, speed/load, fully fitted price and mail-order price in GBP, EU label values, run_flat, season, promotion code, product_url). The product page does not show a fitting date, so earliest_fitting_date and availability_note are null here. One page fetch per call. A product_url whose tyre id the site no longer recognises returns a stale_input (input_not_found) error; a URL that is not a blackcircles.com tyre page returns stale_input (input_format_invalid).

### Input

|Param|required|	Type|	Description
|-----|--------|------|------------
product_url|required|string|	Tyre product page URL exactly as returned in search_tyres.tyres[*].product_url (a blackcircles.com /brands/... path with a tyre= id).

### Response
```json
{
  "type": "object",
  "fields": {
    "name": "full tyre name including size, speed and load",
    "size": "size string 'width/profile Rrim'",
    "brand": "tyre brand",
    "model": "tyre model / pattern name",
    "price": "fully fitted price per tyre in GBP (number)",
    "season": "summer, all_season or winter",
    "tyre_id": "stable site product id of the tyre",
    "noise_db": "EU label exterior noise in dB (integer)",
    "run_flat": "boolean, true when the site marks the tyre as run flat",
    "wet_grip": "EU label wet grip class A-E",
    "load_index": "load index as a string",
    "price_type": "always 'fully_fitted'",
    "product_url": "canonical product page URL",
    "noise_rating": "EU label noise class A-C",
    "speed_rating": "speed rating letter",
    "promotion_code": "site multibuy promotion code when advertised, else null",
    "fuel_efficiency": "EU label fuel efficiency class A-E",
    "mail_order_price": "mail-order (tyre only, delivered) price per tyre in GBP; null when not shown",
    "availability_note": "null on the product page (only available from search_tyres)",
    "earliest_fitting_date": "null on the product page (only available from search_tyres)"
  },
  "sample": {
    "data": {
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
      "availability_note": null,
      "earliest_fitting_date": null
    },
    "status": "success"
  }
}
```
