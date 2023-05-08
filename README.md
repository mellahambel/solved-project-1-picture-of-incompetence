Download Link: https://assignmentchef.com/product/solved-project-1-picture-of-incompetence
<br>
<h1>“Uh oh…”</h1>

Jonah Ryan has just spilled a jug of Lysol mixed with vodka all over the latest publicity photos of Selina Meyer and her team! Some dangerous chemicals must have been in the photos because they’re doing all kinds of strange things: stretching, shrinking, turning bizarre colors. As the only computer scientist working for the Vice President, you must put it all right.

<h2>The Mission</h2>

In order to reconstruct the images, we need you to write a program that can read in a bitmap file and perform a sequence of modifications consisting of the following seven operations, depending on the commands given by the user.




<table class="shaded">

 <tbody>

  <tr>

   <th>User Command</th>

   <th>Operation</th>

   <th>Example</th>

  </tr>

  <tr>

   <td>i</td>

   <td>Invert the colors of the bitmap. If the original color of a pixel was (R, G, B), the new color value should be (255 – R, 255 – G, 255 – B).</td>

   <td><img decoding="async" alt="Invert Example" data-recalc-dims="1" data-src="https://i0.wp.com/users.etown.edu/w/wittmanb/cs221/projects/images/invert.png?w=980" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

    <noscript>

     <img decoding="async" src="https://i0.wp.com/users.etown.edu/w/wittmanb/cs221/projects/images/invert.png?w=980" alt="Invert Example" data-recalc-dims="1">

    </noscript></td>

  </tr>

  <tr>

   <td>g</td>

   <td>Make the image grayscale. Set the R, G, and B values for a single pixel to one value. That value should be: .3R + .59G + .11B, <strong>rounded</strong> to the nearest integer.Note that when the red, green and blue components are all the same, the color is a shade of gray. For example (0,0,0) is black, (255, 255, 255) is white, and (128, 128, 128) is a 50% gray.</td>

   <td><img decoding="async" alt="Grayscale Example" data-recalc-dims="1" data-src="https://i0.wp.com/users.etown.edu/w/wittmanb/cs221/projects/images/grayscale.png?w=980" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

    <noscript>

     <img decoding="async" src="https://i0.wp.com/users.etown.edu/w/wittmanb/cs221/projects/images/grayscale.png?w=980" alt="Grayscale Example" data-recalc-dims="1">

    </noscript></td>

  </tr>

  <tr>

   <td>b</td>

   <td>Blur the image. For each pixel, make each of its color components the weighted average of all the pixels in a two pixel radius, <strong>rounding</strong> to the nearest integer.For a normal pixel, doing so means adding up the color values for a 5 × 5 square of 25 pixels. (Two rows above and below, two columns to the left and to the right.) The red, green, and blue sums should each be divided by 25.Of course, any pixels which are close to an edge should only average pixels that are part of the image. Thus, a corner pixel will generally be the average of a 3 × 3 square of pixels. (Two rows down and two columns to the right only.) Clever use of loops and counting the number of pixels summed can take care of these edge cases without too much additional code.</td>

   <td><img decoding="async" alt="Blur Example" data-recalc-dims="1" data-src="https://i0.wp.com/users.etown.edu/w/wittmanb/cs221/projects/images/blur.png?w=980" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

    <noscript>

     <img decoding="async" src="https://i0.wp.com/users.etown.edu/w/wittmanb/cs221/projects/images/blur.png?w=980" alt="Blur Example" data-recalc-dims="1">

    </noscript></td>

  </tr>

  <tr>

   <td>v</td>

   <td>Vertically mirror the bitmap. Flip the pixels of the bitmap around the <em>x</em>-axis.</td>

   <td><img decoding="async" alt="Vertical Mirror Example" data-recalc-dims="1" data-src="https://i0.wp.com/users.etown.edu/w/wittmanb/cs221/projects/images/vertical.png?w=980" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

    <noscript>

     <img decoding="async" src="https://i0.wp.com/users.etown.edu/w/wittmanb/cs221/projects/images/vertical.png?w=980" alt="Vertical Mirror Example" data-recalc-dims="1">

    </noscript></td>

  </tr>

  <tr>

   <td>s</td>

   <td>Shrink the bitmap to half its size in both height and width directions. Because the bitmap will cover 1/4 the area that it did before, you will have to average the color values for four pixels into color values for one pixel. Averaging should be done by converting the values to floating point values, averaging them together, and <strong>rounding</strong> to the nearest integer.If either the height or width of the image are not even, ignore the last row or column that makes the image odd.</td>

   <td><img decoding="async" alt="Shrink Example" data-recalc-dims="1" data-src="https://i0.wp.com/users.etown.edu/w/wittmanb/cs221/projects/images/shrink.png?w=980" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

    <noscript>

     <img decoding="async" src="https://i0.wp.com/users.etown.edu/w/wittmanb/cs221/projects/images/shrink.png?w=980" alt="Shrink Example" data-recalc-dims="1">

    </noscript></td>

  </tr>

  <tr>

   <td>d</td>

   <td>Double the size of the bitmap in both height and width directions. You will have to make four pixels have the same color values as one pixel did in the original.</td>

   <td><img decoding="async" alt="Double Example" data-recalc-dims="1" data-src="https://i0.wp.com/users.etown.edu/w/wittmanb/cs221/projects/images/double.png?w=980" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

    <noscript>

     <img decoding="async" src="https://i0.wp.com/users.etown.edu/w/wittmanb/cs221/projects/images/double.png?w=980" alt="Double Example" data-recalc-dims="1">

    </noscript></td>

  </tr>

  <tr>

   <td>r</td>

   <td>Rotate the image 90 degrees to the left (counter-clockwise).</td>

   <td><img decoding="async" alt="Rotate Example" data-recalc-dims="1" data-src="https://i0.wp.com/users.etown.edu/w/wittmanb/cs221/projects/images/rotate.png?w=980" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

    <noscript>

     <img decoding="async" src="https://i0.wp.com/users.etown.edu/w/wittmanb/cs221/projects/images/rotate.png?w=980" alt="Rotate Example" data-recalc-dims="1">

    </noscript></td>

  </tr>

 </tbody>

