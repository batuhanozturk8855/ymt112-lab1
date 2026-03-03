# Task 3: Hospital Appointment and Test Results System — Pseudocode

## System Description
Models a hospital system for making appointments and accessing laboratory test results.

---

```
START

PRINT "Welcome to the Hospital System"
PRINT "Please enter your ID number:"
READ patient_id

IF patient_id exists in system THEN
    SET patient = retrieve patient data
    PRINT "Welcome, " + patient.name
ELSE
    PRINT "Patient not found. Please register at the reception."
    END
END IF

SET another_action = YES

LOOP WHILE another_action == YES:

    PRINT "Please select an action:"
    PRINT "1 - Make Appointment"
    PRINT "2 - View Test Results"
    READ action_choice

    ─────────────────────────────────────────
    MODULE 1: MAKE APPOINTMENT
    ─────────────────────────────────────────
    IF action_choice == 1 THEN

        PRINT "Select a clinic:"
        DISPLAY list of clinics
        READ clinic_choice

        DISPLAY list of doctors in selected clinic
        READ doctor_choice

        SET slot_selected = NO

        LOOP WHILE slot_selected == NO:
            DISPLAY available time slots for chosen doctor
            PRINT "Select a time slot (or 0 to go back):"
            READ slot_choice

            IF slot_choice == 0 THEN
                BREAK out of slot loop
            ELSE IF slot_choice is available THEN
                CONFIRM appointment
                SAVE appointment to system
                SEND SMS notification to patient
                PRINT "Appointment confirmed for " + date + " at " + time
                SET slot_selected = YES
            ELSE
                PRINT "That slot is no longer available. Please choose another."
            END IF
        END LOOP

    ─────────────────────────────────────────
    MODULE 2: VIEW TEST RESULTS
    ─────────────────────────────────────────
    ELSE IF action_choice == 2 THEN

        IF patient has any test orders THEN

            DISPLAY list of patient tests

            IF test results are ready THEN
                DISPLAY test results on screen
                PRINT "Would you like to download results as PDF? (YES/NO)"
                READ download_choice

                IF download_choice == YES THEN
                    Generate PDF
                    PRINT "PDF downloaded successfully."
                END IF

            ELSE
                PRINT "Your test results are not ready yet."
                PRINT "Please check back later or contact the laboratory."
            END IF

        ELSE
            PRINT "No test orders found for your account."
        END IF

    ELSE
        PRINT "Invalid selection. Please try again."
    END IF

    PRINT "Would you like to perform another action? (YES/NO)"
    READ another_action

END LOOP

PRINT "Thank you. Goodbye!"

END
```
