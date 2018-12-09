An URI file has the following structure:

 - Every line contains URIs pointing to a single source
 - URIs pointing to the same source are separated by a space
 
 >**Example**: 
 > This is a valid URI file
 >~~~~
 >http://mirror1.site.com/file.zip http://mirror2.site.com/file.zip http://mirror3.site.com/file.zip
 >http://site2.com/other_file.zip
 >https://site3.com/nice_secure_file.zip
 >~~~~
 >
 > This is an ***invalid*** URI file
 >~~~~
 >http://mirror1.site.com/file.zip http://site2.com/other_file.zip https://site3.com/nice_secure_file.zip
 >http://mirror2.site.com/file.zip http://site3.com/other_file.zip 
 >~~~~
 
 Remember that if you mix URIs pointing to different resources, then the download may fail or be corrupted without aria2 complaining.
 
 >**Note**: when adding BitTorrent Magnet URIs, every line must contains ***only one*** URI