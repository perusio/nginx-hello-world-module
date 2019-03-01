# Hello World Module for Nginx

## Introduction

This module serves as a learning exercise for me, and hopefully for
others too, when doing [Nginx](http://nginx.org) module development. 

I [stole](http://dominicfallows.com/2011/02/20/hello-world-nginx-module-3/)
the code and added some notes using mostly Evan Miller's
[Nginx Module Development Guide](http://www.evanmiller.org/nginx-modules-guide.html). Also
helpful is the
[translation](http://antoine.bonavita.free.fr/nginx_mod_dev_en.html)
of Vhalery Kholodov's
[Nginx Module Guide](http://www.grid.net.ru/nginx/nginx-modules.html)
done by [Antoine Bonavita](http://antoine.bonavita.free.fr/) that also
mantains a [Nginx Discovery](http://www.nginx-discovery.com/) blog to
document his journey on Nginx module development.

## Installation

   1. Configure Nginx adding this module with:
          
          Static Module : ./configure (...) --add-module=/path/to/nginx-hello-world-module
          Dynamic Module: ./configure (...) --add-dynamic-module=/path/to/nginx-hello-world-module
       
   2. Build Nginx as usual with `make`.
   
   3. Configure the module. There's only one directive `hello_world`
      that is supported in the **location** context only.
      
      Example:
          
          location = /test {
             
             hello_world;
          
          }

      Now doing something like:
          
          curl -i http://example.com/test
          
      should return the **hello world** string as the response body.

## Further reading

 * English: You can go to the [Nginx Planet](http://planet.nginx.org/)
   and get a lot of Nginx related information.
  
 * Russian: The [Habrahabr Nginx Blog](habrahabr.ru/blogs/nginx/) a
   treasure trove of Nginx related discussions. Use google translate
   or Babelfish if you don't read Russian.
      
## TODO

 1. Add an argument to the `hello_world` directive specifying the
    language. For example:
    
    * en: hello world
    
    * fr: bounjour monde
    
    * pt: olá mundo
 
    * es: hola mundo
 
 2. Make the `hello_world` directive be also defined in the **if in
    location** context (`NGX_HTTP_LIF_CONF`) in
    `ngx_http_config.h`. Which implies defining a **merge
    configuration** function.
 
 3. Document everything with
    [Doxygen](https://secure.wikimedia.org/wikipedia/en/wiki/Doxygen)
    linking the relevant header and source files from the Nginx core.
