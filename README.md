## Smali2Dex
This is a tool that converts a Smali file or folder into a DEX format. It also includes the ability to execute a DEX file.

### Installation Instructions
- First, place the **bin/** directory in the Termux home directory.
- Make both files (**smali2dex** and **dex**) executable. For example, use "chmod +x bin/smali2dex".
- (Optional) You can copy these two files to the binary directory using "cp bin/smali2dex bin/dex $PREFIX/bin/".

### Testing Code
```smali
.class public LMain;
.super Ljava/lang/Object;
.source "Main"

.method public constructor <init>()V
    .registers 1

    .line 8
    invoke-direct {p0}, Ljava/lang/Object;-><init>()V

    return-void
.end method

.method public static main([Ljava/lang/String;)V
    .registers 3
    .annotation system Ldalvik/annotation/Signature;
        value = {
            "([",
            "Ljava/lang/String;",
            ")V"
        }
    .end annotation

    .line 6
    sget-object v0, Ljava/lang/System;->out:Ljava/io/PrintStream;

    const-string v1, "Hello World!"

    invoke-virtual {v0, v1}, Ljava/io/PrintStream;->println(Ljava/lang/String;)V

    return-void
.end method
```

### Converting Smali to Dex

***Note: The DEX file extension will be automatically added to the output file. For example, "output" will become "output.dex".***

```sh
smali2dex output -o Main.smali
```
***In this case, the output will be named "app.dex".***

```sh
smali2dex Main.smali
```

***Lastly, you can also convert multiple Smali files to DEX by specifying the parent folder.***

```sh
smali2dex folder-smali
```

### Executing Dex
```sh
dex output.dex
```

You can also add parameters to the DEX file execution.

```sh
dex output.dex param1 ...
```