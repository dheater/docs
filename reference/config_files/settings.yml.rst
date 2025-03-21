.. _settings_yml:

settings.yml
============

The input ``settings`` for packages in Conan are predefined in ``~/.conan/settings.yml`` file, so only a few like ``os`` or ``compiler``
are possible. These are the **default** values, but it is possible to customize them, see :ref:`custom_settings`.

.. code-block:: yaml

    # Only for cross building, 'os_build/arch_build' is the system that runs Conan
    os_build: [Windows, WindowsStore, Linux, Macos, FreeBSD, SunOS, AIX]
    arch_build: [x86, x86_64, ppc32be, ppc32, ppc64le, ppc64, armv5el, armv5hf, armv6, armv7, armv7hf, armv7s, armv7k, armv8, armv8_32, armv8.3, sparc, sparcv9, mips, mips64, avr, s390, s390x, sh4le, e2k-v2, e2k-v3, e2k-v4, e2k-v5, e2k-v6, e2k-v7]

    # Only for building cross compilation tools, 'os_target/arch_target' is the system for
    # which the tools generate code
    os_target: [Windows, Linux, Macos, Android, iOS, watchOS, tvOS, FreeBSD, SunOS, AIX, Arduino, Neutrino]
    arch_target: [x86, x86_64, ppc32be, ppc32, ppc64le, ppc64, armv5el, armv5hf, armv6, armv7, armv7hf, armv7s, armv7k, armv8, armv8_32, armv8.3, sparc, sparcv9, mips, mips64, avr, s390, s390x, asm.js, wasm, sh4le, e2k-v2, e2k-v3, e2k-v4, e2k-v5, e2k-v6, e2k-v7]

    # Rest of the settings are "host" settings:
    # - For native building/cross building: Where the library/program will run.
    # - For building cross compilation tools: Where the cross compiler will run.
    os:
        Windows:
            subsystem: [None, cygwin, msys, msys2, wsl]
        WindowsStore:
            version: ["8.1", "10.0"]
        WindowsCE:
            platform: ANY
            version: ["5.0", "6.0", "7.0", "8.0"]
        Linux:
        Macos:
            version: [None, "10.6", "10.7", "10.8", "10.9", "10.10", "10.11", "10.12", "10.13", "10.14", "10.15", "11.0"]
            sdk: [None, "macosx"]
            subsystem: [None, catalyst]
        Android:
            api_level: ANY
        iOS:
            version: ["7.0", "7.1", "8.0", "8.1", "8.2", "8.3", "9.0", "9.1", "9.2", "9.3", "10.0", "10.1", "10.2", "10.3", "11.0", "11.1", "11.2", "11.3", "11.4", "12.0", "12.1", "12.2", "12.3", "12.4", "13.0", "13.1", "13.2", "13.3", "13.4", "13.5", "13.6"]
            sdk: [None, "iphoneos", "iphonesimulator"]
        watchOS:
            version: ["4.0", "4.1", "4.2", "4.3", "5.0", "5.1", "5.2", "5.3", "6.0", "6.1"]
            sdk: [None, "watchos", "watchsimulator"]
        tvOS:
            version: ["11.0", "11.1", "11.2", "11.3", "11.4", "12.0", "12.1", "12.2", "12.3", "12.4", "13.0"]
            sdk: [None, "appletvos", "appletvsimulator"]
        FreeBSD:
        SunOS:
        AIX:
        Arduino:
            board: ANY
        Emscripten:
        Neutrino:
            version: ["6.4", "6.5", "6.6", "7.0"]
    arch: [x86, x86_64, ppc32be, ppc32, ppc64le, ppc64, armv4, armv4i, armv5el, armv5hf, armv6, armv7, armv7hf, armv7s, armv7k, armv8, armv8_32, armv8.3, sparc, sparcv9, mips, mips64, avr, s390, s390x, asm.js, wasm, sh4le, e2k-v2, e2k-v3, e2k-v4, e2k-v5, e2k-v6, e2k-v7]
    compiler:
        sun-cc:
            version: ["5.10", "5.11", "5.12", "5.13", "5.14"]
            threads: [None, posix]
            libcxx: [libCstd, libstdcxx, libstlport, libstdc++]
        gcc: &gcc
            version: ["4.1", "4.4", "4.5", "4.6", "4.7", "4.8", "4.9",
                      "5", "5.1", "5.2", "5.3", "5.4", "5.5",
                      "6", "6.1", "6.2", "6.3", "6.4", "6.5",
                      "7", "7.1", "7.2", "7.3", "7.4", "7.5",
                      "8", "8.1", "8.2", "8.3", "8.4",
                      "9", "9.1", "9.2", "9.3",
                      "10", "10.1"]
            libcxx: [libstdc++, libstdc++11]
            threads: [None, posix, win32] #  Windows MinGW
            exception: [None, dwarf2, sjlj, seh] # Windows MinGW
            cppstd: [None, 98, gnu98, 11, gnu11, 14, gnu14, 17, gnu17, 20, gnu20]
        Visual Studio: &visual_studio
            runtime: [MD, MT, MTd, MDd]
            version: ["8", "9", "10", "11", "12", "14", "15", "16"]
            toolset: [None, v90, v100, v110, v110_xp, v120, v120_xp,
                      v140, v140_xp, v140_clang_c2, LLVM-vs2012, LLVM-vs2012_xp,
                      LLVM-vs2013, LLVM-vs2013_xp, LLVM-vs2014, LLVM-vs2014_xp,
                      LLVM-vs2017, LLVM-vs2017_xp, v141, v141_xp, v141_clang_c2, v142,
                      llvm, ClangCL]
            cppstd: [None, 14, 17, 20]
         msvc:
            version: ["19.0",
                      "19.1", "19.10", "19.11", "19.12", "19.13", "19.14", "19.15", "19.16",
                      "19.2", "19.20", "19.21", "19.22", "19.23", "19.24", "19.25", "19.26", "19.27", "19.28"]
            runtime: [static, dynamic]
            runtime_type: [Debug, Release]
            cppstd: [14, 17, 20]
        clang:
            version: ["3.3", "3.4", "3.5", "3.6", "3.7", "3.8", "3.9", "4.0",
                      "5.0", "6.0", "7.0", "7.1",
                      "8", "9", "10", "11", "12", "13"]
            libcxx: [None, libstdc++, libstdc++11, libc++, c++_shared, c++_static]
            cppstd: [None, 98, gnu98, 11, gnu11, 14, gnu14, 17, gnu17, 20, gnu20]
            runtime: [None, MD, MT, MTd, MDd]
        apple-clang: &apple_clang
            version: ["5.0", "5.1", "6.0", "6.1", "7.0", "7.3", "8.0", "8.1", "9.0", "9.1", "10.0", "11.0", "12.0"]
            libcxx: [libstdc++, libc++]
            cppstd: [None, 98, gnu98, 11, gnu11, 14, gnu14, 17, gnu17, 20, gnu20]
        intel:
            version: ["11", "12", "13", "14", "15", "16", "17", "18", "19"]
            base:
                gcc:
                    <<: *gcc
                    threads: [None]
                    exception: [None]
                Visual Studio:
                    <<: *visual_studio
                apple-clang:
                    <<: *apple_clang
        qcc:
            version: ["4.4", "5.4"]
            libcxx: [cxx, gpp, cpp, cpp-ne, accp, acpp-ne, ecpp, ecpp-ne]
        mcst-lcc:
            version: ["1.19", "1.20", "1.21", "1.22", "1.23", "1.24", "1.25"]
            base:
                gcc:
                    <<: *gcc
                    threads: [None]
                    exceptions: [None]

    build_type: [None, Debug, Release, RelWithDebInfo, MinSizeRel]
    cppstd: [None, 98, gnu98, 11, gnu11, 14, gnu14, 17, gnu17, 20, gnu20]  # Deprecated, use compiler.cppstd


