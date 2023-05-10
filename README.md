# Oculus360

* Our main problem was that we read the pixels.txt file within the **XrCompositor_NativeActivity.c** while pixels.txt residing at the same directory. The problem with that is we assume that our machine is the runtime environment whereas the runtime environment is the Oculus itself, and by doing so, the Oculus cannot access the file since it is not in its memory.
* I tried to solve the previous problem by storing the pixels.txt file on the Oculus but this was not enough as the absolute path of Oculus is not clear and it also needed some permissions before it can open the file at runtime.
* So, instead, I just wrote the pixels on an array in a .h file and included this file in the **XrCompositor_NativeActivity.c** and end up putting this array on the texture.
* pixels.h contains the pixels of bg.png which is a 1024*512 image.
* pixels_1.h contains the pixels of nature.png which is a 1440*1080 image.
* The width and height variables at lines 1620 and 1621 of **XrCompositor_NativeActivity.c** should be set up properly to run the code.
* Please search in the **XrCompositor_NativeActivity.c** on "// ****" as this signature was added before every modification I have done (they are only 6).
* I think this runtime environment problem should be solved as it can helpful for us for testing and debugging. I wait an ok from you regarding my opinion.
