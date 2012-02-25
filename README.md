# gepub [<img src="https://secure.travis-ci.org/skoji/gepub.png" />](http://travis-ci.org/skoji/gepub)

* http://github.com/skoji/gepub

## DESCRIPTION:

a generic EPUB parser/generator library.

## FEATURES/PROBLEMS:

* GEPUB::Book provides functionality to create EPUB file, and parsing EPUB file
* Handle every metadata in EPUB2/EPUB3.
* GEPUB::Builder privides easy and powerful way to create EPUB3 files

* See [issues](https://github.com/skoji/gepub/issues/) for known problems.

## SYNOPSIS:

### Builder Example

    require 'rubygem'
    require 'gepub'
    builder = GEPUB::Builder.new {
      language 'en'
      unique_identifier 'http:/example.jp/bookid_in_url', 'BookID', 'URL'
      title 'GEPUB Sample Book'
      subtitle 'This book is just a sample'

      creator 'KOJIMA Satoshi'

      contributors 'Denshobu', 'Asagaya Densho', 'Shonan Densho Teidan', 'eMagazine Torutaru'

      date '2012-02-29T00:00:00Z'

      resources(:workdir => '~/epub/sample_book_source/') {
        cover_image 'img/image1.jpg' => 'image1.jpg'
        ordered {
          file 'text/chap1.xhtml'
          heading 'Chapter 1'

          file 'text/chap1-1.xhtml'

          file 'text/chap2.html'
          heading 'Chapter 2'
        }
      }
    }
    epubname = File.join(File.dirname(__FILE__), 'example_test_with_builder.epub')
    builder.generate_epub(epubname)

[more builder examples](https://gist.github.com/1878995)
 
[examples in this repository](https://github.com/skoji/gepub/tree/master/examples/) 

## INSTALL:

* gem install gepub

## LICENSE:

(The New BSD License)

Copyright (c) 2010-2012, KOJIMA Satoshi
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

    * Redistributions of source code must retain the above copyright
      notice, this list of conditions and the following disclaimer.
    * Redistributions in binary form must reproduce the above copyright
      notice, this list of conditions and the following disclaimer in the
      documentation and/or other materials provided with the distribution.
    * Neither the name of the <organization> nor the
      names of its contributors may be used to endorse or promote products
      derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL <COPYRIGHT HOLDER> BE LIABLE FOR ANY
DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.