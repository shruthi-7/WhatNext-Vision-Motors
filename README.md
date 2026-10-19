# WhatNext-Vision-Motors
Salesforce CRM implementation for WhatNext Vision Motors including automated dealer assignment, test drive reminders, stock validation triggers, and scheduled batch jobs.
# WhatNext Vision Motors - Salesforce CRM Implementation

## Overview
WhatNext Vision Motors streamlines end-to-end automotive mobility operations using Salesforce CRM. This implementation includes automated dealer assignment, scheduled customer reminders, real-time stock validation, and batch synchronization.

## Architecture & Data Model
- **Vehicle__c**: Manages vehicle inventory, models, pricing, and live stock quantity.
- **Vehicle_Dealer__c**: Captures authorized dealer locations, contact details, and servicing capabilities.
- **Vehicle_Customer__c**: Manages customer profiles, delivery addresses, and vehicle preferences.
- **Vehicle_Order__c**: Handles order placement, status workflows (Pending/Confirmed), and dealer fulfillment.
- **Vehicle_Test_Drive__c**: Tracks test drive bookings and scheduled dates.
- **Vehicle_Service_Request__c**: Manages post-sales maintenance and issue logs.

## Automations
1. **Auto Assign Dealer (Record-Triggered Flow)**: Evaluates customer address attributes upon order creation to dynamically link the nearest dealer record.
2. **Test Drive Reminder (Scheduled Flow)**: Executes 1 day before the scheduled test drive date to send automated confirmation emails to customers.
3. **VehicleOrderTrigger & Handler (Apex)**: Validates inventory before order insertion to prevent out-of-stock purchases and automatically decrements stock count when an order is confirmed.
4. **VehicleOrderBatch & Scheduler (Async Apex)**: Scans pending orders daily at 12:00 PM and confirms orders as inventory replenishes.
