The plugin forces browser to open a dialog for downloading content produced within controller's action. 
Although the theory says that this is easily controlled by specifying Content-Disposition HTTP header, the practice shows
that there are special situations (ofcourse) with IE that has to be handled properly.

Controllers are extended with forceDownload method that takes as parameters a Map specifying download options, 
and a object containing content:

    forceDownload(file:"file", contentType:"application/octet-stream", contentLength: 123, content)

* file specifies the name that will be presented in browser download dialog, if omitted the default value is 'file'
* contentType is MIME content type that will be sent to browser for the given content, if omitted the default value is application/octet-stream
* contentLength is optional, but recommended to have - browsers will be able to show proper progress while downloading. 
  If not explicitely specified, it can be read from content object, if it implements size() method
* content - optional. If omitted then controller's code must write to response stream or render response manually using standard Grails approaches
