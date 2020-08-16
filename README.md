# crlvc
Code Runner Like VsCode

## Motivation
After hours and hours of searching for a vim add-on equal to [code runner](https://marketplace.visualstudio.com/items?itemName=formulahendry.code-runner) and none of the ones found satisfied my needs, I said to myself "Hey, it's time to create it!"

## Quick Start
Open a terminal and run ./install

## Setting
Before installing you can configure the languages you want to be supported, The configuration file is called crlvc.json.

The file should look like this:

```` json

{
    "java": "cd {dir} && javac {fileName} && java {fileNameWithoutExt}",
    "kt": "cd {dir} && kotlinc-native {fileName} -o {fileNameWithoutExt} && ./{fileNameWithoutExt}.kexe",
    "c": "cd {dir} && gcc {fileName} -o {fileNameWithoutExt} && {dir}{fileNameWithoutExt}",
    "cpp": "cd {dir} && g++ {fileName} -o {fileNameWithoutExt} && {dir}{fileNameWithoutExt}",
    "py": "python -u {file}",
    "cs": "alacritty -e sh -c 'cd {dir} && mcs {fileName} && mono *.exe'",
    "ts": "deno run {file}",
    "rs": "cd {dir} && rustc {fileName} && {dir}{fileNameWithoutExt}"
}

````

In the crlvc.json a series of commands associated with file extensions is specified, if you want to add some other language follow this structure "extension": "commans"

### Variable

Variables are represented in python f string style
the available variables are the following:

  * file  //file path(~/anyrute/anyrute/myfile.cpp)
  * fileName  //file name(myfile.cpp)
  * fileNameWithoutExt  //file without extension(myfile)
  * dir  //path(~/anyrute/anyrute/)

#### Example

add support to javascript and objective c:

```` json
{
....... more..........
     "js": "node {file}",
     "objective-c": "cd {dir} && gcc -framework Cocoa {fileName} -o {fileNameWithoutExt} && {dir}{fileNameWithoutExt}"

}


````

## Use

In Terminal:

  crlvc ~/somedir/myfile

so simple.

### Use in vim

The easiest way to use is by assigning it shortcuts

add this to your .vimrc or init.vim:

```` vim
nmap <leader>B :belowright 7split term://crlvc %<CR>

````
Use the combination of keys you want

### Screenshots

![typescript](https://i.ibb.co/JCg3tNd/ezgif-com-video-to-gif.gif)

![python](https://i.ibb.co/1njTRTL/ezgif-com-video-to-gif.gif)

# Important
If you have any ideas to improve this project, do not hesitate to make a request, if problems arise, try to solve them and publish them. Don't be so picky I did this in one afternoon.






