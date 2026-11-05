# Warehouse tools

Small Python utilities for warehouse order and shipping workflows.

Run the tests with `python3 -m unittest discover -s tests -v`.

## Shipping

`shipping_quote(weight_kg, zone, service="standard")` returns a delivery quote
in US dollars.

| Parameter   | Values                      | Notes                                      |
|-------------|-----------------------------|--------------------------------------------|
| `weight_kg` | positive float              | Parcel weight in kilograms                 |
| `zone`      | `"local"`, `"regional"`     | Delivery zone                              |
| `service`   | `"standard"`, `"express"`   | Service level; defaults to `"standard"`    |

Express shipping adds a flat **$7 surcharge** on top of the standard rate.
Unknown zones or service values raise `ValueError`.

### CLI usage

```
python -m warehouse.cli <weight_kg> <zone> [--service {standard,express}]
```

Examples:

```
# Standard quote – 3 kg, local zone
python -m warehouse.cli 3 local

# Express quote – 3 kg, regional zone
python -m warehouse.cli 3 regional --service express
```
