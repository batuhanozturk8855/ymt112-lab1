# Task 2: Online Shopping Cart System — Pseudocode

## System Description
Models the product browsing, cart management, and checkout process of an e-commerce website.

---

```
START

PRINT "Welcome! Please log in."
READ username, password

IF credentials valid THEN
    PRINT "Login successful. Welcome, " + username
ELSE
    PRINT "Invalid credentials. Redirecting to login page."
    END
END IF

SET cart = empty list
SET browsing = YES

LOOP WHILE browsing == YES:
    PRINT "Browse product categories:"
    PRINT "1-Electronics  2-Clothing  3-Books  4-Home  5-Go to Cart"
    READ category_choice

    IF category_choice == 5 THEN
        SET browsing = NO
    ELSE
        Display products in selected category
        PRINT "Enter product ID to add to cart (or 0 to go back):"
        READ product_id

        IF product_id != 0 THEN
            IF product stock > 0 THEN
                ADD product to cart
                PRINT "Product added to cart."
            ELSE
                PRINT "Sorry, this product is out of stock."
            END IF
        END IF
    END IF
END LOOP

SET editing = YES

LOOP WHILE editing == YES:
    PRINT "Your Cart:"
    DISPLAY cart items and subtotal
    PRINT "1-Proceed to Checkout  2-Remove Item  3-Continue Shopping"
    READ cart_action

    IF cart_action == 1 THEN
        SET editing = NO
    ELSE IF cart_action == 2 THEN
        PRINT "Enter item number to remove:"
        READ item_to_remove
        REMOVE item_to_remove from cart
    ELSE
        SET browsing = YES (go back to browsing loop)
    END IF
END LOOP

SET subtotal = calculate cart total

PRINT "Do you have a discount code? (YES/NO)"
READ has_discount

IF has_discount == YES THEN
    READ discount_code
    IF discount_code is valid THEN
        APPLY discount to subtotal
        PRINT "Discount applied! New subtotal: " + subtotal
    ELSE
        PRINT "Invalid discount code."
    END IF
END IF

IF subtotal < 10 THEN
    PRINT "Minimum order amount is $10. Please add more items."
    Go back to cart editing
END IF

IF subtotal >= 40 THEN
    SET shipping_fee = 0
    PRINT "Free shipping!"
ELSE
    SET shipping_fee = 5.99
    PRINT "Shipping fee: $" + shipping_fee
END IF

SET total = subtotal + shipping_fee

PRINT "Select payment method:"
PRINT "1-Credit Card  2-PayPal  3-Bank Transfer"
READ payment_method

IF payment_method == 1 THEN
    READ card details
    Process credit card payment
ELSE IF payment_method == 2 THEN
    Redirect to PayPal
ELSE
    Display bank transfer details
END IF

IF payment successful THEN
    PRINT "Order confirmed! Order ID: " + generate_order_id()
    PRINT "Estimated delivery: 3-5 business days"
ELSE
    PRINT "Payment failed. Please try again."
END IF

END
```
