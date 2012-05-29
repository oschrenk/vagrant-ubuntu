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