# Clinicom

## Masterfiles


### Ward

    SELECT * FROM SQLUser.MFIPWARD


### Hospital

    SELECT * FROM SQLUser.MFGENHOSPDET;
    SELECT * FROM SQLUser.MFGENHOSPDETMORE;

### Ward Bed Type

    SELECT * FROM SQLUser.CLIN_EDIT_LISTS WHERE EDL_DD = 'J9786'

### Transport

    SELECT * FROM SQLUser.TRANS

### Referral Type

    SELECT * FROM SQLUser.CLIN_EDIT_LISTS WHERE EDL_DD = 'C0196'

### Admission Method

    SELECT * FROM SQLUser.MFIPMETHOFADMISSION

### Accident Type

    SELECT * FROM SQLUser.CLIN_EDIT_LISTS WHERE EDL_DD = 'A0358'

### Admission Source

    SELECT * FROM SQLUser.MFIPADMSOURCE

### Consultant

    SELECT * FROM SQLUser.MFGENCONSULTANT

### Specialty

    SELECT * FROM SQLUser.SPEC
    SELECT * FROM SQLUser.CONSPEC

###  Category

    SELECT * FROM PATCAT 

### Transport

SELECT * FROM TRANS

### Folder / Casenote

CASENOTEDETS

### ADMISSION PREADMISSION REFERRAL CODE - Admission ReferralType

C0196.DD

### Admission Method

MFIPMETHOFADMISSION

### Accident Type

A0358.DD

### Admission Source

MFIPADMSOURCE 

### Intended Management

INMAN

### Operating Room / Operating Theatre

MFGENOPERROOM 

### Diet

MFGENDIET