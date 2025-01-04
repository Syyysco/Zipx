<p align="center">
  <img src="src/img/main_banner.png" width="400" alt="Zipx - An all-in-one tools to handle compression methods"><br>
  <img alt="GitHub Release" src="https://img.shields.io/github/v/release/:Syyysco/:Zipx?display_name=release&style=social&logoColor=0c0c0c&labelColor=0c0c0c&color=0c0c0c&link=https%3A%2F%2Fhola.com"><br>
  <img src="https://img.shields.io/badge/%20-bash-white?logo=zsh&logoColor=white&labelColor=2c2c2c" alt="Build on bash"></a>
  <img src="https://img.shields.io/badge/license-GPL-blue?logo=gnuprivacyguard" alt="license">
  <img src="https://img.shields.io/github/last-commit/Syyysco/Zipx?colorB=319e8c" alt="Last Commit">
  <img src="https://img.shields.io/badge/debian%20pkg-magenta?logo=debian&logoColor=red&label=&labelColor=gray&color=2c2c2c" alt="Available debian install package"><br><br>
  <i>Zipx</i> is a best zip de/compressor All-in-one.<br><br>
  <img src="src/img/profile-banner.png" width="50" alt="Sysco - A mad hardcoder"><br>
</p>

# Zipx Documentation

A professional command-line tool designed for **Linux systems** that unifies compression, decompression, and content listing for virtually all known archive formats. This tool simplifies handling multiple formats with a single interface, saving time and eliminating the need for separate tools.

---