As you can see, the possible values ``settings`` can take are restricted in the same file. This is done to ensure matching naming and
spelling as well as defining a common settings model among users and the OSS community.
If a setting is allowed to be set to any value, you can use ``ANY``.
If a setting is allowed to be set to any value or it can also be unset, you can use ``[None, ANY]``.

However, this configuration file can be modified to any needs, including new settings or subsettings and their values. If you want
to distribute a unified *settings.yml* file you can use the :ref:`conan config install command<conan_config_install>`.

.. note::

    The *settings.yml* file is not perfect nor definitive and surely incomplete. Please share any suggestion in the Conan issue tracker
    with any missing settings and values that could make sense for other users.

    To force the creation of the *settings.yml* the command ``conan config init`` is available.

Compilers
---------

Some notes about different compilers:

msvc
++++

The new ``msvc`` compiler is a new, **experimental** one, that is intended to deprecate the ``Visual Studio`` one in Conan 2.0:

- It uses the compiler version, that is 19.0, 19.1, etc, instead of the Visual Studio IDE (15, 16, etc).
- It is only used by the new build integrations in :ref:`conan_tools_cmake` and :ref:`conan_tools_microsoft`, but not the previous ones.
- At the moment it implements a ``compatible_packages`` fallback to Visual Studio compiled packages, that is, previous existing binaries
  compiled with ``settings.compiler="Visual Studio"`` can be used for the ``msvc`` compiler if no binaries exist for it yet.
  This behavior can be opted-out with ``core.package_id:msvc_visual_incompatible`` :ref:`global_conf` configuration.
