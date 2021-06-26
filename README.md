# proto-pixels

simple tool to convert pixels to the Tailwind spacing scheme.

> IMPORTANT:  this is an extrapolation of the spacing scale within Tailwind.  Not all of these spaces exist in the default configuration.  Please check the documentation...

The output generates markdown by default:

## usage

```
node pixels --help
```
```
Usage: pixels [--start num] [--stop num] [-e]

Options:
      --help     Show help...                                          [boolean]
      --version  0.0.1                                                 [boolean]
  -x, --start    Start Value (px)                          [number] [default: 0]
  -z, --stop     Stop Value (px)                         [number] [default: 100]
  -s, --single   Single Value                         [boolean] [default: false]
  -e, --export   Export as Config                     [boolean] [default: false]
  -d, --debug    Debug output                         [boolean] [default: false]

copyright 2021
```

## examples

```
node pixels --start 20 --stop 30
```

this would generate markdown with the following info:

range: 20px-30px

| name | rems | pixels |
| :--- | :--- | ---: |
| 5 | 1.25 | 20 |
| 5.25 | 1.3125 | 21 |
| 5.5 | 1.375 | 22 |
| 5.75 | 1.4375 | 23 |
| 6 | 1.5 | 24 |
| 6.25 | 1.5625 | 25 |
| 6.5 | 1.625 | 26 |
| 6.75 | 1.6875 | 27 |
| 7 | 1.75 | 28 |
| 7.25 | 1.8125 | 29 |
| 7.5 | 1.875 | 30 |


if you want to save the markdown, you can do something like this:

```
node pixels > foo.md
```
```
node pixels --stop 90 --start 80 > foobar.md
```

## export

if you want to export the spacings so that you can drop them into the tailwind.config.js, you do something like this:

```
node pixels --start 306 --single -e
```

which generates:

```
theme: {
  extend: {
    spacing: {
      "76p5": "306px",
    }
  }
},
```

> **IMPORTANT:**
>   
> _you'll notice that the '.' in the name was replaced with a 'p' to make it compatible with the spacing names allowed in Tailwind..._
> 

## references

- [Default spacing scale](https://tailwindcss.com/docs/customizing-spacing#default-spacing-scale) - _the official Tailwind scale_


## footnote

this is the base definition which this tool uses:

```
const base = {
  tag: 0.5,
  rem: 0.125,
  px: 2,
};
```

everything else is built from this base...

> a variation of this tool could easily be created as a tailwind plugin so that you wouldn't need to manually paste the exports into your tailwind config.  
> 
> Create an issue on GitHub, if you think this would be useful...
> 



