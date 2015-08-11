# aws-sdk-js-upload-progress
This is an updated version of aws-sdk-js to enable tracking progress of each file separately while uploading concurrent files.

if you are trying to upload multiple files concurrently on amazon s3 using their sdk, while tracking progress you have to listen on "httpUploadProgress" event, but you get payload like this:

**{loaded: 147456, total: 415560925, part: 1}**

**{loaded: 180224, total: 13566183, part: 1}**

which is very confusing to know which data is for which file?

after update:
=============
we added some values to the emitted event payload in order to identify the associated file. The same event is emitted but with payload like this:

**{loaded: 147456, total: 415560925, part: 1, name: "12.mp4", key: "idOn4M86"}**

**{loaded: 180224, total: 13566183, part: 1, name: "122345.mp4", key: "ShMOAxJN"}**

now you know the first is associated with file named **12.mp4** it's key is **idOn4M86**

the second id addociated with  file named **122345.mp4** it's key is **ShMOAxJN**
