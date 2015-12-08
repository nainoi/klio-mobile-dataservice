  1. Checkout framework's eclipse project using your favorite eclipse svn plugin
  1. Create a new android project and from the project proprieties choose "Java Build Path" -> "Project" and add the project "KlioMobileDS"
  1. Change application permission so it can access the internet, add the following code in AndroidManifest.xml
```
<uses-permission android:name="android.permission.INTERNET"></uses-permission>
```
  1. In your Activity onCreate method add the following code, changing the message broker URL, service and method:
```
AMFConnection amfConnection= new AMFConnection();

try {	
	amfConnection.connect("http://yourdomain.com/messagebroker/amf");
} catch (ClientStatusException cse) {
	System.out.println("Error while connecting");
	return;
}
		
try {
	Object result = amfConnection.call("yourService.yourMethod");
	System.out.println(result);
} catch (Exception e) {
	System.out.println("Error while calling remote method");
	return;
}
```