
<h1> <img src="https://raw.githubusercontent.com/hiteshlala/unzippy/master/logo.png" alt="Logo" width="50px" height="50px" style="vertical-align:middle"/> Unzippy </h1>

## __Status__ In Development

## A Node.js unzip library

  - Zero dependencies.

  - Uncompresses Deflate archives ( default for most zip libraries ).

  - Provides a directory listing of archive.

  - Selectively inflate individual items.

  - Does not verifiy size or calculate CRC32 of artifacts.



## Examples

Simplest extraction:
```javascript
  const { unzip } = require( '@hiteshlala/unzippy' );

  const source = 'path_some_zip_archive.zip';
  const dest = 'path_to_place_to_write_artifacts';

  unzip(  source, out )
  .then( console.log )
  .catch( console.error );

```

Add more options:
```javascript
  const { Unzippy } = require( '@hiteshlala/unzippy' );

  const source = 'path_some_zip_archive.zip';
  const dest = 'path_to_place_to_write_artifacts';

  // instantiate archive
  const z = new Unzippy({ 
    src: source, 
    dest: out
  });

  // get a directory listing
  const dir = z.getDir(); // returns an array
  console.log( dir.map( i => i.fName ) );

  // extract a single file - select by index of dir array
  z.extractSingle( 3 )
  .then( console.log )
  .catch( console.error );

  // extract entire directory
  z.unzip()
  .then( console.log )
  .catch( console.error );

```

## API

### Class Unzippy

- <b>new Unzippy( options )</b>

  - Takes an options object:

    ```javascript
    {
      src: < String: path to source archive >,
      dest: < String: path to where to unzip >,

      // planned options to come in future release:
      // logfile: < Boolean: create a log file>
      // verbose: < Allow logging to console >

    }
    ```

- <b>.getDir()</b>

  - Returns an Array containing an Object for each artifact in archive.


- <b>.extractSingle( id )</b>

  - Extracts a single artifact and returns a Promise.


- <b>.unzip()</b>

  - Extracts all artifacts and returns a Promise.


### unzip

- <b>unzip( src, dest )</b>

  - src - path to source archive

  - dest - path to where to unzip



## License

This project is covered by the [License found here.](/License)