</table>




If you are in a 3 person group, you have to do the following extra operations:

<table class="shaded">

 <tbody>

  <tr>

   <th>User Command</th>

   <th>Operation</th>

   <th>Example</th>

  </tr>

  <tr>

   <td>m</td>

   <td>Perform a <a href="https://en.wikipedia.org/wiki/Median_filter">median filter</a>. The purpose of a median filter is to reduce noise. One way to reduce noise is to blur an image by making it a weighted average of itself and its neighbors. Doing so destroys a lot of edge information and makes the image much less sharp. An alternative is to replace the pixel value with the median (rather than the average) of the surrounding pixels. Of course, we can’t find the median of full color values. Instead, we take the median of the red, green, and blue components separately. To implement a median filter, record the values of the R, G, and B values of all of the immediate neighbors of a pixel (including itself) in separate arrays for each color component. For a pixel that isn’t on edge of the image, it and its neighbors will form a 3 x 3 grid (actually, three different 3 x 3 grids, taking each color component separately). Take the nine elements from each grid and sort them. Then, use the middle value for as the new color component. For any pixel that’s on an edge, use the original color value without any filtering. Be sure to make a new set of arrays to hold the resulting image to avoid re-filtering image data.</td>

   <td></td>

  </tr>

  <tr>

   <td>h</td>

   <td>Horizontally mirror the bitmap. Flip the pixels of the bitmap about the y-axis.</td>

   <td><img decoding="async" alt="Horizontal Mirror Example" data-recalc-dims="1" data-src="https://i0.wp.com/users.etown.edu/w/wittmanb/cs221/projects/images/horizontal.png?w=980" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

    <noscript>

     <img decoding="async" src="https://i0.wp.com/users.etown.edu/w/wittmanb/cs221/projects/images/horizontal.png?w=980" alt="Horizontal Mirror Example" data-recalc-dims="1">

    </noscript></td>

  </tr>

 </tbody>

</table>




