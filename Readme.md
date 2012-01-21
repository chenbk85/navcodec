
Node libavcodec bindings
=

*navcodec* is a module that aims to provide a node wrapper for the excellent [libavcodec](http://libav.org) library. The module does not aim to make a 1 to 1 mapping between this library and javascript. Instead the aim is to create a new javascript API inspired by the underlying library that is more javascript oriented and easier to use.

The initial priority will be to make the transcoding use case, and later move to other uses cases such as playing, filtering, editing, etc.

Simple example:

	navcodec = require('navcodec');

	options = {
		width:640,
		height:480,
		bit_rate_audio:128000,
		bit_rate_video:500000
	}

	navcodec.transcode('myinput.mov', 'myoutput.mp4', options, function(progress){
		console.log(progress);
	});

This will transcode myinput.mov into myoutput.mp4 according to the given options. The callback will be called with a progress variable between 0 and 1.

We will be adding more options soon, to allow more flexibility.

Since the transcode uses mostly *libavcodec* optimized functions, the above example will run really fast.

Install
-

navcodec depends on [libavcodec](http://libav.org), and this library
must be installed before you can install this module using npm. 

The library has been tested with libavcodec version 0.7.4 and 0.8 beta 2.

For most unixes there are packages available, in ubuntu for example use *libavcodec-dev*. If you want you can also compile the source code with your preferred settings, this can be useful if you want to get the maximum performance from the library.

For Mac OSX use brew and install the ffmpeg package.

	brew install ffmpeg

When the libavcodec dependencies are fulfilled, just use npm to install the package:

	npm install navcodec


  
Compiling libavcodec
-

- Download the latest stable 0.7 release from [libav.org](http://libav.org/download.html#release_0.7)

- Uncompress the tarball, Ex:
  
	tar -xvf libav-0.7.4.tar.gz
	cd libav-0.7.4
  
- Configure your makefile, example:

		./configure  --prefix=/usr/local --enable-shared --enable-gpl --enable-version3 --enable-nonfree --enable-hardcoded-tables --cc=/usr/bin/clang --enable-libfaac --enable-libmp3lame --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libxvid
  
you can get a list of other configuration options using:

	./configure --help
  
- Compile the libraries:

		make
  
- Install


		make install

Todo
-

- Make Asynchronous.
- Add Progress support.
- Fix Memory Leaks.

License
-

Copyright(c) 2012 Optimal Bits Sweden AB. All rights reserved.
 
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to
deal in the Software without restriction, including without limitation the
rights to use, copy, modify, merge, publish, distribute, sublicense, and/or
sell copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS
IN THE SOFTWARE.
 

