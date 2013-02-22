Haml parser reference
=====================

What is Haml?
-------------
This is the best Haml definition:

>Haml takes your gross, ugly templates and replaces them with veritable Haiku.
>Haml is the next step in generating views in your Rails (also in PHP) application. Haml is a refreshing take that is meant to free us from the shitty templating languages we have gotten used to.

>Haml is based on one primary principal. Markup should be beautiful.

I'm not Haml author, I only implemented Haml in PHP. Why? I tested a lot of templating system like Smarty, PHP TAL, clean PHP, but all has one problem - too many unreadable code.

HamlParser class reference
==========================

### `object __construct([string path, [mixed compile]])`

The constructor. Create the instance of HamlParser.

#### Arguments

    `path`
    Path to directory with templates. Path must exists and can't ends with slash
    (/).

        `compile`
        If `compile == false` then path for compiled templates is same as source path
        and templates are compiled on every request. If `compile` is string then
        `compile` = path to compiled templates and templates are compiled only if
        source changed.

### `string __toString()`

Render current template and return it.

### `object append(array data)`

Sets the template variables from associative array and return object instance.

#### Arguments

    `data`
    Associative array where keys are variables names and values are variables
    values.

### `object assign(string name, mixed value)`

Sets the template variable and return object instance.

#### Arguments

    `name`
    Name of variable.

        `value`
        Value of variable.

### `object clearCompiled()`

Removes all compiled templates (*.hphp) from temporary directory and return
object instance.

### `object clearVariables()`

Clear templates variables and return object instance.

### `void display([string filename])`

Display current template or template from `filename`.

#### Arguments

    `filename`
    Optional filename or full file path to template.

### `string fetch([string filename])`

Fetch (return compiled) current template or template from `filename`.

#### Arguments

    `filename`
    Optional filename or full file path to template.

### `string getFilename(string name)`

Return filename used for including. You can override this method.

#### Arguments

    `name`
    Name to file (view) to include.

### `array getVariables()`

Return associative array of variables assigned to template.

### `string render()`

Similar functionality as `fetch()`.

### `object setFile(string filename)`

Sets template filename and return object instance.

#### Arguments

    `filename`
    Real path or file in templates directory.

### `object setPath(string path)`

Sets path to templates and return object instance.

#### Arguments

    `path`
    Path to templates without ending slash (/).

### `object setSource(string source)`

Sets Haml source and return object instance.

#### Arguments

    `source`
    Haml source (can be multiline or one line).

### `object setTmp(string path)`

Sets path to compiled templates and return object instance.

#### Arguments

    `path`
    Path to compiled templates.

### `object registerBlock(callable block, string name)`

Register text processing block

#### Arguments

    `block`
    The processing function. Argument of it is text block data, callable must
    return processed data.

        `name`
        Name of processing block used in templates

### `object unregisterBlock(string name)`

Unregister (delete) text processing block

#### Arguments

    `name`
    Name of processing block to unregister

### `object registerFilter(callable filter, string name)`

Register output filter

#### Arguments

    `filter`
    The processing function. Argument of it is compiled template, callable must
    return processed compiled template.

        `name`
        Name of output filter

### `object unregisterFilter(string name)`

Unregister (delete) output filter

#### Arguments

    `name`
    Name of output filter to unregister




