## Intersystem Cache

### Save image to database
---
        Set stream=##class(%Stream.FileBinary).%New()
        Set sc=stream.LinkToFile("/usr/cache/dsa/clb/def/hst.jpg")
        If ($$$ISERR(sc)) Throw sc
        Set document = ##class(HSTHIS.DATA.Document).%OpenId(1)
        Do document.Image.CopyFrom(stream)
        Set sc = document.%Save()
        If ($$$ISERR(sc)) Throw sc

### Try Catch
---
        Try {
            Set sc = $$$OK
            Set sc = ...
            If ($$$ISERR(sc)) Throw sc

        }
        Catch error {

            If $$$ISERR(sc)
            {
                Do $SYSTEM.Status.DecomposeStatus(sc, .error)
                Set errorMessage = error(error)
                W "Status code error ===========================", !
                W errorMessage, !
            }
            Else
            {
                W "General error ===========================", !
                W "error code: ",error.Code,!
                W "error location: ",error.Location,!
                W "error data:",error.Data,!			
                W "error name:",error.Name,!
            }
            
        }

### Create a namespace in SMP
---
        ENSEMBLE -> System Administration -> Configuration -> System Configuration -> Namespaces

### ODBC vs ODBC35
---
When I install, there are two drivers (CacheODBC and CacheODBC35). What does this mean?

When you do the install, there are 2 drivers – CacheODBC and CacheODBC35. These support different levels of the ODBC standard. The first support version 2.5 and the second support version 3.5. The ODBC driver Manager will convert 3.5 requests to the older 2.5 automatically, so in most cases you can use either driver.

-- source: Cache Website

### OBDC Logging
---
ODBC Log
When checked, enables ODBC client driver logging. 

The log file is called CacheODBC.log. 

By default, the location of file is %PUBLIC%\Logs\, where the %PUBLIC% syntax specifies that the path is based on the PUBLIC environment variable (which is defined by default on some Windows systems). For older versions of Windows, the file is stored in either the Windows or WinNT directory. You can also specify a custom path and file using the CACHEODBCTRACEFILE environment variable.

### ERROR #6022: Gateway failed: PrepareW.
---
This might be because of a non-existant table in your SQL query, or an incorrect sql query, but could also be because of other errors.

Take the sql from your objectscript and execute it in dbvis to figure out if the query's syntax is correct or not.

To see the actual error, enable 'OBDC Logging' checkbox in the ODBC configuration.

### ERROR #6026: Gateway: Cannot allocate statement.: ,ZILLEGAL VALUE
---

The ODBC name may not have been created/configured yet.
Check the the server/pc on which the Cache server run, has a ODBC defined.

### \<UNDEFINED>^DW.Modules.Pmi.Person.1 *resultSet
---
You may have variabled set in your debugger 'watch'.

So just delete or update these watch variables.

###  Search/Find column/fields in database
---
        SELECT parent->SqlTableName 
        FROM %dictionary.compiledproperty
        WHERE SqlFieldName='Surname'

### Default values for Cache fields/properties
---

        Class Package.ClassName Extends %Persistant
        {
            Property Modified As %Library.TimeStamp [ InitialExpression = {$zdatetime($zu(188),3,1,0)} ];
        }

### Unique values  for Cache fields/properties

---

        Index ucName On Name [ Unique ];

### Get properties of classes

---

        SELECT * FROM %dictionary.<PROPERTY>
        WHERE Parent = '<PACKAGENAME>.<CLASSNAME>'
        
### Loop through / traverse a global (and its nodes)

---

The following example loops through a global and ^RIW and up to four levels ^RIW(L1,L2,L3,L4):

	// //////////////////////////
	s a=""
	f  {
		s a=$o(^RIW(a)) 
		q:a=""

		i $g(^RIW(a))'="" w ^RIW(a), !
		
		// //////////////////////////
		s b=""
		f {
			s b=$o(^RIW(a,b))
			q:b=""
			
			i $g(^RIW(a,b))'="" w ^RIW(a,b), !

			// //////////////////////////
			s c=""
			f {
				s c=$o(^RIW(a,b,c))
				q:c=""
				i $g(^RIW(a,b,c))'="" w ^RIW(a,b,c), !
				
				
				// //////////////////////////
				s d=""
				f {
					s d=$o(^RIW(a,b,c,d))
					q:d=""
					i $g(^RIW(a,b,c,d))'="" w ^RIW(a,b,c,d), !
					
				}
				
			}
		}
		
		//}
	}
	q

### String.format

---

String.format method in Cache like C#

        ClassMethod f(pString As %String, pList As %List) As %String
        {
                Set s = pString
                Set len = $LISTLENGTH(pList)
                For i=1:1:len
                {
                        Set s = $Replace(s,"{" _ (i-1) _ "}", $LIST(pList,i))
                }
                Quit s
        }

