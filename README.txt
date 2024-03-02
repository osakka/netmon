 Welcome to NetMon
 -----------------

 -[group record specs]------------------------------------
 type          value            unique    min. entries max
 ----          -----            ------    ------------ ---
 group         1-1024           yes       1 (key)      1
 description   string           yes       1            1
 track         string <host>    no        1            u  <- from any group
               priority 1-128   yes       1            128 (unique priority,
                                                            unique host,
                                                            multiple trackers)
 request       <request> type   no        0            u  <- applies to host
 alert         <alert> type     no        0            u  <- applies to host
 -------------------------------------------------------------
 
 -[host record specs]-----------------------------------------------------------
 type          value            unique locally unique globally  min. entries max
 ----          -----            -------------- ---------------  ------------ ---
 host          word             yes            yes               1 (key)      1
 ipa           4 8 bit base10   yes            no                1            1
 description   string           yes            no                1            1
 group         1-1024           yes            no                1            1
 request       <request> type   no             no                0            u
 alert         <alert> type     no             no                0            u
 -------------------------------------------------------------------------------


 bin/  - systems binaries including netmon 
 etc/  - current configuration files
 log/  - logs
 src/  - commands.
 tmp/  - temp directory
 var/  - collected data files

 delimited fields, with ":" as the delimiter.
 flat text file
 first item of field is field_name.

 1) get data - read data file into array called $record.
 2) get data - parse $record item specified by user into $field.

 1) list config <optional type>. (*|host|plugin)
 2) add record (type <name>).    (host)
 3) del record (type <name>).    (host|plugin)
 4) add field  (type <name> field type, field name)
 5) del field  (type <name> field type, field name)
 6) find record  (type <name>) (optional type)
