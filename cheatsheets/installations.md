
# Enable writing on NTFS (OUTDATED)

Adapted from [here](http://apple.stackexchange.com/questions/106589/write-in-ntfs-using-mavericks).
```bash
brew update
brew install ntfs-3g
brew cask install osxfuse
sudo mv /sbin/mount_ntfs /sbin/mount_ntfs.orig
sudo ln -s /usr/local/sbin/mount_ntfs /sbin/mount_ntfs
```

# Switch the Finder icon in the Dock:

Icon by [Esxxi](http://esxxi.me/)

```bash
cp ~/.home/conf/finder.png /System/Library/CoreServices/Dock.app/Contents/Resources/finder.png
ls -l /private/var/folders/*/*/*/com.apple.dock.iconcache
rm /private/var/folders/*/*/*/com.apple.dock.iconcache
killall Dock
```

# MongoDB

### Install mongo
```bash
brew install mongodb
sudo mkdir -p /data/db
sudo chown $USER /data/db
mongod
mongo
```

### Run mongod on restart
```bash
#To have launchd start mongodb at login:
ln -sfv /usr/local/opt/mongodb/*.plist ~/Library/LaunchAgents
#Then to load mongodb now:
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.mongodb.plist
#Or, if you don't want/need launchctl, you can just run:
mongod --config /usr/local/etc/mongod.conf
```

### Example
```mongo
show dbs
use DATABASENAME
db
show collections
var col = db.aCollection
col.find()
col.ensureIndex({id:1}, {unique:true})
col.insert({})
col.insert({id:1})

var a = col.findOne({id:1})
a.x = 'wat'
col.update({id:a.id},a)

col.remove({})
col.find()

exit
```


# MySQL

### Install mysql
```bash
brew install mysql
mysql.server start
mysql -uroot
```

### Create database
```
CREATE DATABASE dbname;
exit
```

### Dump something inside
```bash
mysql -uroot dbname < dbname.mysql
```

# pip
Python modules installations

```bash
pip install eyeD3 eyeD3-pip
pip install beautifulsoup4
pip install PIL
```
