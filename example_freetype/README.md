### Install Freetype Linux
Download and unpack a version from https://download.savannah.gnu.org/releases/freetype/.
Change directory to freetype folder. Create a build folder. Configure. Make. Install. Fix path issues using symlink.

```bash
wget https://download.savannah.gnu.org/releases/freetype/freetype-doc-2.9.tar.gz
cd freetype-2.9
mkdir build
cd build
../configure
make -j10
sudo make install
# Fix path issue using symlink
# This make is so that you don't need include flags `-I` when compiling.
sudo ln -s /usr/local/include/freetype2/ft2build.h /usr/local/include/
sudo ln -s /usr/local/include/freetype2/freetype /usr/local/include/
```

Check if library is installed
```bash
ls /usr/local/lib/ | grep freetype
ls /usr/local/include/ | grep freetype
```

Use link flag `-lfreetype` when compiling.
```C
#include <freetype2/ft2build.h>
#include FT_FREETYPE_H 
```
