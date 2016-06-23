Table of Content
----------------
* The OGC WMS Standard
* What Can You Do With It?
* Primary Use Cases
* Maturity of the standard
* Primary API Calls
* GetMap Example
* Optional Requests
* Links
* Related standards

About this Page
===============

This page is a high level introduction to the OGC WMS standard. Please find the full technical description of the OGC WMS standard to learn about all the features and options the standard offers on the web sites of the Open Geospatial Consortium at: http://www.opengeospatial.org/standards/wms 

The OGC WMS Standard 
--------------------

The OGC WMS (Web Map Server) standard specifies the interface and parameters to dynamically request maps from a server. Every OGC WMS is individually configured and can serve a multitude of different maps, combination of layers and can optionally even be styled with different cartography. The "Capabilities" document contains all information needed to intelligently request maps from the server. 

What Can You Do With It?
========================

In simple words: Get maps! Depending on the configuration of the server maps can come in a variety of formats, sizes, coordinate and projection systems. The following examples show the same map data at different scales and in different coordinate systems. 

     .. image:: https://raw.githubusercontent.com/7o9/implementer-friendly-standards/master/full_map.png

     `OGC WMS GetMap request: Get this map Online <http://metaspatial.net/cgi-bin/ogc-wms.xml?VERSION=1.3.0&REQUEST=GetMap&SERVICE=WMS&LAYERS=Topography,Infrastructure,osm_points,Places&STYLES=,,,&CRS=EPSG:27700&BBOX=440956.1728395062,113999.62962962964,442343.8271604938,115560.37037037036&WIDTH=282&HEIGHT=316&FORMAT=image/png&BGCOLOR=0xffffff&TRANSPARENT=TRUE&EXCEPTIONS=XML>`_


Maps can be structured into "layers" and the server can offer to apply filters to select or highlight specific features. The OGC WMS standard offers a great many options limited only by your data and your creativity. 

.. image:: https://raw.githubusercontent.com/7o9/implementer-friendly-standards/master/wms_layers_600px.png


This demo server hosts street data. The images show how the topography is overlayed with infrastructure, points of interests and finally some text notes. The combination of all layers shows a regular map. Additionally you can overlay map data from other sources which can even come from different and remote providers. The result is onyl visualized in your client (for example any desktop GIS or web map client).

Primary Use Cases
=================

The OGC WMS standard is used to retrieve Online maps via the Internet (http). Maps can be linked from a web site, navigated with a professional GIS client, or used on mobile devices. Any application that needs map images can use the OGC WMS standard to get maps. And because it is a widely accepted industry standard almost any map generating or using software can "speak" OGC WMS allowing to combine maps from several sources regardless of the underlying software implementation. 

Maturity of the standard
========================

The OGC WMS standard is mature. It has been adopted by ISO and is an integral component of many national and international regulations and directives. The first version was released in 2001, the current stable version 1.3 has been released in 2006 and is implemented by several hundred software products. 

Primary API Calls
=================

There are two primary API calls: 

* GetCapabilities
* GetMap

GetCapabilities
~~~~~~~~~~~~~~~

The GetCapabilities request returns a document in XML format which contains all information a client needs to make a GetMap request. 

*The URL of this link has been truncated for better readability:*
   http://metaspatial.net/cgi-bin/ogc-wms.xml?
   
   SERVICE=WMS&
   
   VERSION=1.3.0&
   
   REQUEST=GetCapabilities

Use this link: `GetCapabilities <http://metaspatial.net/cgi-bin/ogc-wms.xml?SERVICE=WMS&VERSION=1.3.0&REQUEST=GetCapabilities>`_ document from the OGC WMS Demo and Reference Server.

GetMap
~~~~~~

The GetMap request returns an image files of the requested map. In case the server cannot answer the request an error message is returned. This error message is either formatted as an image of the same size as the requested map or as an XML string. 

*The URL of this link has been truncated for better readability:*

   http://metaspatial.net/cgi-bin/ogc-wms.xml?

   SERVICE=WMS&

   VERSION=1.3.0&

   REQUEST=GetMap&  LAYERS=DTM,Overview,Raster_250K,Topography,nationalparks,Infrastructure,Places&

   STYLES=,,,,,,&

   CRS=EPSG:27700&

   BBOX=424735.97,96026.98,467064.02,127773.01

   WIDTH=400&

   HEIGHT=300&

   FORMAT=image/png&

   BGCOLOR=0xffffff&

   TRANSPARENT=TRUE&

   EXCEPTIONS=XML

Use the link: `GetMap <http://metaspatial.net/cgi-bin/ogc-wms.xml?VERSION=1.3.0&REQUEST=GetMap&SERVICE=WMS&LAYERS=DTM,Overview,Raster_250K,Topography,nationalparks,Infrastructure,Places&STYLES=,,,,,,&CRS=EPSG:27700&BBOX=424735.97883597884,96026.98412698413,467064.02116402116,127773.01587301587&WIDTH=400&HEIGHT=300&FORMAT=image/png&BGCOLOR=0xffffff&TRANSPARENT=TRUE&EXCEPTIONS=XML>`_ to retrieve the map image form the OGC Demo and Reference Server. It will be rendered dynamically each time you request the image (given that no proxy interferes and delivers an earlier graphic rendition of the map data).

	.. image:: http://metaspatial.net/cgi-bin/ogc-wms.xml?VERSION=1.3.0&REQUEST=GetMap&SERVICE=WMS&LAYERS=DTM,Overview,Raster_250K,Topography,nationalparks,Infrastructure,Places&STYLES=,,,,,,&CRS=EPSG:27700&BBOX=424735.97883597884,96026.98412698413,467064.02116402116,127773.01587301587&WIDTH=400&HEIGHT=300&FORMAT=image/png&BGCOLOR=0xffffff&TRANSPARENT=TRUE&EXCEPTIONS=XML
		:width: 400
		:height: 300
		:scale: 100
		:alt: Map image returned by the OGC WMS server

GetMap Example

Optional Calls
==============

There are several optional API calls. These include:

* GetLegendGraphic - returns a legend image
* GetFeatureInfo - returns information about features 'on' a map

Demo and Reference Server
=========================
The `OGC WMS Demo and Reference Server <http://metaspatial.net/wiki/index.php/OGC_WMS_Demo_and_Reference_Server>`_ is an external resource which can be used to test a live and compliant implementation of the OGC WMS standard. 

Related Standards Family
------------------------
Every standard of the OGC is complemented, referenced or used by other OGC standards. The following list gives an overview of the most related standards. 

* OGC WMTS (Web Map Tile Service): For heavy use and high scalability the OGC has developed the WMTS service standard. It is an area-wide collection of consistently addressable seamless map image tiles organized in a pyramid with fixed scales. Clients request as many tiles as needed to cover the requested area. 
* OGC WFS (Web Feature Service): The WFS service standard returns geographical features like points, lines and polygons in a geographical file format.
* OGC GML (Geographic Markup Language): Geographical XML file format to encode complex features like points, lines and polygons, and collections thereof. 
* OGC KML (Keyhole Markup Language): Geographical XML file format to encode features like points, lines and polygons, includes styling information.
* GeoJSON. Serialized geographical file format to encode simple features like points, lines and polygons ignoring coordinate system specifics. 

