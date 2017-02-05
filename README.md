# Fork information

Adds a compress function to compress data to lz4 and write to file, decompress function to read lz4 data from file and decompress.

string **lz4\_compress_to_file** ( string _$path_, string _$data_ [ , int _$level_ = 0 , string _$extra_ = NULL ] )

* _path_

  File path to write lz4 data to.

string **lz4\_uncompress_from_file** ( string _$path_, string _$data_ [ , long _$maxsize_ = -1 , long _$offset_ = -1 ] )

* _path_

  File path to read lz4 data from and decompress.

Original README follows:

# LZ4 Extension for PHP

[![Build Status](https://secure.travis-ci.org/kjdev/php-ext-lz4.png?branch=master)](http://travis-ci.org/kjdev/php-ext-lz4)

This extension allows LZ4.

Documentation for LZ4 can be found at
[» https://github.com/Cyan4973/lz4](https://github.com/Cyan4973/lz4).

## Build

    % git clone --recursive --depth=1 https://github.com/kjdev/php-ext-lz4.git
    % cd php-ext-lz4
    % phpize
    % ./configure
    % make
    % make install

> use system library: `./configure --with-lz4-includedir=/usr`

## Configration

lz4.ini:

    extension=lz4.so

## Function

* lz4\_compress — LZ4 compression
* lz4\_uncompress — LZ4 decompression

### lz4\_compress — LZ4 compression

#### Description

string **lz4\_compress** ( string _$data_ [ , int _$level_ = 0 , string _$extra_ = NULL ] )

LZ4 compression.

#### Pameters

* _data_

  The string to compress.

* _level_

  The level of compression (1-12, Recommended values are between 4 and 9).
  (Default to 0, Not High Compression Mode.)

* _extra_

  Prefix to compressed data.

#### Return Values

Returns the compressed data or FALSE if an error occurred.


### lz4\_uncompress — LZ4 decompression

#### Description

string **lz4\_uncompress** ( string _$data_ [ , long _$maxsize_ = -1 , long _$offset_ = -1 ] )

LZ4 decompression.

#### Pameters

* _data_

  The compressed string.

* _maxsize_

  Allocate size output data.

* _offset_

  Offset to decompressed data.

#### Return Values

Returns the decompressed data or FALSE if an error occurred.

## Examples

    $data = lz4_compress('test');

    lz4_uncompress($data);

## Compress Data

### Default

    $data = lz4_compress('test')

![compress-default](docs/compress-default.png)

### Extra prefix data

    $data = lz4_compress('test', false, 'PREFIX')

![compress-extra](docs/compress-extra.png)

## Uncompress Data

### Default

    lz4_uncompress($data);

![uncompress-default](docs/uncompress-default.png)

### Offset

    lz4_uncompress($data, 256, 6);

![uncompress-offset](docs/uncompress-offset.png)
