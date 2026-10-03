## lookup_vehicle

Looks up a UK vehicle by registration number and returns the vehicle the site identifies (make, model, full description, colour, MOT status/date as shown) together with the list of tyre sizes the site offers for it. Each tyre size carries width, profile, rim diameter, speed rating, load index, the vehicle's original-equipment speed rating, and the fitting position (front_and_rear, front or rear) parsed from the site's label. The site does not publish a model year. One page fetch plus one lookup request per call. A registration the site cannot resolve returns a stale_input (input_not_found) error.

### Input
|Param| 	|Type|	Description
|------|------|----|-------------
|registration| $\color{#ff0000}\textsf{required}$ |string	|UK vehicle registration number (e.g. AB12CDE). Letters and digits; spaces are ignored.
