# Unlocking Data Potential: Utilizing REDCap API Integration for Effective DataManagement and Reporting

##### East Carolina University Brody School of Medicine 
##### Office of Data Analysis and Strategy
---

This document will assist with questions on how to use the provided REDCap API call code.  Some of the various functions and options used in the call syntax will be explained; but for further explanation, please visit the API documentation on REDCap.  There you will find the full list of call types, and any required or optional parameters for a given API call.  The `REDCap_to_PowerBI_API_Call.txt` file shows the typical, default use of how to call the REDCap instruments and receive a CSV file of the collected data.  The code in this file can be copied into PowerBI when editing a data connection with the PowerQuery Editor, the code should then be pasted into the Advanced Editor.

### API Call Definitions and Descriptions

|     Section     |     Definition     |
| --------------- | ------------------ |
| `actualURL` | REDCap API URL. |
| `record` | API options required to customize the call. |
| `token` | Instrument specific API security token. |
| `content` | Target section of instrument for API call. |
| `format` | Return format of data. |

Additional information about each of these parameters and more options for API calls are available on the REDCap API Documentation site with examples and instructions on how to use each.

* `actualURL`
	* This URL is provided by REDCap under the API Documentation section and should be specific to your institution.  This URL should be the same for every type of API call to the REDCap site.
* `record` 
	* This parameter states the content to be retrieved by the call and contains an array of optionals to customize the call.  These options could alter which columns, data headers, timestamps, etc. are included in the output.
* `token`
	* This is simply a string of characters used for security and confirming the correct connection in the API.  The token can be requested in the specific REDCap Instrument and a user must have the proper rights to request one.
* `content` 
	* This parameter states the type of data to be retrieved from REDCap and can contain any aspect of a Project, including the Project type itself.  The API Documentation has more information about all possible options for this parameter and what each includes in the output.
* `format` 
	* This parameter states the return type to be retrieved from REDCap via the API call.  These are limited to the type of `content` in the call but can be CSV, XML, FLAT, etc.
---

#### Office of Data Analysis and Strategy Info
**Team Members** - Jhojana Infante, Jedediah Smith, Lennen Madere

**Email** - odas@ecu.edu