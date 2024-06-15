<center><h1>temgen</h1></center>

A simple template generator for creating latex/typst article/presentation
templates.

## Usage

```bash
temgen -h
temgen [-lf] identity [output]
```

- `-h`: Show help message.
- `-l`: List template directories, instead of generating a template.
- `-f`: force overwrite of existing directory.

`identity` is the identity of the template to generate. It is of the form
`{a,p}{l,t}[:<name>]`. E.g. `al:template1`, `pt`.
- `{a,p}` stands for article or presentation.
- `{l,t}` stands for latex or typst.
- `[:<name>]` is an optional name for the template. If it is not provided, 
    interactive mode will be used to get the name. If it is provided, `temgen`
    uses a fuzzy search to find the template. 

`output` is the output directory for the template. If it is not provided, the
current directory will be used. By default, `temgen` refuses to overwrite
non-empty directories. Use `-f` to force overwrite.

## The template directory

The searching of the template directory is done in the following order:
- environment variable `TEMGEN_TEM_DIR`.
- read from the configuration file `~/.config/temgen/temgen.conf`, the first valid line of which is the template directory.
- `~/.local/share/temgen/template/`.
- `/usr/share/temgen/template/`.

And `temgen` stops at the first directory that exists.

The template directory has the following subdirectories, served as the templates:
```
{art,pre}-{latex,typst}-name
```
E.g. `art-latex-template1`, `pre-typst-nju`.

All files that does not match the above pattern will be ignored.
