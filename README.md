# DivertPInvoke
PInvoke wrapper for [WinDivert](https://github.com/basil00/Divert).  
  
Be mindful of the fact that the source file(s) in this repo are LGPLv3. Make sure you comply with this license (which is the same license as WinDivert).

This class will append two directories to the env vars of the executing application. It will append `EXE\x86` and `EXE\x64`. This way, you can drop the WinDivert native executables in arch-specific directories next to your deployed application and keep using AnyCPU, and thanks to this little trick, the .NET assembly resolver will load the proper WinDivert native libraries.

Note that network to host and host to network order conversion is provided transparently by the structures defined here. In WinDivert, this is not the case obviously, but because we have the syntactic sugar to do this, it's done in this wrapper. For example, you can simply read or write the `DstPort` of a TCP packet to `80` like `x.DstPort = 80` or `x.DstPort == 80`, and all necessary order swapping is done under the hood.
