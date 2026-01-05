# Fractal compression - Wikipedia

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a1/Zasada_dzialania_ifs_1.svg/250px-Zasada_dzialania_ifs_1.svg.png)](/broken/pages/7a8ab1c1d4107a5fc8504f30d23355df0e44e6f9)

Fractal compression is a [lossy compression](/broken/pages/3e1879273a212b010525610ef26f5dde22a2a771) method for [digital images](/broken/pages/32f9873ca645287ca2c7abee8cc3a3f49d2c7f0a), based on [fractals](/broken/pages/48bacce87ee5da9516913d491294378db832f5b0). The method is best suited for textures and natural images, relying on the fact that parts of an image often resemble other parts of the same image.[\[1\]](fractal-compression-wikipedia.md#cite_note-1) Fractal algorithms convert these parts into mathematical data called "fractal codes" which are used to recreate the encoded image.

### Iterated function systems

Main article: [Iterated function system](/broken/pages/bedef2d84d5ea97ae07f5892ad20fbd8f84277ab)

Fractal image representation may be described mathematically as an [iterated function system](/broken/pages/bedef2d84d5ea97ae07f5892ad20fbd8f84277ab).[\[2\]](fractal-compression-wikipedia.md#cite_note-SIGGRAPH'92-2)

#### For binary images

We begin with the representation of a [binary image](/broken/pages/b5dacb0c89a5d23d76b61ab626d1e7ca2d1bcb8e), where the image may be thought of as a subset of R2. An IFS is a set of contraction mappings f1, ..., fN,

fi: R2 → R2.

According to these mapping functions, the IFS describes a two-dimensional set S as the fixed point of the [Hutchinson operator](/broken/pages/8c79d4bcb562eaf9bafb3bdd7d4209369bd3b7bc)

H(A) = ⋃\_{i=1}^N fi(A), A ⊂ R2.

That is, H is an operator mapping sets to sets, and S is the unique set satisfying H(S) = S. The idea is to construct the IFS such that this set S is the input binary image. The set S can be recovered from the IFS by [fixed point iteration](/broken/pages/7755687c14ed97fbdeae36670f267ac7c3d8b13d): for any nonempty compact initial set A0, the iteration A\_{k+1} = H(A\_k) converges to S.

The set S is self-similar because H(S) = S implies that S is a union of mapped copies of itself:

S = f1(S) ∪ f2(S) ∪ ⋯ ∪ fN(S).

So we see the IFS is a fractal representation of S.

#### Extension to grayscale

IFS representation can be extended to a [grayscale image](/broken/pages/10e03a93c6984c8f1c016b4832deb8569287a7f5) by considering the image's [graph](/broken/pages/4fc838367376f99631007965199a0fc0905e09dd) as a subset of R3. For a grayscale image u(x, y), consider the set S = {(x, y, u(x, y))}. Then similar to the binary case, S is described by an IFS using a set of contraction mappings f1, ..., fN, but in R3,

fi: R3 → R3.

### Encoding

A challenging problem of ongoing research in fractal image representation is how to choose the f1, ..., fN such that its fixed point approximates the input image, and how to do this efficiently.

A simple approach[\[2\]](fractal-compression-wikipedia.md#cite_note-SIGGRAPH'92-2) for doing so is the following partitioned iterated function system (PIFS):

{% stepper %}
{% step %}
### Partition range blocks

Partition the image domain into range blocks Ri of size s × s.
{% endstep %}

{% step %}
### Find matching domain blocks

For each Ri, search the image to find a block Di of size 2s × 2s that is very similar to Ri.
{% endstep %}

{% step %}
### Select mapping functions

Select the mapping functions such that H(Di) = Ri for each i.
{% endstep %}
{% endstepper %}

In the second step, it is important to find a similar block so that the IFS accurately represents the input image, so a sufficient number of candidate blocks for Di need to be considered. On the other hand, a large search considering many blocks is computationally costly.

This bottleneck of searching for similar blocks is why PIFS fractal encoding is much slower than, for example, [DCT](/broken/pages/756991a7ce1c5bce3193fe07a90a046ab16adb19) and [wavelet](/broken/pages/77f2a69c34d9c96d5998c4ffbe5b592fd42e1831) based image representation.

The initial square partitioning and [brute-force search](/broken/pages/ea674807de17a156adf73969a74137d66f6daf04) algorithm presented by Jacquin provides a starting point for further research and extensions in many possible directions—different ways of partitioning the image into range blocks of various sizes and shapes; fast techniques for quickly finding a close-enough matching domain block for each range block rather than brute-force searching, such as fast [motion estimation](/broken/pages/5c5f3a2e819fd1c7fde0c3ec672cbb3b0a151079) algorithms; different ways of encoding the mapping from the domain block to the range block; etc.[\[3\]](fractal-compression-wikipedia.md#cite_note-3)

Other researchers attempt to find algorithms to automatically encode an arbitrary image as RIFS (recurrent iterated function systems) or global IFS, rather than PIFS; and algorithms for fractal video compression including [motion compensation](/broken/pages/ddb6117d51ed93cd4f55045ab0716184d6f8c94f) and three dimensional iterated function systems.[\[4\]](fractal-compression-wikipedia.md#cite_note-lacroix-4)[\[5\]](fractal-compression-wikipedia.md#cite_note-5)

Fractal image compression has many similarities to [vector quantization](/broken/pages/748043bdedb49623eb0477ffc77b4afe5cad5b46) image compression.[\[6\]](fractal-compression-wikipedia.md#cite_note-6)

### Features

With fractal compression, encoding is extremely computationally expensive because of the search used to find the self-similarities. Decoding, however, is quite fast. While this asymmetry has so far made it impractical for real time applications, when video is archived for distribution from disk storage or file downloads fractal compression becomes more competitive.[\[7\]](fractal-compression-wikipedia.md#cite_note-Jenson_7-0)[\[8\]](fractal-compression-wikipedia.md#cite_note-Heath1999-8)

At common compression ratios, up to about 50:1, fractal compression provides similar results to [DCT-based](/broken/pages/756991a7ce1c5bce3193fe07a90a046ab16adb19) algorithms such as [JPEG](/broken/pages/3cced3a19f96602f59895ccfd1700462af60095c).[\[9\]](fractal-compression-wikipedia.md#cite_note-9) At high compression ratios fractal compression may offer superior quality. For satellite imagery, ratios of over 170:1[\[10\]](fractal-compression-wikipedia.md#cite_note-ieee_2000-10) have been achieved with acceptable results. Fractal video compression ratios of 25:1–244:1 have been achieved in reasonable compression times (2.4 to 66 sec/frame).[\[11\]](fractal-compression-wikipedia.md#cite_note-11)

Compression efficiency increases with higher image complexity and color depth, compared to simple [grayscale](/broken/pages/f3def42c93612f94efef086a23a48159724675e0) images.

#### Resolution independence and fractal scaling

An inherent feature of fractal compression is that images become resolution independent[\[12\]](fractal-compression-wikipedia.md#cite_note-12) after being converted to fractal code. This is because the iterated function systems in the compressed file scale indefinitely. This indefinite scaling property of a fractal is known as "fractal scaling".

#### Fractal interpolation

The resolution independence of a fractal-encoded image can be used to increase the display resolution of an image. This process is also known as "fractal interpolation". In fractal interpolation, an image is encoded into fractal codes via fractal compression, and subsequently decompressed at a higher resolution. The result is an up-sampled image in which iterated function systems have been used as the [interpolant](/broken/pages/f40b2059f49e4091a27ba155e674880e9a914af4).[\[13\]](fractal-compression-wikipedia.md#cite_note-13)

Fractal interpolation maintains geometric detail very well compared to traditional interpolation methods like [bilinear interpolation](/broken/pages/ce608f59bafcd06236072974d12dc8439804880f) and [bicubic interpolation](/broken/pages/3c2f98441578ad097ef5507b7082e5091a6ea666).[\[14\]](fractal-compression-wikipedia.md#cite_note-14)[\[15\]](fractal-compression-wikipedia.md#cite_note-15)[\[16\]](fractal-compression-wikipedia.md#cite_note-16) Since the interpolation cannot reverse Shannon entropy however, it ends up sharpening the image by adding random instead of meaningful detail. One cannot, for example, enlarge an image of a crowd where each person's face is one or two pixels and hope to identify them.

### History

[Michael Barnsley](/broken/pages/594ca9f2a5a55549cbed0d350155c4987b94e912) led the development of fractal compression from 1985 at the Georgia Institute of Technology (where both Barnsley and Sloan were professors in the mathematics department).[\[17\]](fractal-compression-wikipedia.md#cite_note-17) The work was sponsored by [DARPA](/broken/pages/17d110ca5fc76d9affe9b76a6dbfda8bb9918b07) and the [Georgia Tech Research Corporation](/broken/pages/60e1c86ecb5dbfacaa0369944e02cfc395579e7c). The project resulted in several [patents](/broken/pages/4802215b4f1f78b3524293cb15b749d41e7fcf0b) from 1987.[\[18\]](fractal-compression-wikipedia.md#cite_note-18) Barnsley's graduate student Arnaud Jacquin implemented the first automatic algorithm in software in 1992.[\[19\]](fractal-compression-wikipedia.md#cite_note-19)[\[20\]](fractal-compression-wikipedia.md#cite_note-20) All methods are based on the [fractal transform](/broken/pages/e71a31962e4314b92c5ac250f7efd15ba0f9cc3e) using [iterated function systems](/broken/pages/bedef2d84d5ea97ae07f5892ad20fbd8f84277ab). Michael Barnsley and Alan Sloan formed Iterated Systems Inc.[\[21\]](fractal-compression-wikipedia.md#cite_note-21) in 1987 which was granted over 20 additional patents related to fractal compression.

A major breakthrough for Iterated Systems Inc. was the automatic fractal transform process which eliminated the need for human intervention during compression as was the case in early experimentation with fractal compression technology. In 1992, Iterated Systems Inc. received a US$2.1 million government grant[\[22\]](fractal-compression-wikipedia.md#cite_note-22) to develop a prototype digital image storage and decompression chip using fractal transform image compression technology.

Fractal image compression has been used in a number of commercial applications: [onOne Software](/broken/pages/6280154cb7166173087c29228f52cceba0a3bf37), developed under license from Iterated Systems Inc., [Genuine Fractals](/broken/pages/8e8e8cacaca3fe9e8dbdfe2969f42f8168b3cd9c) 5[\[23\]](fractal-compression-wikipedia.md#cite_note-23) which is a [Photoshop](/broken/pages/36fd4faaa4bc9ac20735fe945e0a5a33bd41d787) plugin capable of saving files in compressed FIF (Fractal Image Format). To date the most successful use of still fractal image compression is by [Microsoft](/broken/pages/3e123123c97583409c703e0be1d5d405c04ceb42) in its [Encarta](/broken/pages/b07a01cd869f769e8eae09ede1bfd6a59e16c651) multimedia encyclopedia,[\[24\]](fractal-compression-wikipedia.md#cite_note-24) also under license.

Iterated Systems Inc. supplied a shareware encoder (Fractal Imager), a stand-alone decoder, a Netscape plug-in decoder and a development package for use under Windows. The redistribution of the "decompressor DLL" provided by the ColorBox III SDK was governed by restrictive per-disk or year-by-year licensing regimes for proprietary software vendors and by a discretionary scheme that entailed the promotion of the Iterated Systems products for certain classes of other users.[\[25\]](fractal-compression-wikipedia.md#cite_note-25)

ClearVideo – also known as [RealVideo](/broken/pages/04426fd97ca4432f7661cd7dfc8ce2c68f1c4dc2) (Fractal) – and SoftVideo were early fractal video compression products. ClearFusion was Iterated's freely distributed streaming video plugin for web browsers. In 1994 SoftVideo was licensed to [Spectrum Holobyte](/broken/pages/47f8f694fbf7e730a0c1f7a9c389a420ae2b1371) for use in its [CD-ROM](/broken/pages/842d1c14b48122dd181855dc695e8e4554db0a29) games including Falcon Gold and [Star Trek: The Next Generation A Final Unity](/broken/pages/cedfc0f8a402bb6bd6cf5a8aa464b8507a1e5622).[\[26\]](fractal-compression-wikipedia.md#cite_note-26)

In 1996, Iterated Systems Inc. announced[\[27\]](fractal-compression-wikipedia.md#cite_note-27) an alliance with the [Mitsubishi](/broken/pages/d2db4af84eb2fa5d3087c5784edfee63ef3592c0) Corporation to market ClearVideo to their Japanese customers. The original ClearVideo 1.2 decoder driver is still supported[\[28\]](fractal-compression-wikipedia.md#cite_note-28) by Microsoft in [Windows Media Player](/broken/pages/d61780503e7d55698beb3aac98fd8c013339f627) although the encoder is no longer supported.

Two firms, Total Multimedia Inc. and Dimension, both claim to own or have the exclusive licence to Iterated's video technology, but neither has yet released a working product. The technology basis appears to be Dimension's U.S. patents 8639053 and 8351509, which have been considerably analyzed.[\[29\]](fractal-compression-wikipedia.md#cite_note-29) In summary, it is a simple quadtree block-copying system with neither the bandwidth efficiency nor PSNR quality of traditional DCT-based codecs. In January 2016, TMMI announced that it was abandoning fractal-based technology altogether.

Research papers between 1997 and 2007 discussed possible solutions to improve fractal algorithms and encoding hardware.[\[30\]](fractal-compression-wikipedia.md#cite_note-30)[\[31\]](fractal-compression-wikipedia.md#cite_note-31)[\[32\]](fractal-compression-wikipedia.md#cite_note-32)[\[33\]](fractal-compression-wikipedia.md#cite_note-33)[\[34\]](fractal-compression-wikipedia.md#cite_note-34)[\[35\]](fractal-compression-wikipedia.md#cite_note-35)[\[36\]](fractal-compression-wikipedia.md#cite_note-36)[\[37\]](fractal-compression-wikipedia.md#cite_note-37)[\[38\]](fractal-compression-wikipedia.md#cite_note-38)

### Implementations

A library called Fiasco was created by Ullrich Hafner. In 2001, Fiasco was covered in the [Linux Journal](/broken/pages/68731d99726bb6d06b7eae876d9323b9a65b4604).[\[39\]](fractal-compression-wikipedia.md#cite_note-39) According to the 2000-04 Fiasco manual, Fiasco can be used for video compression.[\[40\]](fractal-compression-wikipedia.md#cite_note-40) The [Netpbm](/broken/pages/10c1a0fc150b318c1e089d60d22ed3f99061ce14) library includes the Fiasco library.[\[41\]](fractal-compression-wikipedia.md#cite_note-41)[\[42\]](fractal-compression-wikipedia.md#cite_note-42)

Femtosoft developed an implementation of fractal image compression in [Object Pascal](/broken/pages/9579f2f200c5d3b9471f116cb210d50e2db52002) and [Java](/broken/pages/f82a3e9dd403ba4443368fcdd8c55302d55c90af).[\[43\]](fractal-compression-wikipedia.md#cite_note-43)

### See also

* [Iterated function system](/broken/pages/bedef2d84d5ea97ae07f5892ad20fbd8f84277ab)
* [Image compression](/broken/pages/28b3a114a3ea706073d4524879fb0ec4187d99ec)
* [Wavelet](/broken/pages/77f2a69c34d9c96d5998c4ffbe5b592fd42e1831)

### Notes

1. May, Mike (1996). "Fractal Image Compression". American Scientist. 84 (5): 442–451. [Bibcode: 1996AmSci..84..442M](https://ui.adsabs.harvard.edu/abs/1996AmSci..84..442M). [JSTOR 29775747](https://www.jstor.org/stable/29775747). [ProQuest 215266230](https://www.proquest.com/docview/215266230).
2. Fischer, Yuval (1992-08-12). Przemyslaw Prusinkiewicz (ed.). SIGGRAPH'92 course notes - Fractal Image Compression (PDF). SIGGRAPH. Vol. Fractals - From Folk Art to Hyperreality. ACM SIGGRAPH. Archived PDF. Retrieved 2017-06-28.
3. Saupe, Dietmar; Hamzaoui, Raouf (November 1994). "A review of the fractal image compression literature". ACM SIGGRAPH Computer Graphics. 28 (4): 268–276. doi:10.1145/193234.193246.
4. Lacroix, Bruno (1999). Fractal image compression (Thesis). doi:10.22215/etd/1999-04159.
5. Fisher, Yuval (2012). Fractal Image Compression: Theory and Application. Springer. p. 300. ISBN 978-1-4612-2472-3.
6. Henry Xiao. "Fractal Compression". 2004.
7. John R. Jensen, "Remote Sensing Textbooks", Image Compression Alternatives and Media Storage Considerations (reference to compression/decompression time), University of South Carolina (archived).
8. Steve Heath (23 August 1999). Multimedia and communications technology. Focal Press. pp. 120–123. ISBN 978-0-240-51529-8.
9. Sayood, Khalid (2006). Introduction to Data Compression. Elsevier. pp. 560–569. ISBN 978-0-12-620862-7.
10. Wee Meng Woon; et al. (2000). "Achieving high data compression of self-similar satellite images using fractal". IGARSS 2000. doi:10.1109/IGARSS.2000.861646.
11. Fisher, Y. (July 1995). Fractal encoding of video sequences. Fractal image encoding and analysis. Trondheim. INIST 1572685.
12. "Walking, Talking Web" Byte Magazine article on fractal compression/resolution independence (Archived).
13. He, Chuan-jiang; Li, Gao-ping; Shen, Xiao-na (May 2007). "Interpolation decoding method with variable parameters for fractal image compression". Chaos, Solitons & Fractals. 32 (4): 1429–1439. doi:10.1016/j.chaos.2005.11.058.\
    14–16. Additional references on fractal interpolation and scaling (see source).
14. Barnsley, Michael; Sloan, Alan (January 1988). "A Better Way to Compress Images". Byte. pp. 215–223.\
    18–43. Further patents, papers, manuals, and implementation references (see source).

### External links

* [Pulcini and Verrando's Compressor](http://www.verrando.com/pulcini/gp-uw1.html)
* Keith Howell's 1993 M.Sc. dissertation Fractal Image Compression for Spaceborne Transputers (archived)
* "My Main Squeeze: Fractal Compression", Nov 1993, Wired.
* [Fractal Basics](https://www.fileformat.info/mirror/egff/ch09_09.htm) description at FileFormat.Info
* [Superfractals](http://www.superfractals.com/) website devoted to fractals by the inventor of fractal compression

(References and inline citation links retained as in the source.)
