## Intersystem Cache

### Save image to database

        Set stream=##class(%Stream.FileBinary).%New()
        Set sc=stream.LinkToFile("/usr/cache/dsa/clb/def/hst.jpg")
        If ($$$ISERR(sc)) Throw sc
        Set document = ##class(HSTHIS.DATA.Document).%OpenId(1)
        Do document.Image.CopyFrom(stream)
        Set sc = document.%Save()
        If ($$$ISERR(sc)) Throw sc

### Try Catch

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

        ENSEMBLE -> System Administration -> System Configuration -> Namespaces

### ODBC vs ODBC35

When I install, there are two drivers (CacheODBC and CacheODBC35). What does this mean?

When you do the install, there are 2 drivers – CacheODBC and CacheODBC35. These support different levels of the ODBC standard. The first support version 2.5 and the second support version 3.5. The ODBC driver Manager will convert 3.5 requests to the older 2.5 automatically, so in most cases you can use either driver.

-- source: Cache Website

### OBDC Logging

ODBC Log
When checked, enables ODBC client driver logging. 

The log file is called CacheODBC.log. 

By default, the location of file is %PUBLIC%\Logs\, where the %PUBLIC% syntax specifies that the path is based on the PUBLIC environment variable (which is defined by default on some Windows systems). For older versions of Windows, the file is stored in either the Windows or WinNT directory. You can also specify a custom path and file using the CACHEODBCTRACEFILE environment variable.

### ERROR #6022: Gateway failed: PrepareW.

This might be because of a non-existant table in your SQL query, but could also be because of other errors.

To see the actual error, enable 'OBDC Logging' checkbox in the ODBC configuration.

