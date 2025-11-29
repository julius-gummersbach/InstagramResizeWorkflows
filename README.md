# InstagramResizeWorkflows
Mac Workflows for posting portrait images to Instagram without cropping

- These Workflows always produce a 1440x1800 image, and add either white or black padding around the image, as indicated by the W or B.
- The Workflows with "Portrait" in the name take images as input, whose height is larger than their width
- The Workflows with "LtoP" in the name, take images as input, whose width is larger than their height (landscape to portrait)

The Workflows use `sips`.
Example (`Insta Portrait W.workflow`):

```
on run {input, parameters}  
repeat with this_file in input
    set this_path to the quoted form of the POSIX path of this_file
	do shell script "sips " & this_path & " --resampleHeight 1720"
	do shell script "sips " & this_path & " -p 1800 1440 --padColor FFFFFF -i"
end repeat
return input
end run
```
