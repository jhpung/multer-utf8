# multer-utf8 [![NPM version](https://badge.fury.io/js/multer-utf8.svg)](https://badge.fury.io/js/multer) [![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat)](https://github.com/feross/standard)

`multer-utf8` is a solution for `latin1` charset issue.

`busboy` reads files with `latin1` charset by default, which causes some problems with `utf8` encoded files.

I fixed it by changing this part of code.

```javscript
try {
  busboy = Busboy({ headers: req.headers, limits: limits, ßpreservePath: preservePath, defParamCharset: charset })
} catch (err) {
  return next(err)
}
```

## Support `latin1`

```
/**
* mutler for utf8 
* default charset is `utf8`
*/ 

const multerWithUTF8 = multer({
  ...mutlerOptions
})

// multer for latin1
const multer = multer({
  ...multerOptions
  charset: 'latin1'
});
```
