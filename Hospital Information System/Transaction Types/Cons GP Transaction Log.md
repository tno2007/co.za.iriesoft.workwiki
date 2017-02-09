# 

## CONS/GP TRANSACTION LOG TRANSACTION TYPE 

### Data Definition

    A6852.DD

### Global

    ^CGTL

### Mapped Sql

    SELECT
            EDL_Key,
            EDL_Description,
            EDL_Internal_Value
    FROM
            SQLUser.CLIN_EDIT_LISTS
    WHERE
            EDL_DD = 'A6852'

### Listing

    Key    Code    Description
    80            Direct Consultant Referral Attendance
    81            GP (Community) Attendance