- It is not detected by the profile auto-detect, it needs to explicitly be defined in profiles.

When using the ``msvc`` compiler, the Visual Studio toolset version (the actual ``vcvars`` activation and ``MSBuild`` location) will be
defined by the default provide of that compiler version:

- ``msvc`` compiler version '19.0': Visual Studio 14 2015
- ``msvc`` compiler version '19.1': Visual Studio 15 2017
- ``msvc`` compiler version '19.2': Visual Studio 16 2019

This can be configured in your profiles with the ``tools.microsoft.msbuild:vs_version`` configuration:

.. code-block:: text

    [settings]
    compiler=msvc
    compiler.version=19.0

    [conf]
    tools.microsoft.msbuild:vs_version = 16


In this case, the ``vcvars`` will activate the Visual Studio 16 installation, but the ``19.0`` compiler version will still be used
because the necessary ``toolset=v140`` will be set.


clang
+++++

The release 13.0.0 will be released officially on September 21, 2021. However, Conan 1.40 will support it in settings.yml before
the final release. It will be considered as **experimental** in case of incompatibility until the release.


Architectures
-------------

Here you can find a brief explanation of each of the architectures defined as ``arch``, ``arch_build`` and ``arch_target`` settings.

- **x86**: The popular 32 bit x86 architecture.

- **x86_64**: The popular 64 bit x64 architecture.

- **ppc64le**: The PowerPC 64 bit Big Endian architecture.

- **ppc32**: The PowerPC 32 bit architecture.

- **ppc64le**: The PowerPC 64 bit Little Endian architecture.

- **ppc64**: The PowerPC 64 bit Big Endian architecture.

- **armv5el**: The ARM 32 bit version 5 architecture, soft-float.

- **armv5hf**: The ARM 32 bit version 5 architecture, hard-float.

- **armv6**: The ARM 32 bit version 6 architecture.

- **armv7**: The ARM 32 bit version 7 architecture.

- **armv7hf**: The ARM 32 bit version 7 hard-float architecture.

- **armv7s**: The ARM 32 bit version 7 *swift* architecture mostly used in Apple's A6 and A6X chips on iPhone 5, iPhone 5C and iPad 4.

- **armv7k**: The ARM 32 bit version 7 *k* architecture mostly used in Apple's WatchOS.

- **armv8**: The ARM 64 bit and 32 bit compatible version 8 architecture. It covers only the ``aarch64`` instruction set.

- **armv8_32**: The ARM 32 bit version 8 architecture. It covers only the ``aarch32`` instruction set (a.k.a. ``ILP32``).

