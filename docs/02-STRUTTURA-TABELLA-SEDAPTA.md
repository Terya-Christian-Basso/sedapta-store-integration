# SEDAPTA_PICKING_LIST Table Documentation

## Overview
This document outlines the structure and details of the `SEDAPTA_PICKING_LIST` table.

| Field Name                 | Data Type      | Description                                                           | Business Meaning                                                  |
|----------------------------|----------------|-----------------------------------------------------------------------|------------------------------------------------------------------|
| CODICE_ORDINE              | VARCHAR         | Unique identifier for the order.                                     | Represents the specific order associated with the picking.        |
| CODICE_PARTE               | VARCHAR         | Code of the part being picked.                                      | Identifies the part within the inventory system.                  |
| CODICE_VERSIONE             | VARCHAR         | Version code of the part.                                           | Reflects the version of the part, if applicable.                  |
| QUANTITA                   | INTEGER         | Quantity of the item being picked.                                  | Specifies how many items are associated with this order.          |
| UN_QUANTITA                | VARCHAR         | Unit of measure for quantity (e.g., pieces, kilograms).            | Denotes the measurement unit for the quantity.                    |
| IDENTIFICATIVO_LOTTO       | VARCHAR         | Lot identifier for the items.                                       | Connects items to specific production lots.                        |
| DATA_CONSEGNA               | DATETIME       | Delivery date and time for the order.                               | Indicates when the items should be delivered.                     |
| CUST_ATTR01                | VARCHAR         | Custom attribute 01.                                                | Allows for added flexibility to store additional attributes.       |
| CUST_VAL01                 | VARCHAR         | Value for custom attribute 01.                                      | Value corresponding to the custom attribute.                       |
| CUST_DATA01                | DATETIME       | Date for custom attribute 01.                                       | Date associated with the custom attribute.                         |
| FLAG01                     | BOOLEAN         | A flag indicating specific status (e.g., processed).                | Provides a way to mark the order's processing state.              |
| FLAG02                     | BOOLEAN         | Another flag for additional processing status.                       | Allows tracking of secondary statuses.                             |
| DATA01                     | DATETIME       | Additional date field.                                             | Custom use based on business logic.                                |
| NOTE01                     | TEXT            | Notes related to the order.                                         | Any relevant comments or notes for the order.                     |
| NOTE02                     | TEXT            | Additional notes related to the order.                              | Further remarks or details regarding special circumstances.        |

## Conclusion
This documentation provides essential information regarding the `SEDAPTA_PICKING_LIST` table, which is critical for order processing and management. Proper understanding of each field's function can enhance efficiency and accuracy in handling orders.