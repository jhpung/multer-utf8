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

## Options

|Key| Description|
|--|--|
|dest or storage| Where to store the files|
|fileFilter| Function to control which files are accepted|
|limits| Limits of the uploaded data|
|preservePath| Keep the full path of files instead of just the base name|
|charset| charset of files. for example `latin1`, `utf8`|

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