- **armv8.3**: The ARM 64 bit and 32 bit compatible version 8.3 architecture. Also known as ``arm64e``, it is used on the A12 chipset added
  in the latest iPhone models (XS/XS Max/XR).

- **sparc**: The SPARC (Scalable Processor Architecture) originally developed by Sun Microsystems.

- **sparcv9**: The SPARC version 9 architecture.

- **mips**: The 32 bit MIPS (Microprocessor without Interlocked Pipelined Stages) developed by MIPS Technologies (formerly MIPS Computer
  Systems).

- **mips64**: The 64 bit MIPS (Microprocessor without Interlocked Pipelined Stages) developed by MIPS Technologies (formerly MIPS Computer
  Systems).

- **avr**: The 8 bit AVR microcontroller architecture developed by Atmel (Microchip Technology).

- **s390**: The 32 bit address Enterprise Systems Architecture 390 from IBM.

- **s390x**: The 64 bit address Enterprise Systems Architecture 390 from IBM.

- **asm.js**: The subset of JavaScript that can be used as low-level target for compilers, not really a processor architecture, it's produced
  by Emscripten. Conan treats it as an architecture to align with build systems design (e.g. GNU auto tools and CMake).

- **wasm**: The Web Assembly, not really a processor architecture, but byte-code format for Web, it's produced by Emscripten. Conan treats it
  as an architecture to align with build systems design (e.g. GNU auto tools and CMake).

- **sh4le**: The Hitachi SH-4 SuperH architecture.

- **e2k-v2**: The Elbrus 2000 v2 512 bit VLIW (Very Long Instruction Word) architecture (Elbrus 2CM, Elbrus 2C+ CPUs) originally developed by MCST (Moscow Center of SPARC Technologies).

- **e2k-v3**: The Elbrus 2000 v3 512 bit VLIW (Very Long Instruction Word) architecture (Elbrus 2S, aka Elbrus 4C, CPU) originally developed by MCST (Moscow Center of SPARC Technologies).

- **e2k-v4**: The Elbrus 2000 v4 512 bit VLIW (Very Long Instruction Word) architecture (Elbrus 8C, Elbrus 8C1, Elbrus 1C+ and Elbrus 1CK CPUs) originally developed by MCST (Moscow Center of SPARC Technologies).

- **e2k-v5**: The Elbrus 2000 v5 512 bit VLIW (Very Long Instruction Word) architecture (Elbrus 8C2 ,aka Elbrus 8CB, CPU) originally developed by MCST (Moscow Center of SPARC Technologies).

- **e2k-v6**: The Elbrus 2000 v6 512 bit VLIW (Very Long Instruction Word) architecture (Elbrus 2C3, Elbrus 12C and Elbrus 16C CPUs) originally developed by MCST (Moscow Center of SPARC Technologies).

- **e2k-v7**: The Elbrus 2000 v7 512 bit VLIW (Very Long Instruction Word) architecture (Elbrus 32C CPU) originally developed by MCST (Moscow Center of SPARC Technologies).


C++ standard libraries (aka compiler.libcxx)
--------------------------------------------

``compiler.libcxx`` sub-setting defines C++ standard libraries implementation to be used. The sub-setting applies only to certain compilers,
e.g. it applies to *clang*, *apple-clang* and *gcc*, but doesn't apply to *Visual Studio*.

- **libstdc++** (gcc, clang, apple-clang, sun-cc): `The GNU C++ Library <https://gcc.gnu.org/onlinedocs/libstdc++/>`__. NOTE that this implicitly
  defines **_GLIBCXX_USE_CXX11_ABI=0** to use old ABI. See :ref:`How to manage the GCC >= 5 ABI <manage_gcc_abi>` for the additional details. Might
  be a wise choice for old systems, such as CentOS 6. On Linux systems, you may need to install `libstdc++-dev <https://packages.debian.org/sid/libstdc++-dev>`_
  (package name could be different in various distros) in order to use the standard library. NOTE that on Apple systems usage of **libstdc++** has been deprecated.