When your program starts, it should prompt the user for a file to open. If the file is invalid, it should quit gracefully and print an appropriate error message. Next, it should ask the user how many threads should be used. Then, it should run a loop, asking the user to input commands to alter the image. Legal commands are: <code>i</code>, <code>g</code>, <code>b</code>, <code>v</code>, <code>s</code>, <code>d</code>, <code>r</code>, and <code>q</code> to quit. When the <code>q</code> option is given, the program should prompt the user for a file to save the altered image into.

Some sample execution output is given below. User input is given in <code class="green">green</code>.

<pre>What image file would you like to edit: <em>image.bmp</em>How many threads would you like to use: <em>4</em>What command would you like to perform (i, g, b, v, s, d, r, or q): <em>s</em>Command took 0.147 seconds to executeWhat command would you like to perform (i, g, b, v, s, d, r, or q): <em>i</em>Command took 0.014 seconds to executeWhat command would you like to perform (i, g, b, v, s, d, r, or q): <em>r</em>Command took 0.009 seconds to executeWhat command would you like to perform (i, g, b, v, s, d, r, or q): <em>q</em>What do you want to name your new image file: <em>edited.bmp</em></pre>

This sample execution opens a file called <code>image.bmp</code>, shrinks it, inverts its colors, rotates it 90° to the left, then saves it to <code>edited.bmp</code>.




<h2>Binary Finary</h2>

The first task you need to attack is reading in the bitmap. You will need to allocate enough space to hold the data in the bitmap. How can you do that? Well, at the beginning of a bitmap file is a header which gives a lot of information about the file. If we were coding in C or C++, we could dump that data directly into a <code>struct</code>. Unfortunately, Java doesn’t like giving us direct access to memory. So, we’ll have to read everything in piece by piece. If we were using C, the header would be laid out as follows.

<pre class="prettyprint prettyprinted"><span class="kwd">unsigned</span> <span class="kwd">char</span><span class="pln"> 	type</span><span class="pun">[</span><span class="lit">2</span><span class="pun">];</span>		<span class="com">// always contains 'B' and 'M'</span><span class="kwd">unsigned</span> <span class="kwd">int</span><span class="pln">	size</span><span class="pun">;</span>			<span class="com">// total size of file</span><span class="kwd">unsigned</span> <span class="kwd">int</span><span class="pln">	reserved</span><span class="pun">;</span>		<span class="com">// always 0</span><span class="kwd">unsigned</span> <span class="kwd">int</span><span class="pln">	offset</span><span class="pun">;</span>			<span class="com">// start of data from front of file, should be 54</span><span class="kwd">unsigned</span> <span class="kwd">int</span><span class="pln">	header</span><span class="pun">;</span>			<span class="com">// size of header, always 40</span><span class="kwd">unsigned</span> <span class="kwd">int</span><span class="pln">	width</span><span class="pun">;</span>			<span class="com">// width of image in pixels</span><span class="kwd">unsigned</span> <span class="kwd">int</span><span class="pln">	height</span><span class="pun">;</span>			<span class="com">// height of image in pixels</span><span class="kwd">unsigned</span> <span class="kwd">short</span><span class="pln">	planes</span><span class="pun">;</span>			<span class="com">// planes in image, always 1</span><span class="kwd">unsigned</span> <span class="kwd">short</span><span class="pln">	bits</span><span class="pun">;</span>			<span class="com">// color bit depths, always 24</span><span class="kwd">unsigned</span> <span class="kwd">int</span><span class="pln">	compression</span><span class="pun">;</span>		<span class="com">// always 0		</span><span class="kwd">unsigned</span> <span class="kwd">int</span><span class="pln">	dataSize</span><span class="pun">;</span>		<span class="com">// size of color data in bytes</span><span class="kwd">unsigned</span> <span class="kwd">int</span><span class="pln">	horizontalResolution</span><span class="pun">;</span>	<span class="com">// unreliable, use 72 when writing</span><span class="kwd">unsigned</span> <span class="kwd">int</span><span class="pln">	verticalResolution</span><span class="pun">;</span>	<span class="com">// unreliable, use 72 when writing</span><span class="kwd">unsigned</span> <span class="kwd">int</span><span class="pln">	colors</span><span class="pun">;</span>			<span class="com">// colors in palette, use 0 when writing</span><span class="kwd">unsigned</span> <span class="kwd">int</span><span class="pln">	importantColors</span><span class="pun">;</span>	<span class="com">// important colors, use 0 when writing</span></pre>

