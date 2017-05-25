    SELECT 
        CLINIPREINSTATEMENTSID, 
        InternalPatientNumber, 
        EpisodeNumber, 
        EpsActvDtimeInt, 
        IpSuspStartDtimeInt, 
        IpSuspReturnDtimeInt, 
        HospitalNumber, 
        Ward, 
        Consultant, 
        Specialty, 
        Category, 
        Room, 
        AdtRbtOutlierReinstateInt, 
        Outlier, 
        Bed, 
        SigFacility 
    FROM 
        SQLUser.CLINIPREINSTATEMENTS 
    WHERE
        InternalPatientNumber = {0}
    AND 
        EpisodeNumber = {1} 
    AND 
        EpsActvDtimeInt = '{2}'