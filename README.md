# MTUOC Web UI

Web user interface for translating text and documents (.txt, .docx and .odt at the moment) with MTUOC machine translation servers.

# Installing the Web UI

Clone the repository and install the package with pip: `pip install mtuoc-web-ui/`

# Installing mtuoc-translate-files for file translation

For document translation, the mtuoc-translate-files package also needs to be installed:
   - `git clone https://github.com/TommiNieminen/mtuoc-translate-files.git`
   - `cd mtuoc-translate-files`
   - `git switch okapi`
   - `pip install .

### Install Java and the MTUOC Okapi wrapper:

mtuoc-translate-files uses the Okapi framework to parse and generate files. Okapi is built on Java, so using it requires a Java runtime engine.

1. Download OpenJDK22 for your system from here: [https://jdk.java.net/22/](https://jdk.java.net/22/)
2. Extract the OpenJDK22 tar.gz archive that you downloaded in the previous step (at the time of writing, the archive name is openjdk-22.0.1_linux-x64_bin.tar.gz): `tar -xvf openjdk-22.0.1_linux-x64_bin.tar.gz`
3. Export the path of the extracted tar.gz archive as JAVA_HOME environment variable. For instance, if you extracted the archive into your home directory: `export JAVA_HOME="$HOME/jdk-22.0.1"`
4. Download the MTUOC Okapi wrapper jar file from here: [https://github.com/TommiNieminen/mtuoc-translate-files/releases/tag/okapi_wrapper_v1](https://github.com/TommiNieminen/mtuoc-translate-files/releases/download/okapi_wrapper_v1/mtuocokapiwrapper-1.0.jar)
5. Create a _jars_ directory in the top directory of the mtuoc-web-ui repository, and move the mtuocokapiwrapper-1.0.jar there.

# Usage

1. The Web UI reads the server information from a file called _mtSystems.yaml_. There is an example file in the top folder of the repository. Modify the file to contain the servers you wish to use.
2. Change the working dir to the top directory of the mtuoc-web-ui repository (the one containing the _jars_ subdirectory and the _mtSystems.yaml_ file).
3. Start the Web UI with the following command: `gunicorn -w 4 -t 600 -b 127.0.0.1:5000 'wsgi:app'`.
4. The API is now available at localhost:5000 (this can be changed by providing a different -b value to gunicorn in the previous step).

Adjust the timeout (-t) and worker amount (-w) option values provided to gunicorn in step 3 according to your use case (for very large files, a longer timeout may be needed, and the worker amount may need to be increased if there are many concurrent requests). Do not increase the amount of threads (the default is 1), as the this seems to break the Java integration required for file translation.

Adapted from the LibreTranslate UI. MTUOC Web UI is not officially associated with LibreTranslate or its products.
