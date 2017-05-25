    SELECT
        A.SYSIPCURRDISCHARGEID,
        A.InternalPatientNumber, 
        A.EpisodeNumber,
        A.IpDschDtimeInt,
        A.SamAdtValuablesReturnedOnDicharge,
        A.MethodOfDischarge,
        A.DestinationOnDischarge,
        A.TransTo,
        A.Transport,
        A.Kilometres,
        A.DischargeWeight,  
        A.DischargeHeight,
        A.Diagnosis
    FROM
        SQLUser.SYSIPCURRDISCHARGE A