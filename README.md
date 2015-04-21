
```
   ______                                                     __
  /\__  _\                                                   /\ \__
  \/_/\ \/    __    ____    ____     __   _ __    __      ___\ \ ,_\
     \ \ \  /'__`\ /',__\  /',__\  /'__`\/\`'__\/'__`\   /'___\ \ \/
      \ \ \/\  __//\__, `\/\__, `\/\  __/\ \ \//\ \L\.\_/\ \__/\ \ \_
       \ \_\ \____\/\____/\/\____/\ \____\\ \_\\ \__/.\_\ \____\\ \__\
        \/_/\/____/\/___/  \/___/  \/____/ \/_/ \/__/\/_/\/____/ \/__/

```

Want to tesseract your video? You've come to the right place, my friend.


# Quickstart

### Install it

```
gem install video_tesseract
```

### Run it

```
video-tesseract -i my-video.mp4 -g 5x5 -s 320x180 -o tesseract.mp4
```

This will take your video (`my-video.mp4`) and tesseract it into a 5x5 grid where
each tile is 320x180. The output video will be saved as `tesseract.mp4`.


# How it works

This script takes the original video and generates a new "tesseracted" video
in which the entire timeline of the original video is laid out in two dimensional
space. It's kind of hard to describe in words. You should just take a look at
the demo here: http://videotesseract.com

Here's what the script actually does:

1. Extract every frame of the original video as a png.
2. Tile some of these frames into a single montage image. This montage is a
   single frame in the final tesseracted video.
3. Keep repeating step 2 with new frames from the original video until we've
   generated every frame we need for the tesseracted video.
4. Compile the montage frames into the final tesseracted video.


# Requirements

- Ruby 1.9+
- OSX or Linux (haven't tested on Windows, sorry)
- **FFmpeg** – We use FFmpeg extracts the frames from the video and compiles
  the montages into the final tesseracted video.
- **ImageMagick** – We use this to stitch together the frames from the original
  into montages for each frame of the tesseracted video.

On OSX:

```
brew install ffmpeg
brew install imagemagick
```


# Building the gem

This is mostly a note to self.

1. Bump the version in the gemspec, commit it, push it.
2. Git tag it: `git tag -a 0.1.0 -m 'Version 0.1.0'` and `git push origin 0.1.0`
2. Build it: `gem build video_tesseract.gemspec`
3. Ship it: `gem push video_tesseract-0.1.0.gem`


# MIT License

Copyright (C) 2015 Wistia, Inc.

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