- **libstdc++11** (gcc, clang, apple-clang): `The GNU C++ Library <https://gcc.gnu.org/onlinedocs/libstdc++/>`__. NOTE that this implicitly
  defines **_GLIBCXX_USE_CXX11_ABI=1** to use new ABI. See :ref:`How to manage the GCC >= 5 ABI <manage_gcc_abi>` for the additional details. Might
  be a wise choice for newer systems, such as Ubuntu 20. On Linux systems, you may need to install `libstdc++-dev <https://packages.debian.org/sid/libstdc++-dev>`_
  (package name could be different in various distros) in order to use the standard library. NOTE that on Apple systems usage of **libstdc++** has been deprecated.

- **libc++** (clang, apple-clang): `LLVM libc++ <https://libcxx.llvm.org/>`__. On Linux systems, you may need to install `libc++-dev <https://packages.debian.org/sid/libc++-dev>`_
  (package name could be different in various distros) in order to use the standard library.

- **c++_shared** (clang, Android only): use `LLVM libc++ <https://libcxx.llvm.org/>`__ as a shared library. Refer to the `C++ Library Support <https://developer.android.com/ndk/guides/cpp-support>`__ for the
  additiona details.

- **c++_static** (clang, Android only): use `LLVM libc++ <https://libcxx.llvm.org/>`__ as a static library. Refer to the `C++ Library Support <https://developer.android.com/ndk/guides/cpp-support>`__ for the
  additiona details.

- **libCstd** (sun-cc): Rogue Wave's stdlib. See `Comparing C++ Standard Libraries libCstd, libstlport, and libstdcxx <https://www.oracle.com/solaris/technologies/cmp-stlport-libcstd.html>`__.

- **libstlport** (sun-cc): `STLport <http://www.stlport.org/>`__. See `Comparing C++ Standard Libraries libCstd, libstlport, and libstdcxx <https://www.oracle.com/solaris/technologies/cmp-stlport-libcstd.html>`__.

- **libstdcxx** (sun-cc): `Apache C++ Standard Library <http://people.apache.org/~gmcdonald/stdcxx/index.html>`__. See `Comparing C++ Standard Libraries libCstd, libstlport, and libstdcxx <https://www.oracle.com/solaris/technologies/cmp-stlport-libcstd.html>`__.

- **gpp** (qcc): GNU C++ lib. See `QCC documentation <https://www.qnx.com/developers/docs/6.5.0SP1.update/com.qnx.doc.neutrino_utilities/q/qcc.html>`__.

- **cpp** (qcc): Dinkum C++ lib. See `QCC documentation <https://www.qnx.com/developers/docs/6.5.0SP1.update/com.qnx.doc.neutrino_utilities/q/qcc.html>`__.

- **cpp-ne** (qcc): Dinkum C++ lib (no exceptions). See `QCC documentation <https://www.qnx.com/developers/docs/6.5.0SP1.update/com.qnx.doc.neutrino_utilities/q/qcc.html>`__.

- **acpp** (qcc): Dinkum Abridged C++ lib. See `QCC documentation <https://www.qnx.com/developers/docs/6.5.0SP1.update/com.qnx.doc.neutrino_utilities/q/qcc.html>`__.

- **acpp-ne** (qcc): Dinkum Abridged C++ lib (no exceptions). See `QCC documentation <https://www.qnx.com/developers/docs/6.5.0SP1.update/com.qnx.doc.neutrino_utilities/q/qcc.html>`__.

- **ecpp** (qcc): Embedded Dinkum C++ lib. See `QCC documentation <https://www.qnx.com/developers/docs/6.5.0SP1.update/com.qnx.doc.neutrino_utilities/q/qcc.html>`__.

- **ecpp-ne** (qcc): Embedded Dinkum C++ lib (no exceptions). See `QCC documentation <https://www.qnx.com/developers/docs/6.5.0SP1.update/com.qnx.doc.neutrino_utilities/q/qcc.html>`__.

- **cxx** (qcc): LLVM C++. See `QCC documentation <https://www.qnx.com/developers/docs/6.5.0SP1.update/com.qnx.doc.neutrino_utilities/q/qcc.html>`__.