TODO: Show an exmple usuage here

### SQL-Based Development

---

It is possible to develop Caché applications using SQL-based tools, since Caché automatically creates a class definition from any relational tables defined using SQL DDL statements. **This approach does not exploit the full power of objects because you are limited by what DDL can express**; however, it is useful for migrating legacy applications.

- http://localhost:57772/csp/docbook/DocBook.UI.Page.cls?KEY=GOBJ_intro#GOBJ_intro_sqldev

### SQL: Insert where not exist

---
        INSERT INTO DW_Monthly_Admission.MfIpWardBedComplement
        (CostCentre, Ward)
        SELECT '149952', 'C12' 
        WHERE NOT EXISTS 
        (SELECT * FROM DW_Monthly_Admission.MfIpWardBedComplement WHERE Ward = 'C12');

### Checking for empty string <EMPTY> from the database 

---
        If ($ASCII(Object.Field)=0)
        {
                Set settingValue = ""
        }

### Get Current TimeStamp

---

        Write $ZDT($ZU(188),3,1,3)

### Date to/from string

---

        // ************************************************************************

        Set horologDate = $HOROLOG
        Write horologDate, !

        // ************************************************************************

        // String to date ($ZDATEH)
        S StringToConvert = "20160211"   // YYYYMMDD
        S DateFromString = $ZDATEH(StringToConvert, 8)
        W DateFromString, !

        S StringToConvert = "11/02/2016" // DD/MM/YYYY
        S DateFromString = $ZDATEH(StringToConvert, 4)
        W DateFromString, !

        // ZDATEH
        // 9	-	YYYYMMDD
        // 1	-	MM/DD/YYYY
        // 4	-	DD/MM/YYYY
        // 3    -   YYYY-MM-DD

        // ************************************************************************

        // Date to string ($ZDATE)
        S DateToConvert = $ZDATEH("11/02/2016", 4) // First make it a date
        S StringFromDate = $ZDATE(DateToConvert, 8) // Now spit it out as string
        W StringFromDate, !


        S DateToConvert = $ZDATEH("11/02/2016", 4) // First make it a date
        S StringFromDate = $ZDATE(DateToConvert, 3) // Now spit it out as string
        W StringFromDate, !

        // ZDATE
        // 3	-	YYYY-MM-DD
        // 4    -   DD/MM/YYYY
        // 8    -   YYYYMMDD
        // 1	-	MM/DD/YYYY

### Map one-to-one relationship

The table that hold the relation always en up with, (Cardinality = one)

Example 1:

One Person has always one gender. Person will hold this relation

Person:

        Relationship mfGender As DW.Masterfiles.mfGender [ Cardinality = one, Inverse = Person ];

mfGender:

        Relationship Person As DW.Modules.Pmi.Person [ Cardinality = many, Inverse = mfGender ];

Example 2:

One Patient is always only one Person. Patient table will the relation

Patient: 

        Relationship Person As Person [ Cardinality = one, Inverse = Patient ];

Person:

Relationship Patient As Patient [ Cardinality = many, Inverse = Person ];
        

### Map one-to-many relationship

This has (Person)

        Relationship PersonAddress As PersonAddress [ Cardinality = many, Inverse = Person ];

Many-Of-This (Patient)
        
        Relationship Person As Person [ Cardinality = one, Inverse = PersonAddress ];

### SQL Transaction in ObjectScript

---

        ##sql(START TRANSACTION)
        Set sc = 1
        If (sc)
        {
            ##sql(COMMIT WORK)  
        }
        Else
        {
            ##sql(ROLLBACK WORK)
        }
        
### Custom errors

        CreateCustomErrors
                SET st1 = $System.Status.Error(83,"my unique error")
                SET st2 = $System.Status.Error(5001,"my unique error")
                SET allstatus = $System.Status.AppendStatus(st1,st2)
        DisplayErrors
                WRITE "All together:",!
                WRITE $System.Status.GetErrorText(allstatus),!!
                WRITE "One by one",!
                WRITE "First error format:",!
                WRITE $System.Status.GetOneStatusText(allstatus,1),!
                WRITE "Second error format:",!
                WRITE $System.Status.GetOneStatusText(allstatus,2),!

### Exit a While loops

        While (rs.Next())
        {
                
                If(condition)
                {

                }
        }

### HttpRequest via Cache/ENSEMBLE

---

        Method SetHeader(name As %String, value As %String) As %Status

        class %Net.HttpRequest

        Method SendFormData(
                Output pHttpResponse As %Net.HttpResponse, 
                pOp As %String, pHttpRequestIn As %Net.HttpRequest, 
                pFormVarNames As %String, 
                pData...) As %Status [ CodeMode = expression ]
        {

        ..SendFormDataArray(.pHttpResponse,.pOp,.pHttpRequestIn,.pFormVarNames,.pData)
        }