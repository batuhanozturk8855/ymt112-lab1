# Task 5: Smart Home Security System — Pseudocode

## System Description
Models the alarm and notification processes of an IoT-based smart home security system.

---

```
START

PRINT "Smart Home Security System Initializing..."

IF system is active THEN
    PRINT "System is ARMED. Monitoring started."
ELSE
    PRINT "System is DISARMED. No monitoring active."
    END
END IF

── INFINITE MONITORING LOOP ──
LOOP WHILE TRUE:

    READ all sensor data

    ── Motion Sensor Check ──
    IF motion_sensor detects movement THEN
        SET threat_detected = YES
    END IF

    ── Door / Window Sensor Check ──
    IF any door_sensor or window_sensor is triggered THEN
        SET threat_detected = YES
    END IF

    IF threat_detected == YES THEN

        ACTIVATE camera
        CAPTURE image/video footage

        ── False Alarm Check ──
        IF homeowner_at_home == YES THEN
            PRINT "Possible false alarm — homeowner is at home."
            PRINT "Was this a false alarm? (YES/NO)"
            READ false_alarm_response

            IF false_alarm_response == YES THEN
                PRINT "False alarm confirmed. Resetting sensors."
                RESET all sensors
                SET threat_detected = NO
                CONTINUE to next loop iteration
            END IF
        END IF

        ── Determine Alarm Level ──
        IF motion_sensor AND door_sensor both triggered THEN
            SET alarm_level = 3  (HIGH)
        ELSE IF door_sensor OR window_sensor triggered THEN
            SET alarm_level = 2  (MEDIUM)
        ELSE
            SET alarm_level = 1  (LOW)
        END IF

        ── Send Notifications ──
        SEND SMS notification to homeowner
        SEND App push notification
        SEND Email alert

        IF alarm_level == 3 THEN
            CALL emergency services (police)
            SOUND loud alarm siren
        ELSE IF alarm_level == 2 THEN
            SOUND moderate alarm siren
        ELSE
            PRINT "Low threat detected. Homeowner notified."
        END IF

        ── Wait and Re-check ──
        WAIT 30 seconds

        READ updated sensor data

        IF sensors no longer triggered THEN
            PRINT "Threat cleared. Resetting alarm."
            RESET alarm
            SET threat_detected = NO
        ELSE
            PRINT "Threat still active. Re-alerting..."
            Continue loop (alert again)
        END IF

    ELSE
        ── No threat: keep monitoring ──
        WAIT 5 seconds
    END IF

    IF reset_command received THEN
        PRINT "System reset by user. Re-arming..."
        RESET all sensors
    END IF

END LOOP

END
```
