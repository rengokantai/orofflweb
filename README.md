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
