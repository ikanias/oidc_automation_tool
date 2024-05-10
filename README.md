# oidc_automation_tool
Creating an RHTPA bearer token to use when uploading SBOMs and VEX files
--------------------------------------------------------------------------

This automated tool is using the oidc Rust tool to extract a bearer token from RHTPA apllication,
and then using it to upload SBOM files and VEX files to the system.

How to use the tool
--------------------
1. Clone the repo: git clone git@github.com:ikanias/oidc_automation_tool.git
2. Select an image that you want to analyse and generate an SBOM from and copy it to your clipboard
3. run the tool by typing: python3 main.py
4. In the first prompt of the dialog insert the image location - it can be either a full location like:  quay.io/xiezhang7/hello-python:latest
   or a short one like alpine:edge. Please do not add any prefix like 'http:' or 'https:' to the image location
5. Next you need to insert the SBOM standard to generate - cyclonedx or spdx
6. Last thing to insert is the file name you want for your SBOM. You only need to add the name not the file type. The file will be created automatically
   as a .json file

The tool also checks if the user has 'Syft' installed in the local environment. If the user does not have 'Syft' then it will be installed automatically.
If the user already has 'Syft', the tool will skip the installation and start generating the SBOM.
During the runtime of the tool the user will get the image purl. This is important for a later use, because it must be added to the API request to Exhort
(i.e. in Postman) in addition to the SBOM itself, to get the vulnerabilities analysis (.json response from Exhort).
![image](https://github.com/ikanias/oidc_automation_tool/assets/69799772/a69dcbe4-ef62-4164-bc24-49ea7df214ab)
