# GEMINI 2.2 schema plugin for GeoNetwork 3.8.x and 3.10x alongside GEMINI 2.3

This is the GEMINI 2.2 schema plugin for GeoNetwork 3.12.x, where GEMINI 2.3 is also installed. Switch to the appropriate branch in this repository for versions that work with earlier versions of GeoNetwork.

### GeoNetwork version to use with this plugin

Use GeoNetwork 3.12.x.

**This will not work in earlier or later versions of the software.**

## Installing the plugin in GeoNetwork 3.12.x

### Adding to an existing installation

* Download or clone this repository, ensuring you choose the correct branch (3.12.x).
* Copy `src/main/plugin/iso19139.gemini22` to `INSTALL_DIR/geonetwork/WEB_INF/data/config/schema_plugins/iso19139.gemini22` in your installation.
* Copy `target/schema-iso19139.gemini22-3.12-SNAPSHOT.jar` to `INSTALL_DIR/geonetwork/WEB_INF/lib`
* Restart GeoNetwork
* Check that the schema is registered by visiting Admin Console -> Metadata and Templates -> Standards in GeoNetwork. If you do not see iso19139.gemini22 then it is not correctly deployed.  Check your GeoNetwork log files for errors.
* Adding the plugin to the source code prior to compiling GeoNetwork

### The best approach is to add the plugin as a submodule. Use https://github.com/geonetwork/core-geonetwork/blob/3.12.x/add-schema.sh for automatic deployment:

```
.\add-schema.sh iso19139.gemini22 http://github.com/metadata101/iso19139.gemini22 3.12.x
```

#### Building the application 

See https://geonetwork-opensource.org/manuals/trunk/en/maintainer-guide/installing/installing-from-source-code.html. 

Ensure that you build GeoNetwork with the directive `-DschemasCopy=True` (and also use the same directive if running using the embedded jetty server plugin). For example from the GeoNetwork root directory:

```
sudo mvn clean install -DskipTests -DschemasCopy=true -Pes
cd web
sudo mvn jetty:run -DschemasCopy=true
```


Once the application is built `web/target/geonetwork.war` will contain GeoNetwork with the Gemini 2.2 schema plugin included.