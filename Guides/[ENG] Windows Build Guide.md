# Windows Build Guide [ENG]

This is a guide to compile your version of the ShashChess Engine using mingw.

ShashChess is GUI independent and it can work in the termina, but it's UCI (Universal Chess Interface), which means it's compatible with most GUIs (e.g. Arena, CuteChess, etc)

### Step 1:

Download and install MSYS2 from the [official website](https://www.msys2.org). 

While installing, change the installation directory to C:\tools\msys64

### Step 2:

Launch MSYS2 (either 64-bit or 32-bit, based on your configuration).

Run the following command in the terminal:

```powershell
pacman -Syuu --noconfirm --needed --disable-download-timeout
```

(Keep running this command even if the MSYS2 window closes automatically, until you see that all packages are showing the message "xxx is up to date")

Then, run the following command:

```powershell
pacman -S --noconfirm --needed --disable-download-timeout unzip make mingw-w64-x86_64-gcc mingw-w64-x86_64-toolchain mingw-w64-i686-gcc mingw-w64-i686-toolchain mingw-w64-x86_64-clang
```

At this point you can already compile ShashChess, because it does not require CURL. 

If you need CURL you can install it following the next step (marked with the CURL tag), otherwise skip it.

### Step 3 [CURL]:

Launch MSYS2 (either 64-bit or 32-bit, based on your configuration).

Run the following command:

```powershell
pacman -S --noconfirm --needed --disable-download-timeout mingw-w64-x86_64-curl mingw-w64-i686-curl
```

Then, you'll need to run a series of three commands, which vary based on wheter you are using the 64-bit version or the 32-bit.

##### 64-bit:

```powershell
pacman -S mingw-w64-x86_64-ca-certificates
```

```powershell
pacman -S mingw-w64-x86_64-openssl
```

```powershell
pacman -S mingw-w64-x86_64-curl-winssl 
```

##### 32-bit:

```powershell
pacman -S mingw-w64-i686-ca-certificates 
```

```powershell
pacman -S mingw-w64-i686-openssl 
```

```powershell
pacman -S mingw-w64-i686-curl-winssl
```

Here the guide goes back to being the same for 64-bit and 32-bit.

Modify your Makefile near the line 397 to the following:

```makefile
LDFLAGS += -DUSE_LIVEBOOK -lcurl -lnghttp2 -lnghttp3 -lidn2 -lssh2 -lssh2 -lpsl -lbcrypt -ladvapi32 -lcrypt32 -lbcrypt -lssl -lcrypto -lssl -lcrypto -lgdi32 -lwldap32 -lzstd -lzstd -lbrotlidec -lz -lws2_32 -lidn2 -liconv -lunistring -lbrotlidec -lbrotlicommon –static
```

You can now compile both versions.

### Step 4:

Before you create a new release, run the following command from MSYS2 (both 64-bit and 32-bit):

```powershell
pacman -Syuu --noconfirm --needed --disable-download-timeout
```

This will upgrade MSYS2 and all installed packages (including compilers). 

Keep running this command even if the window closes on its own, until you see the message "xxx is up to date" for all packages.

### Step 5:

If you still have problems, run:

```powershell
pacman -Syu 
```

### Step 6:

To compile run this command (inside MSYS shell):

```powershell
make -j profile-build ARCH=x86-64
```
