# OS_Codeset
CS F372 coursework projects and assignments 

# Assignment 1

# Hotel_Management_System

This Hotel Management System is designed to streamline and automate various operations involved in running a hotel. It includes modules for managing tables, customers, orders, and billing. The system consists of the following key components:

## Table Management (table.c)

This module manages the tables in the hotel. Each table can have multiple customers associated with it, making customers the child entities of tables.

Customers are created as child processes within this module.

Functions include adding/removing tables, assigning customers to tables, and maintaining the status of each table (occupied, vacant, etc.).

## Order Management (waiter.c)

Waiters use this module to take orders from customers and send them to the kitchen or relevant departments.

Functions include taking new orders, modifying existing orders, and sending order details to the manager for billing.

## Hotel Manager (hotelmanager.c)

The manager is responsible for compiling and generating bills based on the orders received from the waiters.

Functions include calculating total costs, applying discounts or promotions, generating invoices, and managing overall financial records.

## Cleanup and Shutdown (admin.c)

This module is responsible for closing the hotel operations for the day. It ensures that all data is properly saved and the system is safely shut down.

Functions include finalizing pending transactions, backing up data, and releasing resources used during the day.

## Detailed Component Interactions

### table.c:

Manages table creation and deletion.

Creates customer processes as children and links them to specific tables.

Handles customer check-ins and check-outs, updating the status of tables accordingly.

### waiter.c:

Takes orders from customers seated at tables.

Sends order information to hotelmanager.c for processing and billing.

### hotelmanager.c:

Receives orders from waiter.c.

Compiles bills and processes payments.

Maintains financial records and generates daily reports.

### admin.c:

Finalizes the day's operations.

Ensures all data is saved.

Safely shuts down the system.

## Workflow Overview

Check-in: Customers check in and are assigned to tables via table.c. Customers are created as child processes.

Order Taking: Waiters take orders using waiter.c and forward them to hotelmanager.c.

Billing: The manager compiles bills based on orders using hotelmanager.c.

Check-out: Customers check out, and their data is updated in table.c.

Daily Cleanup: At the end of the day, admin.c ensures all operations are finalized and the system is shut down safely.

This modular approach ensures a well-organized and efficient management of hotel operations, enhancing both customer service and operational efficiency.


***
# Assignment 2

# Flight_Simulator

This Flight Simulator is designed to simulate and manage the operations of airports, planes, and air traffic control. It includes modules for managing airports, planes, air traffic control, and system cleanup. The system consists of the following key components:

## Airport Management (airport.c)

This module represents an airport, where each runway is managed as a separate thread. The threads handle takeoffs and landings concurrently to simulate a realistic airport environment.

### Functions:

Initialize Airport: Functions to initialize the airport and its runways.

Runway Thread Management: Functions to create and manage threads for each runway.

Handle Flights: Functions to manage incoming and outgoing flights using runway threads.

Thread Synchronization: Functions to ensure thread safety and prevent race conditions and deadlocks.

## Plane Management (plane.c)

This module represents an airplane, which could either be a passenger plane or a cargo plane. Each passenger plane has child processes representing the passengers, while cargo planes do not require child processes.

### Functions:

Initialize Plane: Functions to initialize the plane, including type (passenger or cargo) and other attributes.

Manage Passenger Processes: For passenger planes, functions to create and manage child processes for each passenger.

Cargo Operations: For cargo planes, functions to handle cargo-related operations without additional processes.

Communication with Airport: Functions for planes to request takeoff and landing from airports.

## Air Traffic Controller (airtrafficcontroller.c)

This module acts as the air traffic controller, directing planes to their respective airports and managing airspace coordination.

### Functions:

Monitor Air Traffic: Functions to monitor and manage air traffic to ensure safe distances between planes.

Guide Planes: Functions to guide planes to their designated runways at specific airports.

Coordinate Sequences: Functions to coordinate takeoff and landing sequences to optimize airport efficiency.

Emergency Handling: Functions to handle emergency situations and rerouting if necessary.

## Cleanup and Shutdown (cleanup.c)

This module is responsible for shutting down the flight simulation, closing all airports, and ensuring all resources are properly released.

## #Functions:

Terminate Processes: Functions to signal all active threads and processes to terminate.

Close Runways: Functions to ensure all runways (threads) are properly closed and joined.

Resource Release: Functions to release any resources allocated during the simulation.

## Detailed Component Interactions

### airport.c:

Manages Runway Threads: Creates and manages threads for each runway.

Handles Flight Operations: Manages takeoffs and landings concurrently.

Synchronizes Threads: Ensures thread safety and prevents race conditions.

### plane.c:

Initializes Planes: Sets up planes as either passenger or cargo types.

Manages Passenger Processes: Creates child processes for passengers in passenger planes.

Handles Cargo Operations: Manages cargo operations without additional processes.

### airtrafficcontroller.c:

Monitors and Manages Air Traffic: Ensures safe distances and coordinates flight sequences.

Guides Planes to Airports: Directs planes to their designated runways.

### cleanup.c:

Finalizes Simulation: Ensures all operations are finalized and all resources are released.

Shuts Down System Safely: Closes runways and terminates processes properly.

## Workflow Overview

Initialization: Airports and runways are initialized via airport.c. Planes are set up using plane.c.

Flight Operations: Planes request takeoff and landing through airport.c and are guided by airtrafficcontroller.c.

Air Traffic Management: airtrafficcontroller.c monitors and directs air traffic to ensure safety and efficiency.

Simulation Shutdown: At the end of the simulation, cleanup.c ensures all operations are finalized and the system is safely shut down.

This modular approach ensures a well-organized and efficient simulation of airport and air traffic operations, enhancing both operational realism and safety.
