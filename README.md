## About

This script will: 

 1. download the Ubuntu 12.04 alternate server, 32bit iso
 2. ... do some magic to turn it into a vagrant box file
 3. output `package.box`

## Usage

    ./build.sh

This should do everything you need. If you don't have 
mkisofs, install [homebrew](http://mxcl.github.com/homebrew/), then:

    brew install cdrtools

## Problems

 Unfortunately the `tar` command supplied in OS X 10.7.4 has a bug
	
	$ tar --version
	bsdtar 2.8.3 - libarchive 2.8.3

It just won't extract the iso file. Instead of creating a workarround in the build file I opted to solve the problem.

Libarchive has been updated to 3.0.4. homebrew doesn't support it directly, because its duplicating os behavior. So I created my own updated version of libarchive for 3.0.4. and submitted a pull request to the adamv/homebrew-dupes repository (which accepts duplicates). So:

	$ brew install https://raw.github.com/oschrenk/homebrew-dupes/edbc2b464d0bf4420508297418481178299f420a/libarchive.rb
	$ /usr/local/bin/bsdtar --version
	bsdtar 3.0.4 - libarchive 3.0.4
	$ /usr/local/bin/bsdtar -xvf ubuntu-12.04-alternate-i386.iso 
	sudo rm /usr/bin/tar
	cd /usr/bin
	sudo n -s /usr/local/bin/bsdtar tar

Every day a new bug to squash, a new yak to shave