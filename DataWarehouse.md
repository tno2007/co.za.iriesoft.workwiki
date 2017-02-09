# Update

## Agenda

1. Since last time
2. Current developments
3. Currently happening

## 1. Since last time

---

Since last meeting we decided on:

### 1.1 Schema:

PMI tables
- Person
- Patient
- Debtor

Masterfiles
 - Country
 - Gender
 - EthnicGroup
 - Province
 - Country
 - Religion


## 1.2 Schema Findings:

---

Beacuse Patient have only 4 fields
- InternalNo
- ExternalNo
- Carer flag
- Clinicom comments

We are trying to make querying fast and use less joins. 
So we added this to Person table.

If you want to know whether this is a Patient... The InternalNo will be populated.

This leaves us with 2 tables:

 - Person
 - Debtor

So how do we know if a Person is a Debtor... His/Her DebtorNo will be populated. 
 
## 1.3 Use ansi SQL for data warehouse:

---

This investigation... see whether its possible to 
use sql for DW.


## 1.4 Findings

---

- SQL wont work as the sql relationship does not show up in DeepSee.
- Ran the sql script...
- Proceed to build cubes from data and the relationships did not come up
- Cache uses its own internal ID, even if you specify a field called ID.
  Cache will just create a column called ID1

### Therefore we decided to use Cache classes
- We will keep a SQL script on the side
- Just from all the working with this project, my opinion is, 
  Cache was designed to use object as data (Object database)
- I think therefore using sql is not directly supported by DeepSee.
- On the positive side... Use Programming against your object rather 
  using DDL (Data Definition Language).
- However we can still use SQL against our data

##  Option 1 Schema:

---

 - Person, Patient, Debtor

## Option 2 Schema

---

 - Person, Debtor

## 2. Current developments

---

- The feed program is pulling data from FOCUS, as we speak.
- We running the program in 1 minute intervals.
- Once the Once-Off-Import is complete, the program will automatically 
  sync PMI data from LIVE

 
## Suggested Synonoms

---

## Specialty / Discipline
## Episode / Visit / Encounter
## 