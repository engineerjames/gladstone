# :handbag: Gladstone :handbag: 

This is a node module for creating [BagIt archives](https://en.wikipedia.org/wiki/BagIt). 

The goal of the project is to implement the complete [BagIt 0.97](https://tools.ietf.org/html/draft-kunze-bagit-08) specification. 

To use it from the command-line you provide a source directory that you want want to create a BagIt archive for, a name for the bag, and a hashing algorithm.

```bash
gladstone --bagName ~/bagname --originDirectory ~/source --cryptoMethod md5 
```

The BagIt specification has some optional metadata fields that can be present in the bag-info.txt file. These optional fields can
be passed on the command line:

```bash
gladstone --bagName ~/bagname --originDirectory ~/source --cryptoMethod md5 --sourceOrganization "Your Org"
```

You can also use gladstone in other node applications by passing the createBagDirectory function a JSON object:

```javascript 
var gladstone = require('gladstone');


gladstone.createBagDirectory (  { bagName: '/path/to/new/bag',
                                  originDirectory: '/path/to/dir/to/bag',
                                  cryptoMethod: 'md5'});
```

The function returns a promise that can be used to trigger behaviour after the bag has been made:

```javascript 
  return gladstone.createBagDirectory (  { bagName: process.cwd() + '/testbag',
                      originDirectory: process.cwd() + '/test',
                      cryptoMethod: 'md5'}).then(function(result) { 
                      console.log("Done making the bag");
                      });
                    
```
