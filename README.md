# OrcaTag
OrcaTag is a tool that can be used to analyze pictures of orcas, with the aim to recognize and track individual animals.

## Background

The Norwegian Orca Survey (NOS) has over many years collected photographs of orcas (killer whales) from several locations along the norwegian coast. To learn more about the animals it is important to identify individual animals. NOS has been doing this for a while and as of today close to 900 indiviual orcas has been identified and assigned a unique ID.
An indiviual orca can uniquely be identified by nicks in its dorsal fin, combined with scars and scratches on its saddle patch (https://www.norwegianorca-id.no/key).

NOS has a growing collection of photographs (approx 100 000 per august 2017) and wants to engage with a network of specialists to help go through the pictures and tag individual orcas so that they can be identified. 

OrcaTag will be a tool that can be used by the specialists to do this work.

References: 

* The Norwegian Orca Survey, https://www.norwegianorcasurvey.no
* The Norwegian Orca-ID Catalogue, https://www.norwegianorca-id.no

## OrcaTag modules

OrcaTag will consist of several parts: 

* a picture load facility to batch-import pictures
* a database where metadata would be stored
* a search engine to help match new pictures with already identified animals
* a web-application / dashboard to use when processing a picture, tagging the orcas in the pictures, etc
* an export faciltity that can be used to export data in a format suitable for import into other tools, such as Excel

### Loading pictures into OrcaTag

In the first version of OrcaTag, a command line utility will be provided to load pictures into the database. An observer would first copy pictures from her camera memory card into a folder on her computer and then run the ultility with a set of arguments to import the pictures. The load facility would perform several steps for each picture: 

1. relevant metadata items from the picture EXIF data will be extraced and stored in the database
1. if the picture is not geotagged and the user has supplied geographical coordinates on the command line, the coordinates (in decimal latitude/longitude) will be added to the database
1. based on the original picture, lower resolution versions will be generated: e.g. thumbnail, medium, large
1. the pictures (in all resolutions) will be stored in a long term storage facility, e g AWS S3.

Given a subfolder named "20170829_\andenes" the ultility would be used in a manner similiar to this: 

    % orcatag_load -area "andenes" -lat 69.36 -long 16.04 20170829_\andenes
    will process 134 pictures in folder 20170829_\andenes...
    Done!





