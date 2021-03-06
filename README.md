[![Build Status](https://travis-ci.org/KonstantinKuklin/StreamLibrary.svg?branch=master)](https://travis-ci.org/KonstantinKuklin/StreamLibrary)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/KonstantinKuklin/StreamLibrary/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/KonstantinKuklin/StreamLibrary/?branch=master)
[![Scrutinizer Test Coverage](https://scrutinizer-ci.com/g/KonstantinKuklin/StreamLibrary/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/KonstantinKuklin/StreamLibrary/?branch=master)
[![Latest Stable Version](https://poser.pugx.org/konstantin-kuklin/stream-library/v/stable.png)](https://packagist.org/packages/konstantin-kuklin/stream-library)
[![Total Downloads](https://poser.pugx.org/konstantin-kuklin/stream-library/downloads.png)](https://packagist.org/packages/konstantin-kuklin/stream-library)

README
======

What is StreamLibrary?
-----------------

StreamLibrary is a PHP wrapper via stream functions. It allows to work with streams with more
comfortable environment.


Requirements
------------

StreamLibrary is only supported on PHP 5 and up.

Installation
------------

The best way to install StreamLibrary is with composer:

```
composer.phar require konstantin-kuklin/stream-library:dev-master
```

Documentation
-------------

First step to work is a creating object of Stream:

```php
$stream = new \Stream\Stream($path, $protocol, $port, $driver);
```

**path** - Path to file on system or ip address in network or hostname which we will work

**protocol** - String value of protocol type, can be Connection::PROTOCOL_TCP, Connection::PROTOCOL_UDP, Connection::PROTOCOL_UNIX

**port** - Integer value of port to connect. Not needs if protocol Connection::PROTOCOL_UNIX. Default value = 0.

**driver** - Object implements StreamDriverInterface. If your connection need to change transfer data you need to describe it logic with this object. Default value is null(mean data haven't been changed)

### Get data from Stream

```php
$stream = new \Stream\Stream($path, $protocol, $port, $driver);
$stream->setReceiveMethod(new StreamGetContentsMethod($maxLength, $offset));
$stream->getContents();
```

**maxLength** - The maximum bytes to read. Default value is -1 (read all the remaining buffer)

**offset** - Seek to the specified offset before reading. Default value is -1 (read without offset)

### Send data to Stream

```php
$stream = new \Stream\Stream($path, $protocol, $port, $driver);
$stream->sendContents($contents);
```

**contents** - can contain any string data
