# MakrDown.md

Markdonw is used for Readme.md file  
Open "Your_Readme.md" file with VSCode  
Use "Slit Editor"![Slit Editor](./pic-markdown/Split.png) for text style and Preview panels  
Select "Open as Preview"![Open as Preview](./pic-markdown/Preview.png) on the right side panel.

## Title

\# Title 1<br>
\## Title 2<br>
..<br>
\###### Title 6<br>

## new line
\<br> or two space  
Use \\ to ignore special character

## Character type
\_ _Italic_\_<br>
\*\***Bold**\*\*

## List
1. List1
1. List2
    1. List2.1
    1. List2.2

- List1
- List2
    - List2.1
    - List2.2

## Link or Picture
\[name](link) : [GOOGLE link](https://google.com) <br>
\[name](reference): [Google ref](ref_google) <br>
\[reference]:link<br>
Picture need \! before \[name](link) string.

## Code
```c
main(int argc, char *argv[]) {
    return 0;
}
```

```python
s = "Python syntax hightlight"
print s
```

```bash
$ npm run dev
```

## table
|item|Description|
| --- | --- |
| item1 | Description1 |
| item2 | Description2 |

## note (or reference)
Use "\<"
> reference
>> nested blockquote
>>> nested blockquote

## with HTLM
Add <u>underline</u> text.

## comment
--comment start--
<!-- hello -->
[//]: #hello
[//]: # (hello)
[//]: # "hello"
[//]: # 'hello'
--comment end--