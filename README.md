Amazon S3 driver for VFS (Apache Commons Virtual File System)
=============================================================

## Latest branch 4.x.x

[![vfs-s3](https://maven-badges.herokuapp.com/maven-central/com.github.abashev/vfs-s3/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.github.abashev/vfs-s3)
[![Build Status](https://travis-ci.org/abashev/vfs-s3.svg?branch=branch-4.x.x)](https://travis-ci.org/abashev/vfs-s3)
[![codecov](https://codecov.io/gh/abashev/vfs-s3/branch/branch-4.x.x/graph/badge.svg)](https://codecov.io/gh/abashev/vfs-s3)

### How to add as dependency into your Maven build

    <dependency>
        <groupId>com.github.abashev</groupId>
        <artifactId>vfs-s3</artifactId>
        <version>4.0.0</version>
    </dependency>

### How to add as dependency into your Gradle build
    
    implementation 'com.github.abashev:vfs-s3:4.0.0'

### Sample Java Code for AWS S3

	// Create a folder
	FileSystemManager fsManager = VFS.getManager();
	FileObject dir = fsManager.resolveFile("s3://simple-bucket.s3-eu-west-1.amazonaws.com/test-folder/");
	dir.createFolder();

	// Upload file to S3
	FileObject dest = fsManager.resolveFile("s3://s3-eu-west-1.amazonaws.com/test-bucket/backup.zip");
	FileObject src = fsManager.resolveFile(new File("/path/to/local/file.zip").getAbsolutePath());
	dest.copyFrom(src, Selectors.SELECT_SELF);

### Sample Java Code for Yandex Cloud https://cloud.yandex.ru/

	// Upload file
	FileObject dest = fsManager.resolveFile("s3://s3-tests.storage.yandexcloud.net/backup.zip");
	FileObject src = fsManager.resolveFile(new File("/path/to/local/file.zip").getAbsolutePath());
	dest.copyFrom(src, Selectors.SELECT_SELF);
    

### Running tests

For running tests you need active credentials for AWS. You can specify them as

1.  Shell environment properties

        export AWS_ACCESS_KEY=AAAAAAA
        export AWS_SECRET_KEY=SSSSSSS
        export BASE_URL=s3://<full url like simple-bucket.s3-eu-west-1.amazonaws.com or s3-eu-west-1.amazonaws.com/test-bucket>

2. Or any standard ways how to do it in AWS SDK (iam role and so on)


**Make sure that you never commit your credentials!**

### TODO 

- [ ] Shadow all dependencies inside vfs-s3 artifact

### Old releases 

Branch       |  Build Status | Code coverage
------------ | ------------ | ------------
branch-3.0.x |  [![Build Status](https://travis-ci.org/abashev/vfs-s3.svg?branch=branch-3.0.x)](https://travis-ci.org/abashev/vfs-s3) | [![codecov](https://codecov.io/gh/abashev/vfs-s3/branch/branch-3.0.x/graph/badge.svg)](https://codecov.io/gh/abashev/vfs-s3)
branch-2.4.x |  [![Build Status](https://secure.travis-ci.org/abashev/vfs-s3.png?branch=branch-2.4.x)](http://travis-ci.org/abashev/vfs-s3) | [![codecov](https://codecov.io/gh/abashev/vfs-s3/branch/branch-2.4.x/graph/badge.svg)](https://codecov.io/gh/abashev/vfs-s3)
branch-2.3.x |  [![Build Status](https://secure.travis-ci.org/abashev/vfs-s3.png?branch=branch-2.3.x)](http://travis-ci.org/abashev/vfs-s3) |
branch-2.2.x |  [![Build Status](https://secure.travis-ci.org/abashev/vfs-s3.png?branch=branch-2.2.x)](http://travis-ci.org/abashev/vfs-s3) |
