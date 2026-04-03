# FLAG01/FLAG02 Synchronization Mechanism

## FLAG01 States
- **0 (da acquisire)**: This state indicates that the order is yet to be acquired.
- **1 (importato)**: This state means that the order has been successfully imported.
- **2 (in elaborazione)**: This state signifies that the order is currently being processed.

## FLAG02: Evaded Orders
FLAG02 is utilized to track orders that have been evaded. It plays a crucial role in how the system differentiates between orders that are still active and those that need further attention due to evasion.

## Step-by-Step Synchronization Process
1. **Initialization**: Begin by checking the current statuses of FLAG01. All entries with a state of `0` will need to be flagged for acquisition.
2. **Processing**: Orders marked with state `2` are processed sequentially. The system will update their status to `1` once they are successfully imported.
3. **Evaded Handling**: For orders that fall under FLAG02, the system identifies them during the checking phase to ensure they are addressed appropriately. If an order requires re-evaluation after being evaded, it will be flagged for review.
4. **Final Updates**: Once changes are made successfully to any orders, the statuses are updated accordingly in both FLAG01 and FLAG02 to reflect the latest state.

## Handling Modifications on Already Evaded Orders
Any modifications made to orders that were previously evaded involve a verification step where the system; checks if the changes align with the current FLAG01 status. If not, the order must revert to the initial `evaded` state until the modifications are finalized and resubmitted for processing.