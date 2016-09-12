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