If you are interested, there is a good explanation of the file format <a href="http://www.fileformat.info/format/bmp/egff.htm">here</a>.

C works a lot like Java, but there are a few differences. An <code>unsigned char</code> takes up 1 byte of space. An <code>unsigned short</code> takes up 2 bytes of space. An <code>unsigned int</code> takes up 4 bytes of space. Java does not have unsigned types for <code>byte</code>, <code>short</code>, or <code>int</code> (and, confusingly, a <code>char</code> is <strong>two</strong> bytes in Java). In the header, the unsigned types won’t cause problems since none of them are likely to be large enough to be different in signed representation.

But how do you read them? Java provides a number of ways to read binary data directly from a file, but I recommend that you use the <code>FileInputStream</code>class. <code>FileInputStream</code> doesn’t have a lot of frills. The only methods you’ll need are the <code>skip()</code>, <code>read()</code>, and <code>close()</code> methods. The <code>skip()</code> method will skip however many bytes you specify. The <code>read()</code> method will either read a single byte or an array of bytes. The <code>close()</code> method closes the file.

<h2>One Little Endian</h2>

In the bitmap file format (and on Intel machines in general), values are stored in Little Endian byte ordering. This means that the bytes of an <code>int</code> value are stored least significant byte first. When you go to reconstruct an <code>int</code> from four bytes that you’ve read in, you should use the bitwise left shift operator (<code>&lt;&lt;</code>) to shift each of the four bytes by the appropriate amount and add them together.

The process is similar for a <code>short</code>, except that there are only two bytes to worry about.

For more information, read the Wikipedia article on <a href="https://en.wikipedia.org/wiki/Endianness">Endianness</a>.

<h2>Writing the Files</h2>

When writing the files, create an object of type <code>FileOutputStream</code>. The only methods you’ll need to worry about are <code>write()</code> and <code>close()</code>. One version of the <code>write()</code> method writes a single byte and one writes an array of bytes.

When you write the header of the file, you need to output all the bytes for all the values, using the default values given above for values that you neither store nor can compute. You will need to decompose <code>int</code> and <code>short</code> values into their component bytes, in the correct order, and output them. You should use the unsigned right shift operator (<code>&gt;&gt;&gt;</code>) to do so.

<h2>Color Data</h2>

The <code>offset</code> member of the header says where the color data starts in the bitmap. This value should be 54, but if it is larger, you should skip bytes after the header until you make up the difference. We will only deal with 24-bit bitmaps. That means that each pixel is represented by three bytes. The first byte is the blue value, the second byte is the green value, and the third byte is the red value. The first pixel that you read in will be the pixel in the lower left-hand corner of the bitmap. As you read in pixels, you will move across the row until you finish the row, then move onto the row above. Although bitmaps are read from the bottom up and with the color values in BGR order (instead of the more standard RGB), neither of these facts should affect your code much. As long as you are consistent, this ordering won’t matter except in the case of image rotation.

You should allocate a 2D array of bytes to hold the color data. Each row should be three times the width of the image. You can read in a whole row at a time using the <code>read()</code> method. Likewise, you can write out a whole row at a time using the <code>write()</code> method.

Unfortunately, it’s not quite that simple. The bitmap standard requires that the number of bytes in a row of pixels falls evenly on word boundaries, in other words, is evenly divisible by 4. If the number of bytes used to represent a row of pixels is not evenly divisible by 4, it will be padded with zeroes until it is. You must read these zeroes in and discard them when getting the bits. Likewise, you have to remember to appropriately repack with zeroes when writing the file back out.

For padding, there are four different possibilities:

<ol>

 <li style="list-style-type: none">

  <ol>

   <li>The bytes in a row is evenly divisible by 4. No padding is needed.Example: Width = 100. Given 3 bytes in a pixel, 100 × 3 = 300 bytes in a row. There is no padding.</li>

  </ol></li>

