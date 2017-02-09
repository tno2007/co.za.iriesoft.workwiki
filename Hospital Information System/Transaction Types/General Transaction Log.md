# 

## GENERAL TRANSACTION LOG TRANSACTION TYPE

### Data Definition

    H0120.DD

### Global

    ^ADTL

### Mapped Sql

    SELECT
            EDL_Key,
            EDL_Description,
            EDL_Internal_Value
    FROM
            SQLUser.CLIN_EDIT_LISTS
    WHERE
            EDL_DD = 'H0120'

### Listing

    Key                 Code    Description
    A & E ATTENDANCE    33     A & E Attendance
    ACP ACTIVITY        70     Augmented Care Period Activity has been recorded
    ACP REMINDER        71     Augmented Care Period Reminder has been recorded
    AD                  7      Admission
    AD DSCH             11     Discharge
    AD REINST           9      Admission Reinstate
    AD SUSP             8      Admission Suspend
    AD XFER             10     Transfer
    CANCER REG          56     Cancer Registration
    CMM UPD             55     Contract Id Change
    EXP DISCHARGE       14     Expected Discharge
    EXP WARD XFER       13     Expected Ward Transfer
    IP APPT ATTENDANCE  82     Inpatient Appointment Attendance
    IP APPT BOOKING     80     Inpatient Appointment Booking
    IP APPT CANCEL      84     Inpatient Appointment Cancellation
    MF UPD              50     Masterfile Update
    MRA DEL CD          37     Medical Record Abstract Delivery
    MRA DX CD           35     Medical Record Diagnosis Coding
    MRA OP CD           36     Medical Record Operation Coding
    NHS NUMBER          47     NHS Number
    OP EP REG           60     Outpatient Episodic Registration
    PMI ADDRESS         44     PMI Address Details Maintenance
    PMI LINK            43     Link between patients (Parent-Child)
    PMI MERGE ADD       42     Addition by Patient Merge
    PMI MERGE DEL       41     Deletion by Patient Merge
    PMI REVISE          40     PMI Revision
    PMI TREATMENT       49     PMI Treatment Episode
    PREADM              5      Preadmission Active
    PREADM CANC         6      Pre Admission Cancelled
    PSY ECT             46     Record ECT Treatment
    PSY LS/MC           45     Change in Legal Status or Mental Category
    RAD ATTENDANCE      31     Radiology Attendance
    WARD ATTENDER       34     Ward Attender Episode
    WARD ATTENDER DIAG  39     Ward Attender Diagnosis
    WARD ATTENDER PROC  38     Ward Attender Procedures
    WL ACTIVE           1      Waiting List Active
    WL CANCEL           4      Waiting List Cancel
    WL DEFER            18     Waiting List Defer
    WL EXP SUSP         15     Waiting List Expected Suspend
    WL REINSTATE        3      Waiting List Reinstate
    WL SUSPEND          2      Waiting List Suspend
    WL TRANS            19     Waiting List Transfer
