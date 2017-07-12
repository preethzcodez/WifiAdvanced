# WifiAdvanced
This library can be used to set advanced settings for wifi such as manual proxy and static ip configurations through your app. This code works in Android 5.0, it also works in 6.0 but you cannot update a network that you have not created yourself (due to android new rules: https://developer.android.com/about/versions/marshmallow/android-6.0-changes.html#behavior-network).

## Add Dependency
Gradle: <br/>
```
repositories {
    maven {
        url  "http://dl.bintray.com/preethzcodez/maven" 
    }
}

dependencies {
  compile 'com.preethzcodez:wifiadvancedlib:1.0'
}
```
or Maven:
```
<dependency> 
  <groupId>com.preethzcodez</groupId> 
  <artifactId>wifiadvancedlib</artifactId> 
  <version>1.0</version> 
  <type>pom</type> 
</dependency>
```
## Usage
**Set Proxy From PAC URL**
```
/* 'conf' is your wifi configuration
example: WifiConfiguration conf = new WifiConfiguration(); */
conf = ProxySettings.setPacURL(conf,url);
```
**Set Manual Proxy**
```
/* 'conf' is your wifi configuration
example: WifiConfiguration conf = new WifiConfiguration(); */
conf = ProxySettings.setManualProxy(conf,host_name,port,bypass_list);
```
**Set Static IP Configuration**
```
/* 'conf' is your wifi configuration
example: WifiConfiguration conf = new WifiConfiguration(); */
conf = IPSettings.setStaticIpConfiguration(conf,InetAddress.getByName(IP_ADDRESS),PREFIX_LENGTH,InetAddress.getByName(GATEWAY),dns_servers);
```
**Example Code - Static IP Configuration**
```
String IP_ADDRESS = "192.168.1.13";
String GATEWAY = "192.168.1.1";
int PREFIX_LENGTH = 24;
InetAddress[] dns_servers = new InetAddress[]{InetAddress.getByName("8.8.8.8"), InetAddress.getByName("8.8.4.4")};
conf = IPSettings.setStaticIpConfiguration(conf,InetAddress.getByName(IP_ADDRESS),PREFIX_LENGTH,InetAddress.getByName(GATEWAY),dns_servers);
```
