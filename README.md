# cbClarifai
This is an unofficial Coldfusion Coldbox client for Clarifai's image recognition API.

## Prerequisites
Before using this gem, make sure to [create an account for Clarifai](https://developer.clarifai.com/signup/) and create an application to obtain an API key.

Please note if choose the free Community plan their license agreement requires you to display AI by Clarifai

## Installation

This API can be installed as standalone or as a ColdBox Module.  Either approach requires a simple CommandBox command:

```
box install cbClarifai
```

Then follow either the standalone or module instructions below.

### Standalone

This API will be installed into a directory called `cbClarifai` and then the API can be instantiated via `new cbClarifai.models.Client()` with the following constructor arguments:

```
<cfargument name="apiKey"             required="true">
```

### ColdBox Module

This package also is a ColdBox module as well.  The module can be configured by adding `ClarifaiApiKey` in your application configuration file: `config/Coldbox.cfc` with the following settings:

```
    settings = {

        // Your Clarifai API Key
        ClarifaiApiKey = "",

        // Your settings....

    };
```

Then you can leverage the API CFC via the injection DSL: `Client@cbClarifai`

## Usage

```
/**
* A normal ColdBox Event Handler
*/
component{
	property name="predict" inject="predict@cbClarifai";
	
	function index(event,rc,prc){
		// returns translated text as string
		var p=predict.predict( asset = 'https://www0.f1online.de/preW/004266000/4266061.jpg', modelname='general' );
		writeDump(p);
		abort;
		
		
	}
}
```

## Written by
www.akitogo.com

## Disclaimer
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
