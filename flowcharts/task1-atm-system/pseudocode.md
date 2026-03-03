# Task 1: ATM Cash Withdrawal System — Pseudocode

## System Description
Models all the steps involved in withdrawing cash from an ATM machine.

---

```
START

PRINT "Please insert your card"
READ card

SET attempts = 0

LOOP WHILE attempts < 3:
    PRINT "Enter your PIN:"
    READ pin
    IF pin == correct_pin THEN
        BREAK out of loop
    ELSE:
        SET attempts = attempts + 1
        IF attempts < 3 THEN
            PRINT "Incorrect PIN. Attempts remaining: " + (3 - attempts)
        END IF
    END IF
END LOOP

IF attempts == 3 THEN
    PRINT "Card blocked due to 3 incorrect PIN attempts."
    Eject and block card
    END
END IF

QUERY account balance from bank system
SET balance = retrieved balance

SET another_transaction = YES

LOOP WHILE another_transaction == YES:

    PRINT "Enter withdrawal amount (multiples of 20 TL):"
    READ amount

    IF amount % 20 != 0 THEN
        PRINT "Amount must be a multiple of 20 TL. Please try again."
        CONTINUE to top of loop
    END IF

    IF amount > balance THEN
        PRINT "Insufficient balance. Available: " + balance
        CONTINUE to top of loop
    END IF

    IF amount > daily_limit THEN
        PRINT "Daily withdrawal limit exceeded. Maximum: " + daily_limit
        CONTINUE to top of loop
    END IF

    Dispense cash
    PRINT "Please collect your cash."
    PRINT receipt

    SET balance = balance - amount
    UPDATE account balance in bank system

    PRINT "Would you like to perform another transaction? (YES/NO)"
    READ another_transaction

END LOOP

PRINT "Thank you for using our ATM. Goodbye!"
Eject card

END
```