## Table of Contents
- [Features](#features)
- [Supported Formats](#supported-formats)
- [Installation](#installation)
- [Build](#build)
- [Usage](#usage)
  - [Help Panel](#help-panel)
  - [Compress Files](#compress-files)
  - [Decompress Files](#decompress-files)
  - [List Archive Contents](#list-archive-contents)
- [Dependencies](#dependencies)
- [License](#license)

---

## Features

- **Unified interface:** Manage all supported formats with consistent commands.
- **Recursive decompression:** Automatically handles nested archives.
- **Selective listing:** Choose between direct or recursive archive content listings.
- **Custom compression formats:** Specify the desired format using a simple flag.
- **Error handling and feedback:** Clear error messages and return codes for seamless operation.

---

## Supported Formats

The tool supports a wide range of formats for compression and decompression:

| **Category**               | **Formats**                                      |
|----------------------------|--------------------------------------------------|
| **Common Formats**         | `tar`, `zip`, `gzip (gz)`, `bzip2 (bz2)`, `xz`   |
| **Compressed Tar Formats** | `tar.gz (tgz)`, `tar.bz2 (tbz2)`, `tar.xz`       |
| **Advanced Formats**       | `7z`, `rar`, `pax`, `pkg`                        |
| **Specialized Formats**    | `cab`, `lzma`, `lzip`                            |

<br>

> [!note]
> - Additional formats can be added as extensions via modular updates.
> - Ensure the required dependencies are installed for specific formats (e.g., `p7zip-full` for `.7z` files).

---

## Installation

> If you don't want to install `zipx` and just want to use it in a portable way you can follow one of the following alternatives:
> - Clone the repository and run it:
>   ```bash
>   git clone https://github.com/Syyysco/Zipx.git
>   cd Zipx
>   ./zipx -v
>   ```
>   
> - Download the portable binary from the releases page and then you can run it as follows:
>   ```bash
>   zipx -v
>   ```

### Prerequisites
- **Linux distribution**: Ubuntu, Debian, or any Linux system with `apt`.

### Steps to Install
1. Go to <a href="https://github.com/Syyysco/Zipx/releases">releases page</a> and download the __x64__ or __x86__ `.deb` file (depending on your platform, usually __x64__)
2. Install the package:
   ```bash
   sudo dpkg -i zipx_x64_1.0_20250201_linux.deb
   sudo apt install -f
   ```
   > The `.deb` file used in the example should be replaced with the name of the downloaded file.

<br>

> [!tip]
> ## Build
> If you want to compile the code because you have made some changes, go to the ["how to build"](src/docs/buildAppPackage.html) section of the repository.

<br>

---

## Usage

### Help Panel

To view the help panel, use:
```bash
zipx -h
```
This displays all available commands, flags, and info:
```ruby
Use: zipx [options] file

Options:
  -h, --help        Show this help panel
  -l, --less        Show the contents of the compressed file without extracting it
  -L, --less-tree   List the entire contents recursively in tree format
  -z, --zip         Compress the file or folder in the format specified with -f
  -x, --unzip       Decompress the file recursively until there are no more compressed files
  -q, --quiet       Run the program in silent mode without displaying output
  -o, --output      Specify an output file
  -f, --format      Compression format
                     ┕( tar tar.gz tgz tar.bz2 tbz2 tar.xz zip 7z gz bz2 xz rar pkg pax lzma lzip cab )
```

---

### Compress Files

To compress files or directories into a specific format, use:
```bash
zipx -z input_file -f tar.gz
```

#### Example:
Compress a directory:
```bash
zipx -z my_folder -f zip
```

---

### Decompress Files

To extract files from any supported archive:
```bash
zipx -x archive_file
```

#### Example:
Decompress a `.tar.gz` archive:
```bash
zipx -x archive.tar.gz
```

---

### List Archive Contents

#### Direct Content Listing
To list only the top-level contents of an archive:
```bash
zipx -l archive_file
```

#### Recursive Listing
To list all nested contents in a tree-like structure:
```bash
zipx -L archive_file
```

---

## Dependencies

> If you installed the `.deb` file and ran the commands in the [installation](#installation) section you should have all the dependencies installed.

The application requires the following tools for full functionality:

### Tabla: Dependencias, Funciones y Usos en la Aplicación

| **Dependence**      | **Function**                                                                                      | **Use on application**                                                                                        |
|---------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
| `tar`               | Compress and decompress files and folders in `tar`, `tar.gz`, `tar.bz2`, `tar.xz` formats         | Provides core functionality for `.tar`, `.tgz`, `.tbz2`, `.tar.xz` formats                                    |
| `gzip`              | Compress and decompress `.gz` files                                                               | Used to handle `gzip` compressed files                                                                        |
| `unzip`             | Extract `.zip` files                                                                              | Extract files and folders from `.zip` archives                                                                |
| `zip`               | Compress files and folders in `.zip` format                                                       | Facilitates the compression of files and folders in `.zip` format                                             |
| `lsd`               | List directory contents with colors and distinguish item types                                    | Used to display content in compressed directories in a visual and color-coded manner                          |
| `tree`              | Display recursive content in tree form                                                            | Displays hierarchy of compressed file contents                                                                |
| `p7zip-full`        | Handle compressed files in `.7z` format                                                           | Makes it easy to compress and decompress `.7z` files                                                          |
| `unrar`             | Extract `.rar` files                                                                              | Handles decompression of `.rar` files                                                                         |
| `rar`               | Compress files in `.rar` format                                                                   | Allows you to create compressed files in `.rar` format                                                        |
| `gcab`              | Compress and decompress `.cab` files                                                              | Used to create and extract `.cab` files                                                                       |
| `lzip`              | Compress and decompress `.lzip` files                                                             | Facilitates handling of compressed files with `lzip`                                                          |
| `xz-utils`          | Compress and decompress `.xz` files                                                               | Provides support for the `.xz` format                                                                         |
| `gzip`              | Decompress `.gz` files                                                                            | Allows you to handle `.gz` files                                                                              |
| `pax`               | Create and extract `.pax` files                                                                   | Facilitates handling of `pax` compressed files                                                                |
| `libarchive-tools`  | Handle multiple archive formats, including `.pkg` and `.pax`                                      | Unzip and manipulate files packed in various formats                                                          |

---

> #### **Example of use in compression:**
> ```bash
> case "$format" in
>     cab)
>         gcab -c "$output" "$input" &> /dev/null;;
> esac
> ```
> 
> #### **Example of use in decompression:**
> ```bash
> case $(file --mime-type -b "$file") in
>     application/vnd.ms-cab-compressed)
>         gcab -x "$file" -C "$temp_dir" &> /dev/null;;
> esac
> ```

### Automatically Install Missing Dependencies
If any dependencies are missing, the application prompts you to install them using `apt`:
```bash
sudo apt install -y <missing_tools>
```

---

## License
`zipx` is made available under the terms of either the [GNU General Public License (GPL)](LICENSE).  
You are free to use, modify, and distribute this project, provided you comply with the terms of the license.  
The full license details are available in the [LICENSE](LICENSE) file.

For more information about the GPL License, visit the [official GNU website](https://www.gnu.org/licenses/gpl-3.0.en.html).

<br>

---

<br>
<br>

<p align="center">
  <img src="src/img/profile-banner.png" width="50" alt="Sysco - A mad hardcoder"><br>
</p><br>
<br>
