bashbundle
==========

Software for running updates on linux based embedded systems

Format
------

The bashbundle format has the following structure:

* filename.bashbundle  - one file containing all relevant data
  * version - file containing a single revision number (only newer bundles than the installed are executed)
  * data.tar.gz - file containing the signed bundle itself
    * version - the version again (signed this time)
    * run.bash - file that gets executed once the version is newer and the package is signed
    * other files that are needed (payload)
  * data.sig - openssl signature of data.tar.gz

Usage runtime
-------------

`bbrun [bashbundle file] [versions folder]`

* Bashbundle looks for authorized signing keys in /etc/bashbundle/keys
* versions for each bundle are stored in the version folder (use /etc/bashbundle/versions for global and ~/.bashbundle/versions for local packages)

Usage packager
--------------

`bbpack [data folder] [private key file] [destination file]`

* data folder: folder containing run.bash and version while version is incremented.
* private key file: PEM file used to sign the package
* destination: .bashbundle file

Creating a key pair
-------------------

- Create DSA parameters: `openssl dsaparam -out dsaparam.pem 2048`
- Create your private key (for bbpack): `openssl gendsa -des3 -out privkey.pem dsaparam.pem` (leave out `-des3` to not have a password)
- Extract the public key part (for /etc/bashbundle/keys on client) with `openssl dsa -in privkey.pem -pubout -out pubkey.pem`

Examples
--------

Check out examples/ for examples. The Hello World Example is a test where the script uses a payload in the data folder.

