# ccc
Cascading Content Closures
modeled somewhat after CSS
every html page contains [ html.spec, http.headers, html.body ]
CCC root templates are defined in a render.ht file in the root of a domain
see {EXAMPLES] for a rudimentary template example

a templates has three sections:
[
<!-- Vars( [var = val]* ) --> 
<!-- css( [css style directives]* ) -->
and 
{ html }
]
templates can include templates using  <!-- include(<template.name>) -->
css() declarations are inlined in the page's http.headers section
vars() are saved as an array of one-line variable-definitions
when the templates are rendered all variable-names 
'{ <0variable.name> }' are replaced by the named variable.value
there are two special templates: render.ht, content.ht
'content' containing <main id="content>...{html}...</main>
is placed automatically as the top-level 'page.content'

render.ht is a sequence of named templates 
<!-- tpl(<template.name>) { --> {html} <!-- } -->
any 'render file' is scanned for templates that maybe be included using
'<!-- include( [template.name] ) -->' or '{{ [template.name] }}'

[EXAMPLES]
<!-- page.format) --><!DOCTYPE html>
<html lang="en">
 <!-- insert(page.vars) -->
 <!-- insert(http.header) -->
 <!-- insert(page.layout) -->
</html><!-- } -->
