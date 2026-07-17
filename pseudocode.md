# Pseudocode — Hotel Room Booking System

```
BEGIN
    DISPLAY system title

    INPUT numberOfBookings
    WHILE numberOfBookings <= 0
        DISPLAY "Invalid entry"
        INPUT numberOfBookings
    END WHILE

    OPEN hotel_booking_report.txt FOR WRITING

    confirmedCount = 0
    pendingCount = 0

    FOR each booking FROM 1 TO numberOfBookings DO
        INPUT guestName, phoneNumber, roomType
        WHILE roomType is NOT valid DO
            DISPLAY "Invalid room type"
            INPUT roomType
        END WHILE

        INPUT roomNumber

        INPUT numberOfNights
        WHILE numberOfNights <= 0 DO
            DISPLAY "Invalid number of nights"
            INPUT numberOfNights
        END WHILE

        INPUT paymentStatus

        DETERMINE roomRate FROM roomType
            IF roomType = "Single" THEN roomRate = 150
            ELSE IF roomType = "Double" THEN roomRate = 250
            ELSE IF roomType = "Executive" THEN roomRate = 400
            END IF

        totalCost = roomRate * numberOfNights

        IF paymentStatus = "Paid" THEN
            bookingStatus = "Confirmed Booking"
            confirmedCount = confirmedCount + 1
        ELSE
            bookingStatus = "Pending Payment"
            pendingCount = pendingCount + 1
        END IF

        DISPLAY booking report
        SAVE booking report TO file
    END FOR

    DISPLAY confirmedCount, pendingCount
    SAVE confirmedCount, pendingCount TO file

    CLOSE file
    DISPLAY "Report saved as hotel_booking_report.txt"
END
```
