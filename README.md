# Gallery
A visual portfolio generator with web hosting for your photo albums. Requires no 3rd party libraries or installations.

## Making your own gallery in less than 5 minutes
- Fork original repo: https://github.com/andyzg/gallery.git
- Clone the repository through terminal by running
`git clone git@github.com:{YOUR_USERNAME}/gallery.git`
- Replace contents of `/photos` with all of your albums. 
**Example**:
```
/photos
  /mockups
    IMG_0123.jpg
    IMG_0124.jpg
  /portrait
    IMG_1234.jpg
    IMG_1235.jpg
```

- Open the folder in finder and **double click** `setup.command`. (If any issue, see observation at the end of the file)This will go through all of your albums and create a `config.json` file for you. This file allows the generator to know which photos will be hosted on your website.
- Personalize the contents at the bottom of `_config.yml`.
- Commit all of your changes and then push all of your changes to Github by running
```
$ git checkout -B gh-pages  # This creates a branch that will be hosted at {username}.github.io/gallery
$ git commit -am "Create my first gallery"  # This saves all of your changes
$ git push origin gh-pages  # This pushes your gallery to be hosted!
```
- Check out your site at {username}.github.io/gallery

*Important notes:* To ⏭speed⏭ up the loading time of your gallery, please make sure to compress your images.
If you want Google Analytics, replace `_includes/ga.html` with your own snippet.


## How It Works
There are two important pieces to gallery:

### Album Generation
`setup.command` goes through all of the folders in your `/photos/` directory. It collects all of the file paths of each photo in each album. It aggregates all of this data into one key file called `config.json`.

### Client-side Generation
Once you've created your `config.json`, the website can now use that file to figure out which photos to show. It uses JavaScript(ES6) to layout your photos, grouping all of the photos per album.

## Customizing your Gallery
Gallery supports 3 different kinds of layouts: rows, squares and columns. You can choose which type of layout you want to use by setting the `layout` variable in `script.js` to be either `SQUARES`, `ROWS` or `COLUMNS`.

Each different layout has both its own and shared set of configuration options.

### Shared
- `spacing` (Integer): The vertical and horizontal distance that separates each photo from all adjacent photos. *Defaulted to 10*.
- `shuffle` (Boolean): Toggle to shuffle or not to shuffle the photos. *Default is `false`*.

### Column Configuration
- `columns` (Integer): The number of columns for the layout. *Default is `3`*.

### Square Configuration
- `columns` (Integer): The number of columns for the layout. *Default is `3`*.
- `maxHeight` (Integer): The max height in px for each photo. *Default is `400`*.

Columns takes priority if both are set.

### Row Configuration
- `maxHeight` (Integer): The max height in px for each photo. *Default is `400`*.

### Instagram
- `instagram` (String): Your Instagram handle. If no string is passed, no footer
  is rendered.

### Observations
For those of you having issues running `setup.command`, try only this line in a Powershell window (Python must be installed in the machine):
``` 
python "C:\Users\Cristian Pique\Desktop\gallery\tools\setup.py"  
```

