About this Page
---------------

This page is a high level introduction to the OGC WMS standard. Please find the full technical description of the OGC WMS standard to learn about all the features and options the standard offers on the web sites of the Open Geospatial Consortium at: http://www.opengeospatial.org/standards/wms 

The OGC WMS Standard 
====================

The OGC WMS (Web Map Server) standard specifies the interface and parameters to dynamically request maps from a server. Every OGC WMS is individually configured and can serve a multitude of different maps, combination of layers and can optionally even be styled with different cartography. The "Capabilities" document contains all information needed to intelligently request maps from the server. 

What Can You Do With It?
------------------------

In simple words: Get maps! Depending on the configuration of the server maps can come in a variety of formats, sizes, coordinate and projection systems. Maps can be structured into "layers" and the server can offer to apply filters to select or highlight specific features. The OGC WMS standard offers a great many options limited only by your data and your creativity. 

This demo server hosts street data. On one image only the highways are selected, on the next only footpaths and the third contains a combination of all the linear road infrastructure items. 

Example: 

Primary Use Cases
-----------------

The OGC WMS standard is used to retrieve Online maps via the Internet (http). Maps can be linked from a web site, navigated with a professional GIS client, or used on mobile devices. Any application that needs map images can use the OGC WMS standard to get maps. And because it is a widely accepted industry standard almost any map generating or using software can "speak" OGC WMS allowing to combine maps from several sources regardless of the underlying software implementation. 

Maturity of the standard
------------------------

The OGC WMS standard is mature. It has been adopted by ISO and is an integral component of many national and international regulations and directives. The first version was released in 2001, the current stable version 1.3 has been released in 2006 and is implemented by several hundred software products. 

Primary API Calls
-----------------

There are two primary API calls: 
- GetCapabilities
- GetMap

The *GetCapabilities API call returns the metadata of the server. The ''OGC WMS Capabilities Document'' comes in XML format and is requested by calling (example): 

``http://metaspatial.net/cgi-bin/ogc-wms.xml?REQUEST=GetCapabilities&SERVICE=WMS&VERSION=1.3``

This document contains all the information needed to make a valid OGC WMS GetMap request.

The GetCapabilities request returns a document in XML format which contains all information a client needs to make a GetMap request. The GetMap request returns the map image. In the case that the server cannot answer the request an error message is treturend, either as an image of the same size as the requested map or as an XML string. 

GetMap Example


Optional Calls
--------------

There are several optional API calls. These include:
- GetLegendGraphic - returns a legend image
- GetFeatureInfo - return information about features on a map
- GetStyle and SetStyle -  cartography based on the OGC SLD (Styled Laer Descriptor) standard. 



Links

Related Standards Family
------------------------

For heavy use and high scalability the OGC WMTS (Web Map Tile Service) may be more appropriate. It returns preseeded map image tiles (map images). The WMS standard gets completmented by the OGC WFS (Web Feature Service) standard which returns geographical feautres like points, lines and polygons with coordinates in different formats like OGC WFS, KML or GeoJSON. These objects can then be rendered on top of the background image. 




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

