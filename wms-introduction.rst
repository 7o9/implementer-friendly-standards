.

OGC WMS Introduction 
====================


About this Page
---------------

This page is a high level introduction to the OGC WMS standard. Please find the full technical description of the OGC WMS standard to learn about all the features and options the standard offers on the web sites of the Open Geospatial Consortium at: http://www.opengeospatial.org/standards/wms 

The OGC WMS Standard 
====================

The OGC WMS (Web Map Server) standard specifies the interface and parameters required to request dynamically rendered maps from a server. 


Current information about the status of this server can be found at the `metaspatial wiki <http://metaspatial.net/wiki/index.php/OGC_WMS_Demo_and_Reference_Server>`_.


Note
~~~~
If this endpoint is called without any additional parameters the software running on this server (`MapServer <http://mapserver.org>`_) will return the following text: 

``No query information to decode. QUERY_STRING is set, but empty.``

This is documented and expected behavior. The server did not get any instructions what to do and therefore only informs us that it has nothing to do. Other software may return different or even no information at all.

In order to query maps from this server we have to first get the metadata. This metadata is contained in the ''OGC WMS Capabilities Document'' and comes in XML format. It is requested by calling: 

``http://metaspatial.net/cgi-bin/ogc-wms.xml?REQUEST=GetCapabilities&SERVICE=WMS&VERSION=1.3``

This document contains all the information needed to make a valid OGC WMS GetMap request.

Getting a Map Image
-------------------
The ``GetMap`` request queries the server with a set of parameters describing the map image. The values of the parameters are taken from the Capabilities document (see above). A correctly formulated ``GetMap`` request will create the image shown below. 

*The URL of this link has been truncated for better readability.*::

	http://metaspatial.net/cgi-bin/ogc-wms.xml?
	VERSION=1.3.0&
	REQUEST=GetMap&
	SERVICE=WMS&
	LAYERS=DTM,Overview,Raster_250K,Topography,nationalparks,Infrastructure,Places&
	STYLES=,,,,,,&
	CRS=EPSG:27700&
	BBOX=424735.97883597884,96026.98412698413,467064.02116402116,127773.01587301587&
	WIDTH=400&
	HEIGHT=300&
	FORMAT=image/png&
	BGCOLOR=0xffffff&
	TRANSPARENT=TRUE&
	EXCEPTIONS=XML

Use the link: `GetMap <http://metaspatial.net/cgi-bin/ogc-wms.xml?VERSION=1.3.0&REQUEST=GetMap&SERVICE=WMS&LAYERS=DTM,Overview,Raster_250K,Topography,nationalparks,Infrastructure,Places&STYLES=,,,,,,&CRS=EPSG:27700&BBOX=424735.97883597884,96026.98412698413,467064.02116402116,127773.01587301587&WIDTH=400&HEIGHT=300&FORMAT=image/png&BGCOLOR=0xffffff&TRANSPARENT=TRUE&EXCEPTIONS=XML>`_ to retrieve the map image form the OGC Demo and Reference Server. It will be rendered dynamically each time you request the image (given that no proxy interferes and delivers an earlier graphic rendition of the map data).

	.. image:: images/metaspatial.net_GetMap.png
		:width: 400
		:height: 300
		:scale: 100
		:alt: Map image returned by the OGC WMS server

Layers
------
