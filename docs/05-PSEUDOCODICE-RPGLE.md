/* RPGLE Pseudocode for Scheduled Job Processing SEDAPTA_PICKING_LIST */

// 1) Scheduled job that reads SEDAPTA_PICKING_LIST every X minutes via JDBC
JobName: 
    CALL 'scheduleJob' every X minutes;
    OnJobStart:
        DBMS_OUTPUT.PUT_LINE('Job started');
        conn = getJDBCConnection();
    end;

// 2) Main loop for processing records with FLAG01=0
WHILE (true) DO
    records = getRecordsWithFlag(conn, 0); // read records where FLAG01=0
    IF (records.isEmpty()) THEN
        SLEEP(60000); // sleep for 1 minute
        CONTINUE;
    ENDIF;

// 3) Flag management (set to 2 during processing, 1 after import)
    FOR each record IN records DO
        updateFlag(record.id, 2); // set flag to 2 during processing
        // 4) Order header creation/retrieval logic
        orderHeader = getOrCreateOrderHeader(record);
        
        // 5) Order line creation
        CREATE ORDER LINE for orderHeader using record;
        // 6) Error handling and NOTE field population
        IF (hasError) THEN
            record.note = 'Error occurred';
            updateRecord(record);
            CONTINUE;
        ENDIF;
        
        // 7) Transaction management
        COMMIT; // commit transaction after successfully processing
        updateFlag(record.id, 1); // set flag to 1 after import
    END FOR;
END WHILE;

CLOSE connection // on job end
