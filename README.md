<div align = center>

<img src="https://i.imgur.com/YCRSuSV.png" alt="banner">

</div>

* A fork of modern version of Code Virtualizer SDK for Go
* All right are reserved by [Oreans.com](https://www.oreans.com)

# Introduction
Code Virtualizer is a powerful code obfuscation system for Windows applications that helps developers to protect their sensitive code areas against Reverse Engineering with very strong obfuscation code, based on code virtualization.

Code Virtualizer will convert your original code (Intel x86/x64 instructions) into Virtual Opcodes that will only be understood by an internal Virtual Machine. Those Virtual Opcodes and the Virtual Machine itself are unique for every protected application, avoiding a general attack over Code Virtualizer.

Code Virtualizer can protect your sensitive code areas in any x86 and x64 native PE/ELF/Mach-O files (like executable files/EXEs, system services, DLLs , OCXs , ActiveX controls, shared objects, screen savers and device drivers).

<div align = center>

<img src="https://www.oreans.com/assets/images/figure_final.jpg" alt="banner">

</div>


# Example
```go
package main

import (
	"fmt"
	"github.com/orange-cpp/virtualizersdk-redux/v2"
)

var stealth_area = [virtualizersdk.STEALTH_ONE_MB * 6]uint32{
	virtualizersdk.STEALTH_ARRAY_FLAG1,
	virtualizersdk.STEALTH_ARRAY_FLAG2,
	virtualizersdk.STEALTH_ARRAY_FLAG3,
	virtualizersdk.STEALTH_ARRAY_FLAG4,
	virtualizersdk.STEALTH_ARRAY_FLAG5,
	virtualizersdk.STEALTH_ARRAY_FLAG6,
	virtualizersdk.STEALTH_ARRAY_FLAG7,
	virtualizersdk.STEALTH_ARRAY_FLAG8}

func main() {
	virtualizersdk.Macro(virtualizersdk.SHARK_BLACK_START)


    // Force compiler to NOT delete array 
    // if it unused.
	if stealth_area[0] == 0x11111 {
		fmt.Println(stealth_area[0])
	}

	fmt.Println("Hello World!")

	virtualizersdk.Macro(virtualizersdk.SHARK_BLACK_END)
}

```