#### orofflweb
- cp2
```
navigator.onLine (true or false)
```
special case: For example, when you are in hotel, wifi needs signin in order to get access to internet.If not login, still return true.

old way:
```
<body ononline="" onoffline="">
</body>
```
better:
```
window.addEventListener("online",function(e){

});

```

Baisc manifest:
in index.html:
```
<html manifest="offline.manifest">
.....
</html>
```

create offline.manifest:(will load offline) note remote server file should begin with //
```
CACHE MANIFEST

css/xxx.css
//fonts.googleapis.com/css?family=xxxx
file1
file2
```
Debug: Resource->application cache
```
```
Remainder: it you set manifest, even online, system still assume you are offline
Improved:
```
CACHE MANIFEST

CACHE: (to update this, you may append a space)
css/xxx.css
//fonts.googleapis.com/css?family=xxxx
file1
file2

NETWORK:
*

#Comment should start with pound sign
```
Every time you update a resource file(e.x css file) you need to update manifest file,even add a space.

explanation:
when connecting to internet, it will load all under NETWORK category.

- Application cache
events:
```
oncached
onchecking
ondownloading
onerror
onnoupdate
onobsolete  //manifest file does not exist
onprogress
onupdateready
status
```
Note application cache will not update partial resources. Only update all or fail all

- Advanced
fallback (if original image is not available, then show offline.jpg)
```
CACHE MANIFEST

CACHE:
css/xxx.css
//fonts.googleapis.com/css?family=xxxx
file1
file2

NETWORK:
*

FALLBACK:
original.jpg offline.jpg
```
issue: how can we update partial resouces?
