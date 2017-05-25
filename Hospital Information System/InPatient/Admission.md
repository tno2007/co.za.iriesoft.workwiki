    SELECT
        A.InternalPatientNumber,
        A.EpisodeNumber,
        A.IpAdmDtimeInt,
        A.AdmWard,
        A.CaseNoteNumber,
        A.Referral,
        A.AdmReason,
        A.MethodOfAdmission,
        A.AccidentCode,
        A.TransFrom,
        A.Lodger,
        A.LivestillBirth,
        A.Consultant,
        A.Specialty,
        A.JointCons,
        A.JointSpec,
        A.IntdMgmt,
        A.Category,
        A.Operation,
        A.COMMENT,
        A.ExpectedLos,
        A.TheatreTime,
        A.HospCode,
        B.Transport,
        B.Kilometres,
        B.ValIndemn,
        B.FmsReceiptNo,
        B.ValReceiptNo,
        B.AdtAdmissionDateInPrevStateHospital,
        B.AdtDischargeDateInPrevStateHospital,
        B.BirthWeightInGrams,
        B.Registrar,
        B.AdtInternFreeText,
        B.KitBookNumber,
        B.OperatingRoom,
        B.DietaryCode,
        C.ChronicallySickOrDisabledIndicatorInternal,
        C.OperationDate_1
    FROM
        SQLUser.CLINIPADMITDISCH A
    JOIN
        SQLUser.CLINBARADMFIN B
    ON
        A.InternalPatientNumber = B.InternalPatientNumber
    AND
        A.EpisodeNumber = B.EpisodeNumber
    AND
        A.IpAdmDtimeInt = B.EpsActvDtimeInt
    JOIN
        SQLUser.SYSIPWAITLIST C
    ON
        B.InternalPatientNumber = C.InternalPatientNumber
    AND
        B.EpisodeNumber = C.EpisodeNumber