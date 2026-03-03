# Task 4: University Course Registration System — Pseudocode

## System Description
Models all the checks and rules of a student course registration system.

---

```
START

PRINT "University Course Registration System"
PRINT "Enter Student ID:"
READ student_id
PRINT "Enter Password:"
READ password

IF credentials valid THEN
    SET student = retrieve student data
    PRINT "Welcome, " + student.name
    PRINT "Current GPA: " + student.gpa
    PRINT "Total registered credits: " + student.current_credits
ELSE
    PRINT "Invalid login. Access denied."
    END
END IF

SET registering = YES
SET total_credits = student.current_credits

LOOP WHILE registering == YES:

    PRINT "─── Course Registration Menu ───"
    PRINT "1 - View Available Courses"
    PRINT "2 - Add Course"
    PRINT "3 - Drop Course"
    PRINT "4 - View My Registered Courses"
    PRINT "5 - Confirm Registration"
    READ menu_choice

    IF menu_choice == 1 THEN
        DISPLAY list of all available courses with details

    ELSE IF menu_choice == 2 THEN

        PRINT "Enter Course Code:"
        READ course_code

        ── Check 1: Quota ──
        IF course.quota <= 0 THEN
            PRINT "This course is full. Registration failed."
            CONTINUE
        END IF

        ── Check 2: Prerequisites ──
        IF student has NOT completed prerequisites for course THEN
            PRINT "You have not completed the prerequisites for this course."
            CONTINUE
        END IF

        ── Check 3: Schedule Conflict ──
        IF course.schedule conflicts with any already-registered course THEN
            PRINT "Schedule conflict detected. Cannot register."
            CONTINUE
        END IF

        ── Check 4: Credit Limit ──
        IF total_credits + course.credits > 35 THEN
            PRINT "Credit limit exceeded. Maximum is 35 credits."
            CONTINUE
        END IF

        ADD course to student's registered list
        SET total_credits = total_credits + course.credits
        PRINT "Course added: " + course.name + " (" + course.credits + " credits)"

    ELSE IF menu_choice == 3 THEN
        PRINT "Enter Course Code to drop:"
        READ drop_code
        IF course is in student's registered list THEN
            REMOVE course from registered list
            SET total_credits = total_credits - course.credits
            PRINT "Course dropped: " + drop_code
        ELSE
            PRINT "Course not found in your registration."
        END IF

    ELSE IF menu_choice == 4 THEN
        DISPLAY student's current registered courses and total credits

    ELSE IF menu_choice == 5 THEN
        SET registering = NO
    END IF

END LOOP

── Advisor Approval Check ──
IF student.gpa < 2.5 THEN
    PRINT "Your GPA is below 2.5. Advisor approval is required."
    SEND approval request to advisor
    PRINT "An approval request has been sent to your advisor."
    PRINT "Registration will be finalized after advisor approval."
ELSE
    FINALIZE registration in system
    PRINT "Registration confirmed!"
END IF

PRINT "Registration Summary:"
DISPLAY registered courses and total credits

END
```
