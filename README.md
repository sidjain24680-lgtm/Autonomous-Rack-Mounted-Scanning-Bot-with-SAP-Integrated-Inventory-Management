# Autonomous-Rack-Mounted-Scanning-Bot-with-SAP-Integrated-Inventory-Management
# Abstract

This project features a rack-mounted autonomous scanning bot designed for multi level ware-
house automation. The system moves horizontally and vertically using a rack and pinion mech-
anism along with a dual pinion vertical climbing structure. In addition to its mechanical move-
ment, the system connects with SAP to provide real time inventory updates. Each scanned
barcode refreshes stock levels in SAP, and if inventory drops below set safety limits, the system
can automatically trigger Purchase Requisitions through SAP Material Requirement Planning
(MRP). This changes the system from a simple scanner into a smart supply chain automation
solution.

# Introduction and Industrial Relevance

Modern warehouses work within ERP driven systems. Here, inventory accuracy directly affects
procurement, production planning, and financial forecasting. Even with ERP in place, many
facilities still rely on manual stock checks and slow data entry.
The main goals of this project are:

- Autonomous mechanical traversal across multi level racks.
- Real time SAP inventory updating without manual intervention.
- Automatic MRP based purchase triggering when stock reaches reorder limits.
This system bridges the physical warehouse layer and the digital ERP layer, ensuring syn-
chronized and proactive inventory management.

# Product Description

The Autonomous Rack Mounted Scanning Bot product has two main parts: the Main Driver Box
and the Detachable Scanning Device. They work together to move around and sync inventory
with SAP ERP.

## Main Driver Box (Motion Unit)

The Main Driver Box is the mechanical center of the system. It contains the horizontal rack and
pinion drive, the dual pinion vertical climbing mechanism, motors, gearbox, control electronics,
and the main power system.
Its primary functions are:


- Horizontal movement across rack levels.
- Vertical climbing between shelves.
- Maintaining mechanical stability using gantry rollers.
- Controlling motion sequencing through the microcontroller.
- Ensuring uninterrupted scanning coverage for accurate SAP stock updates.
The Driver Box enables complete rack traversal, ensuring that all products are scanned and
synchronized with the SAP inventory database.

## Detachable Scanning Device

The Scanning Device is mounted on the Driver Box, but it can also work independently. It has a
camera module (ESP32 CAM), a local processor, and a small battery. This allows it to function
even after being detached from the main box.
Its primary functions are:

- Capturing barcode or QR code data.
- Identifying material codes and storage location.
- Transmitting stock information to SAP ERP.
- Triggering MRP logic if inventory falls below reorder limits.
After each scan, the device updates stock quantities in SAP. If the updated stock is below
the defined safety threshold, SAP MRP automatically generates a Purchase Requisition.
The separation of motion and scanning functions ensures modularity, easy maintenance, and
scalable deployment in ERP driven warehouse environments.

# System Architecture Overview

The system is divided into two synchronized layers:

## 1. Mechanical Motion Layer

This layer ensures full rack traversal :

- Horizontal rack-and-pinion drive
- Cut rail vertical transition
- Dual-pinion climbing mechanism
- Gantry stabilization system


## 2. Digital ERP Integration Layer

This layer ensures intelligent inventory management through:

- Barcode and QR code scanning
- Wireless communication to local server
- SAP database synchronization
- Automatic MRP purchase requisition generation
The mechanical layer ensures complete physical coverage, while the digital layer ensures com-
plete ERP accuracy.

# Mechanical Design and Motion Architecture

## Horizontal Motion (X-Axis)

The horizontal system uses a spur rack that is mounted along aluminum extrusion rails. A
motor driven pinion changes rotational motion into linear movement.
The 4 x V slot gantry system ensures:

- Load balancing
- Reduced vibration
- Precise alignment for scanning
- Minimal backlash
Proper mechanical positioning directly affects scanning reliability. This is essential for accu-
rate SAP stock updates.

## Vertical Motion and Cut Rail Mechanism

