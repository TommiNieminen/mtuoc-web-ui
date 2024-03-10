# MTUOC Web UI

Web user interface for translating text and documents (.txt, .docx and .odt at the moment) with MTUOC machine translation servers.

# Installation

1. Clone the repository and install the package with pip: `pip install mtuoc-web-ui/`
2. For document translation, the mtuoc-translate-files package also needs to be installed:
   - `git clone https://github.com/TommiNieminen/mtuoc-translate-files.git`
   - `pip install mtuoc-translate-files/` 
  
# Usage

1. The Web UI reads the server information from a file called _mtSystems.yaml_. There is an example file in the _mtuocwebui_ folder of   the repository. Modify the file to contain the servers you wish to use, and save it to the location from which you intend to launch the Web UI.
2. Navigate to the location where you saved _mtSystems.yaml_, and start the Web UI with the `mtuocwebui` command.
3. The Web UI starts in localhost:5000 by default, run `mtuocwebui --help` to see options for launching with a different host and port.

Adapted from the LibreTranslate UI. MTUOC Web UI is not not officially associated with LibreTranslate or its products.
