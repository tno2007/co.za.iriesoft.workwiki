	SELECT
	    CLINIPSUSPENSIONSID,
	    InternalPatientNumber,
	    EpisodeNumber,
	    EpsActvDtimeInt,
	    Reason,
	    IpSuspExpReturnDtimeInt,
	    SuspAdmRemark,
	    SuspAdmPrevEventDtimeInt,
	    SuspAdmPrevActvInt,
	    IpSuspStartDtimeInt,
	    HospitalNumber,
	    Ward,
	    Consultant,
	    Specialty,
	    Category,
	    Reason_1 AS ReasonCode,
	    IpSuspReasonEcho,
	    SuspendRoomCode,
	    AdtRbtOutlierSuspendInt,
	    Outlier,
	    Bed,
	    SigFacility,
	    IpSuspensionScottishReasonDescription
	 FROM
	        SQLUser.CLINIPSUSPENSIONS
	 WHERE
	        InternalPatientNumber = 
	AND
			EpisodeNumber = 
	AND
			EpsActvDtimeInt = 