At the end of each horizontal rail, a cut rail section with linear guides enables vertical lifting.
The cut rail moves along linear rods to keep structural stability.
Once a shelf is fully scanned and stock is updated in SAP, the bot moves vertically to the
next level and repeats the scanning process.

# Dual-Pinion Vertical Drive Mechanism

The original single pinion system faced mechanical limits because of side dependency. To fix
this issue, two identical pinions are placed on one gearbox shaft.
Working principle:


- Both pinions rotate simultaneously.
- Only the aligned pinion engages the rack.
- The other rotates freely.
This design eliminates additional motors and simplifies control logic while maintaining me-
chanical robustness.

# Components and Electronics used

## Mechanical Materials

Aluminium Extrusion (2040) – Used as horizontal rails and structural frame.
Spur Rack (Module 1) – Provides linear motion for rack and pinion horizontal traversal.
Steel Pinion Gears (20 Tooth) – Converts motor rotation into linear displacement.
Linear Rods – Guides vertical motion of the cut rail during climbing.
Linear Bearings – Ensures smooth and low friction vertical movement.
V-Slot Rollers – Maintains gantry alignment and reduces vibration during motion.

## Mechanical Components

NEMA 17 Stepper Motor – Drives horizontal rack traversal.
Geared DC Motor – Provides required torque for vertical climbing.
Gearbox – Increases torque output for reliable load lifting.
Cut-Rail – Enables transition between horizontal levels.
Dual Pinion Shaft Assembly – Eliminates side dependency in vertical climbing.

## Electronics

ESP32-CAM – Captures barcode data and processes inventory information.
ESP32 Controller – Controls motion sequencing and communication logic.
Motor Driver – Controls stepper motor speed and direction.
Limit Switches – Detects end of rail and vertical alignment positions.
Hall / TOF Sensors – Provides positional verification.
12V Lithium-Ion Battery – Powers motion system.
3.7V LiPo Battery – Powers detachable scanning module.


# SAP Integration Architecture

## Scanning Module

The detachable scanning module captures:

- Material ID
- Storage location
- Quantity
- Timestamp
This data is processed locally before transmission.

## SAP Communication Workflow

The system communicates with SAP using one of the following methods:

- REST API middleware
- SAP OData services
- RFC connection via local server
Data Flow:
1. Barcode scanned.
2. Product matched with SAP Material Master.
3. Stock updated in SAP MM module.
4. System checks reorder point.
5. If below threshold, SAP MRP generates Purchase Requisition.

## MRP Trigger Logic

The following SAP parameters are evaluated:

- Minimum stock level
- Safety stock
- Reorder point
- Lead time
If the updated stock is below set limits, SAP automatically creates procurement proposals.
This lowers the risk of running out of stock and keeps production going.


# Autonomous Operational Cycle

The system operates in the following sequence:

1. Initialize and connect to SAP server.
2. Scan bottom-level products.
3. Update SAP inventory.
4. Move horizontally.
5. At rail end, initiate vertical climb.
6. Continue scanning next level.
7. Confirm full rack synchronization.
Thus, mechanical traversal and ERP synchronization operate simultaneously and continu-
ously.

# Industrial Advantages

- Eliminates manual stock entry errors.
- Real time ERP accuracy.
- Automatic MRP based procurement triggering.
- Reduced inventory holding uncertainty.
- Improved supply chain responsiveness.
- Compact mechanical integration in existing racks.
This makes the system highly suitable for SAP driven manufacturing plants, spare parts
warehouses, and automated distribution centers.

# Future Scope

- Direct SAP S/4HANA integration.
- Integration with SAP MM and PP modules.
- Predictive inventory analytics.
- AI based object detection.
- Multi bot warehouse coordination.


# Conclusion

The Autonomous Rack Mounted Scanning Bot combines mechanical automation with ERP
intelligence. It integrates rack traversal, dual pinion climbing, and SAP MRP synchronization.
This setup provides ongoing stock visibility and starts the procurement process automatically.
The design improves warehouse efficiency, lowers the risk of stock outages, and supports data
driven supply chain management.

