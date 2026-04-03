# Detailed Algorithms

## 1. Order Creation Logic
- **Inputs:**
  - **Magazzino Prelievo:** The warehouse from where the items will be taken.
  - **Destination:** The intended location for delivery (e.g., MLV/MET).
  - **Shipping Date:** When the order should be shipped.
  - **Work Order:** Document tracking the order fulfillment.

- **Process:**
  1. Verify Magazzino Prelievo status and availability of items.
  2. Validate destination against allowed locations.
  3. Assign the shipping date based on operational capacity.
  4. Create the order entry linked to the work order and store the status as 'Pending'.

## 2. Order Modification Logic with FLAG02 Check
- **Inputs:**
  - **Order ID**
  - **Modification Details**

- **Process:**
  1. Retrieve the existing order using Order ID.
  2. Validate modification against FLAG02:
     - If FLAG02 is active, allow changes only to specific fields.
     - Log modifications appropriately.
  3. Update the order in the database and set status to 'Modified'.

## 3. Order Line Reassignment When Attributes Change
- **Inputs:**
  - **Order ID**
  - **Changed Attributes**

- **Process:**
  1. Identify all order lines related to the given Order ID.
  2. For each line, check if any attributes have changed.
  3. Reassign lines based on new attributes and save updates.

## 4. Type Order Field Constraint (1 Byte Limitation)
- **Implementation:**
  - Ensure that all type order fields can only accept values within 0-255 (1 byte).
  - Implement validation logic to reject invalid inputs with appropriate error messages.

## 5. Quantity Handling Without Rounding
- **Implementation:**
  - Store quantities as decimal values in the database.
  - Ensure calculations involving quantities preserve decimal precision without rounding. 

## 6. Warehouse Inventory Considerations
- **Process:**
  1. Before creation or modification of orders, check warehouse inventory levels.
  2. Implement triggers to alert when inventory levels fall below set thresholds.
  3. Ensure that warehouse capacity compliance is maintained during order processing.