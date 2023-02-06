# mdt-authorities
authorities list for DHARMA metadata 

CSV folder = stores the csv files for authorities: collections, monuments, personns and places downloaded from googleSheets. 
temporary = temporary files for each authorities, to check if necessary. generated from xslts stored in project-documentation/stylesheets/mdt_inscriptions/
output = html files for temporary display in erc-dharùa.giothub.io . Made with xslt stored in project-documentatation/Stylesheets/mdt-authorities/

build_to_display.xml = launch  transformations from xml to html using xslts (see project-documentatation/Stylesheets/mdt-authorities/). one specific task in java ant per authorithy.
clone-projectDoc.xml = clone project-documentation for github action.

.github/workflows
1- run csvtoxml.yml on push, one java line per authority using xslt stored in project-documentation/stylesheets/mdt_inscriptions/ to process. (files mdtCollection_start.xml,mdtMonument_start.xml, mdtPerson_start.xml and mdtPlace_start.xml) resulting files stored into temporary 
2- run commacleaning.yml on finishing csvtoxml.yml task one java line per authority using project-documentation/stylesheets/mdt_inscriptions/mdt_CommaCleaning.xsl resulting files stored into temporary 
3- run xmltodisplay.yml on finishing commacleaning.yml task, launch the two ant tasks clone-projectDoc.xml then build_to_display.xml. 