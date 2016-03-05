[![Build Status](https://travis-ci.org/blar/filesystem.png?branch=master)](https://travis-ci.org/blar/filesystem)
[![Coverage Status](https://coveralls.io/repos/blar/filesystem/badge.png?branch=master)](https://coveralls.io/r/blar/filesystem?branch=master)
[![Dependency Status](https://gemnasium.com/blar/filesystem.svg)](https://gemnasium.com/blar/filesystem)
[![Dependencies Status](https://depending.in/blar/filesystem.png)](http://depending.in/blar/filesystem)

# blar/filesystem

Filesystem functions for PHP.

## Examples

### File exists

    $file = new File('/etc/passwd');
    if($file->exists()) {
        echo 'File exists';
    }

### Readable

    $file = new File('/etc/passwd');
    if($file->isReadable()) {
        echo 'File is readable';
    }

### Writable

    $file = new File('/etc/passwd');
    if($file->isWritable()) {
        echo 'File is writable';
    }

### Set content

    $file = new File('.htaccess');
    $file->setContent("Deny from all\n");

### Get content

    $file = new File('/etc/passwd');
    var_dump($file->getContent());

### Append content

    $file = new File('test.log');
    $file->append('Append some content at the end of the file');

### Slice

    $file = new File('test.mp3');
    if($file->slice(-128, 3) == 'TAG') {
        echo 'File has an ID3v1 tag';
    }

### Copy file

    $file = new File('foo.txt');
    $file->copy('bar.txt');

### Rename file

    $file = new File('foo.txt');
    $file->rename('bar.txt');

### Create a Symlink

    $file = new File('foo.txt');
    $file->link('bar.txt');

### Set permissions

    $file = new File('secret.txt');
    $file->setPermissions(File::PERMISSION_OWNER_ALL | File::PERMISSION_GROUP_NONE | File::PERMISSION_OTHER_NONE);
    // same as $file->setPermissions(0700);

### Check permissions

    $file = new File('secret.txt');
    if($file->checkPermissions(File::PERMISSION_OTHER_READ)) {
        echo 'File is readable for any user on the system';
    }

### Is uploaded file

    $file = new File('/etc/passwd');
    var_dump($file->isUploaded());
