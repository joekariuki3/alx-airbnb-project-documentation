# Property Booking Flowchart

This document explains the flowchart steps for the property booking process in the Airbnb Clone backend system. The flowchart visually represents how a user books a property, from searching to payment and confirmation.

---

## Flowchart Steps

1. **Start**
   The booking process begins.

2. **User searches for property**
   The user browses available properties based on their preferences.

3. **User selects property and date**
   The user chooses a specific property and desired booking dates.

4. **Check availability?**
   The system checks if the property is available for the selected dates.

   - **If No:** The user is notified of unavailability, and the process ends.
   - **If Yes:** The process continues.

5. **Confirm booking and save to DB**
   The booking is confirmed and stored in the database.

6. **Redirect to payment gateway**
   The user is redirected to a secure payment gateway.

7. **Process payment**
   The system processes the user's payment.

8. **Send confirmation to user**
   After successful payment, a booking confirmation is sent to the user.

9. **End**
   The booking process is complete.

---

For a visual representation, refer to the included flowchart image:
`flowcharts/data-flow-diagram.png`