</ol>




<ol>

 <li style="list-style-type: none">

  <ol>

   <li>The bytes in a row has a remainder of 3 when divided by 4. Padding of 1 byte occurs.Example: Width = 101. Given 3 bytes in a pixel, 101 × 3 = 303 bytes in a row. There needs to be 1 byte padding in the row to make 304 bytes.</li>

  </ol></li>

</ol>




<ol>

 <li style="list-style-type: none">

  <ol>

   <li>The bytes in a row has a remainder of 2 when divided by 4. Padding of 2 bytes occurs.Example: Width = 102. Given 3 bytes in a pixel, 102 × 3 = 306 bytes in a row. There needs to be 2 bytes padding in the row to make 308 bytes.</li>

  </ol></li>

</ol>




<ol>

 <li>The bytes in a row has a remainder of 1 when divided by 4. Padding of 3 bytes occurs.Example: Width = 103. Given 3 bytes in a pixel, 103 × 3 = 309 bytes in a row. There needs to be 3 bytes padding in the row to make 312 bytes.</li>

</ol>

Even more bizarrely, the strictest interpretation of the bitmap standard requires the total size of the file to be evenly divisible by 4. Since the header is 54 bytes (not divisible by 4) and the color data is always evenly divisible by 4, you should always output an extra two bytes of zeroes after outputting the color data. Thus, the <code>dataSize</code> that you output should be <em>height</em> × ((<em>width</em> × 3) + <em>padding</em>), and the overall image <code>size</code> that you output should be 54 + <code>dataSize</code> + 2.

<h2>Signed vs. Unsigned</h2>

The bitmap standard assumes that the bytes representing colors are unsigned, with the range 0 – 255. The Java <code>byte</code> type is signed and interprets these values to be in the range -128 – 127. If you are just swapping byte values around, as you will in the vertical mirroring or rotating operations, this fact is unimportant.

However, for the shrink, grayscale, invert, and blur operations, you have to do arithmetic on the <code>byte</code> values. You should convert them to <code>int</code> values to do your arithmetic. If a <code>byte</code> value is positive, the unsigned version is the same. If a <code>byte</code> value is negative, add 256 to it to get the equivalent. Oddly enough, if you store an unsigned value into a signed <code>byte</code>, its value is stored correctly. So, you only have to do the conversion one way.

If your images look mostly correct but have odd, brightly color noise in some parts, you have probably messed up the conversion to unsigned.

<h2>Timing and Concurrency</h2>

Your program should time each operation so that you can tell exactly how long it takes. Display this data with exactly three decimal places as shown in the sample output above. The <code>System.nanoTime()</code> method gives high precision time values that you can subtract from each other to find elapsed nanoseconds.

Furthermore, you should write your operations so that they use the number of threads specified by the user at the beginning of the program. These operations, like many kinds of image manipulations, are <strong>embarrassingly parallel</strong>, having a large amount of data with a clear mapping from input to output. Your threaded code does not need to have any locks or other synchronization tools. Each thread that is spawned should know what data it will write into the output 2D array of bytes. As long as none of the data that the threads are writing overlaps, the threads can run independently without fear.

An easy strategy to adopt is to number your threads. If your program is using four threads, each thread could operate on every fourth row in the image. The amount of data skipped for each thread is called its <strong>stride</strong>. An alternative strategy is for each thread to operate on blocks of rows. Again, if your program is using four threads with this strategy, the first thread would operate on the first 1/4 of the rows, the second on the second 1/4 of rows, and so on. This strategy can have better cache performance, but it is trickier to implement when the number of rows is not divisible by the number of threads.

Because these operations are memory-access intensive, you may see no speedup from threaded versions. On the other hand, your threaded versions of code should not be markedly slower. For your own development as a computer scientist, it is instructive to see which kinds of images (large or small) and which operations achieve some speedup or are particularly prone to slowdown when using multiple threads.

<h2>Hints</h2>

<ul>

 <li style="list-style-type: none">

  <ul>

   <li>Start early. This project is tough. Do everything you can to work smoothly with your partner.</li>

  </ul></li>

