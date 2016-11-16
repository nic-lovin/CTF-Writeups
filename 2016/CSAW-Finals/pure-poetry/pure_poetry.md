# CSAW Finals 2016: ladykiller - Forensics 200

For this challenge, we are given a rdef file:

```
resource(35,"VECTOR:ICON") #'VICN' array {
	$"6E636966010500060A0422202020206022600A0442204020406042600A04225E"
	$"22606060605E0A04223E22406040603E0A0424202426262626200A0428222529"
	$"2A292B22EB0A000402030001000A000104000A00010402400000000000000000"
	$"3EAAAA440000220000000A000104024000000000000000003CAAAA460000000000"
  ...
```

By looking on Google, we realise it's some vector used on Haiku. Oh great. Let's get a VM of Haiku.  

After reading this page: https://www.haiku-os.org/documents/dev/compile_them_resources  
We discover that what we got is just a icon in text format and it must be compiled to be an usable resource :  
> rc -o compiled.rsrc pure.rdef  

After that, we have to bind the resource to a file, according to this: https://www.haiku-os.org/node/10404  
> touch pure  
> xres -o pure compiled.rsrc

Then we obtain the file with the icon.  

![Image] (pure.png)  

The thumbnail is too small to see anything. In the challenge description, we remember that we saw the number "128". Let's try to change the size of it:  

![Image] (pure2.png)

Oh, looks like a datamatrix. Let's scan it and get the flag.

![Image] (pure3.png)
