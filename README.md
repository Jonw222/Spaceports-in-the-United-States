# SPACEPORTS IN THE UNITED STATES
 This repository contains images, index.html files, a readme file, and other data detailing information about US Spaceports as well as community centers in Florida, US.
 
 ## Data Source Information
- Spaceport Data from the US Federal Aviation Administration (https://www.faa.gov/space/spaceports_by_state) and Wikipedia for information about Spaceport Camden in Georgia, USA (https://en.wikipedia.org/wiki/Spaceport_Camden)
- US Spacesport Latitude and Longitude Information from Google Maps (https://www.google.com/maps/@38.0093584,-84.5117312,15z?entry=ttu&g_ep=EgoyMDI0MTAxNi4wIKXMDSoASAFQAw%3D%3D) 
- Country, state, rivers, lake, and ocean data from Natural Earth (https://www.naturalearthdata.com/)
- See Spaceport CSV data under 'data' in this repository for complete spaceport data

 ### Why I Created the Map
I research space exploration, focusing on the complex and multifaceted issue of space-related threats and their impacts on human societies. Specifically, I intend to investigate the contamination of rocket fuel residues and their environmental impact near space landing facilities, focusing on the soil around these areas in the United States. Thus, I created a map of spaceports in the US to visualize all US spaceports in a map, as well as community centers in Florida, where I intend to conduct focus group discussions to have an idea of where they are located. The map gives me a headstart on my fieldwork beginning in the Winter of 2024.

 #### Map Creation Process
- Step 1: I opened a blank excel file and manually inputed data on US spaceports derived from the US Federal Aviation Admnistration, Wikipedia, and Google Maps.
![alt text](<Screenshot 2024-10-20 231024.jpg>)
- Step 2: I saved the excel file as a CSV UTF-8 (Comma Delimited) (*.csv) file in my local computer ![alt text](<Screenshot 2024-10-20 231453.jpg>)
- Step 3: I opened a new project on QGIS, clicked the 'layer' pane on the top left corner of the dashboard - Add layer - Add delimited Layer. In the file name, I included the CSV file from my local computer. Under Geometry Definition - Point Coordinates - I used Longitude as the X field and Latitude in the Y field, with EPSG: 4326 - WGS 84 as the CRS. Then, clicked add for the layer to be visible. ![alt text](<Screenshot 2024-10-20 232454.jpg>)
- Step 4: To symbolize the CSV spaceport layer, I right clicked on the layer - properties - symbology - categorized - for the value, I selected 'ownership type' from the attribute table - for color ramp, I selected 'random colors' to differentiate the type. I also selected the 'airplane' symbol to represent launches or landings in the spaceports. ![alt text](<Screenshot 2024-10-20 233351.jpg>)
- Step 5: Then, I clicked the 'layer' pane again - Add vector data, and added country, state, rivers, lake, and ocean data from Natural Earth I already downloaded in my local computer. I also symbolized the features using a single symbol. To activate the state labels, I right-clicked on the state layer - properties - labels - for value, I used name, - chose a color, style, size, opacity and font - and then clicked apply. ![alt text](<Screenshot 2024-10-20 235037.jpg>) At this step, I completed creating the US_Spaceport Map. ![alt text](<Screenshot 2024-10-20 234155.jpg>)
- Step 6: However, since I intend to conduct Focus Group Discussions in community centers in Florida to understand community members perceptions about space exploration and its risks and benefits, I was also interested in knowing community centers within a 1 mile radius of any of the Florida Spaceports. To achieve this, I used geoprocessing tools. 
     - Adding Community Centers in Florida Layer by using QGIS to extract the data: Installed the QuickOSM plugin by going to Plugins > Manage and Install Plugins, then searched for 'QuickOSM' and installed it - Opened the QuickOSM panel (Vector > QuickOSM > QuickOSM) - Set the Key to amenity and the Value to community centers - clicked Run Query to download the community centers data directly into my QGIS project.
     - Ensured community centers layer was the same CRS as the CSV_Spaceport layer (EPSG: 4326 - WGS 84). Since, the EPSG: 4326 - WGS 84 was in degrees, I changed CRS of both layers to EPSG: 5070 - NAD 83 that allowed projection in miles to use the Buffer tool by right clicking on each layer - export - save feature as - see image below for more details... ![alt text](<Screenshot 2024-10-21 001134.jpg>)
     - Went to the menu bar and selected Vector > Geoprocessing Tools > Buffer. To configure Buffer Setting I clicked Input Layer: Selected spaceports layer - Distance: Entered 1 mile - Segments: 20 for smoothness - did not check the dissolve result box - chose an output file location for the buffered layer - clicked Run.
     - Once the buffer operation completed, a new layer was added to my map, representing the 1-mile buffer around the spaceports. ![alt text](<Screenshot 2024-10-21 001740.jpg>)
     - To check for community centers within the spaceports buffer, went to the menu bar and selected Vector > Research Tools > Select by Location - Select Features From: chose the community center layer - by Comparing to the Features From: chose the buffer spaceport layer I just created - selected intersect to find community centers within the buffer zone - clicked Run. ![alt text](<Screenshot 2024-10-21 002303.jpg>)
     - Nothing was selected meaning there are no community centers within the spaceports buffer zone.

##### Active link to the final index.html page

###### CRS Information
I started the project with EPSG: 4326 - WGS 84. Since, the EPSG: 4326 - WGS 84 projection was in degrees, I changed the CRS of the CSV Spaceport and Community layers to EPSG: 5070 - NAD 83 that allowed projection in miles to use the Buffer tool. Thus, although the project is still in EPSG: 4326 - WGS 84 projection, the CSV Spaceport and Community layers are in EPSG: 5070 - NAD 83.