</ul>




<ul>

 <li style="list-style-type: none">

  <ul>

   <li>Reading in (and writing out) the bitmap data is a huge part of the problem. Once the data is in, if you have stored it in a reasonable way, doing the actual transformations should be relatively straightforward. It’s a good idea to let one member of the group work just on input and output and the other do the bitmap transformations. Also, you should test your code by reading in an image and then outputting it directly. If it looks exactly the same, you’re on the right path.</li>

  </ul></li>

</ul>




<ul>

 <li style="list-style-type: none">

  <ul>

   <li>Make sure you test rectangular (non-square) bitmap images, especially with rotation! Code that works for square images without padding has no guarantee that it will work for messier cases.</li>

  </ul></li>

</ul>




<ul>

 <li style="list-style-type: none">

  <ul>

   <li>You should only read in data from a file once and write it out once. It does not make sense to output the bitmap data to a file after each operation.</li>

  </ul></li>

</ul>




<ul>

 <li style="list-style-type: none">

  <ul>

   <li>You may need to visualize the bitmaps you are creating to see how you are doing. The Windows image viewers should be sufficient for this purpose. If the image won’t load or doesn’t look right, you have corrupted its header or data somehow. Also, you should try to limit the size of the bitmaps you use for testing since they take up a lot of space.</li>

  </ul></li>

</ul>




<ul>

 <li style="list-style-type: none">

  <ul>

   <li>Work incrementally. Compile constantly. Get bitmaps inputting and outputting without any operations first. Then, add in a simple operations like inverse. You may want to print out the header information for testing purposes (or at least view it in the debugger).</li>

  </ul></li>

</ul>




<ul>

 <li style="list-style-type: none">

  <ul>

   <li>Write clean code. You can easily make code so complicated that no one (including your instructor) can figure out why it doesn’t work.</li>

  </ul></li>

</ul>




<ul>

 <li style="list-style-type: none">

  <ul>

   <li>Do not import any packages other than <code>java.io.*</code> and <code>java.util.Scanner</code>.</li>

  </ul></li>

</ul>




<ul>

 <li style="list-style-type: none">

  <ul>

   <li>You are expected to create a class called <code>Bitmap</code> to hold bitmap data. Each transformation (such as shrink or double) should have a corresponding member function. Your class should be stored in a file called <code>Bitmap.java</code>. You must also have a main program that reads the commands and reacts appropriately. This class should be called <code>Manipulator</code> and stored in a file called <code>Manipulator.java</code>. You may write other classes if you find them useful.</li>

  </ul></li>

</ul>




<ul>

 <li style="list-style-type: none">

  <ul>

   <li>Plan out your code ahead of time. Good design saves on coding.</li>

  </ul></li>

</ul>




<ul>

 <li style="list-style-type: none">

  <ul>

   <li>It is recommended that you first get all the image transformations working <strong>without</strong> using multiple threads. Once you get them working, then added threading to your <code>Bitmap</code> class.</li>

  </ul></li>

</ul>




<ul>

 <li>Refer to the <a href="http://users.etown.edu/w/wittmanb/cs221/standards">coding standards page</a> for more information on what I’m looking for in terms of style.</li>

</ul>

<h2>Provided Images Files</h2>

No Padding Required

<ul>

 <li><a href="http://users.etown.edu/w/wittmanb/cs221/projects/images/delaware.bmp">delaware.bmp</a></li>

 <li><a href="http://users.etown.edu/w/wittmanb/cs221/projects/images/jonah.bmp">jonah.bmp</a></li>

 <li><a href="http://users.etown.edu/w/wittmanb/cs221/projects/images/sleeping.bmp">sleeping.bmp</a></li>

</ul>

Padding Required

<ul>

 <li><a href="http://users.etown.edu/w/wittmanb/cs221/projects/images/amy.bmp">amy.bmp</a></li>

 <li><a href="http://users.etown.edu/w/wittmanb/cs221/projects/images/dan.bmp">dan.bmp</a></li>

 <li><a href="http://users.etown.edu/w/wittmanb/cs221/projects/images/maybe.bmp">maybe.bmp</a></li>

</ul>


