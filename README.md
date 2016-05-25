MLAutoReplace
=============

Xcode plugin, Re-Intent, make you write code more quickly.   
Use a portion code of [VVDocumenter-Xcode](https://github.com/onevcat/VVDocumenter-Xcode).

##Overview
You can use shortcut key `Shift+Command+\` to auto re-indent all source of the current edit file.  

You can custom other replacer with regex.  
![regex replace](https://raw.githubusercontent.com/molon/MLAutoReplace/master/replaceOther.gif)  
![regex replace](https://raw.githubusercontent.com/molon/MLAutoReplace/master/replaceTS.gif)  

You can input common getter quickly.  
![replace getter](https://raw.githubusercontent.com/molon/MLAutoReplace/master/replaceGetter.gif)  

##How to install?
Download this project and run.  

##Re-Indent

Just can be quickly re-intent. 

If you find that press `Shift+Command+\` does nothing.   
Please ensure that the shortcut key setting of Re-Intent is default.
![re-intent shortcut key setting](https://raw.githubusercontent.com/molon/MLAutoReplace/master/re-intent-setting.png) 

##Regex replacer

Exmple:  
![replace getter](https://raw.githubusercontent.com/molon/MLAutoReplace/master/regex.png)  
This item means that plugin will replace `@s/` to `@property (nonatomic, strong) <#custom#>`.  


The plugin will detect the content of current input line.  

Some placeholder can be replace with context.

- `<datetime>`: current datetime, you can use it to mark your edit time.
- `<declare_class_below>`: the class name of the first `@interface XXX :` below.
- `<current_protocol>`: the protocol name in current line.

A demo for pseudo-generic:

![pseudo-generic](https://raw.githubusercontent.com/molon/MLAutoReplace/master/pseudo-generic.gif)


##Getter replacer

You need add your own common syntax to the getter replacer.  
![replace getter](https://raw.githubusercontent.com/molon/MLAutoReplace/master/addReplaceGetter.gif)  

`<name>` means the property name.  
`<#xxx#>` means where need to input in,it is recommended to provide.  

Exmple:

```
- (UIImageView *)<name>
{
    if (!_<name>) {
		UIImageView *imageView = [[UIImageView alloc]init];
        imageView.image = [UIImage imageNamed:@"<#imageName#>"];
        imageView.contentMode = UIViewContentModeScaleAspectFill;
        <#custom#>

        _<name> = imageView;
    }
    return _<name>;
}
```  
  
You must reload .plist file with shortcut `control+option+command+\` after editing and saving it.   
You can also reload it with the `Reload .plist Data` button in MLAutoReplace window.   

How to use:   
```
- (UIImageView *)xxx///
```   
Dont forget `///` please. :)
