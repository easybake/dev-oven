
```
export DEV=1
export PATH=/opt/chef/bin:/opt/chef/embedded/bin:$PATH
git submodule init
git submodule update
cd repo/cloud-kitchen
bundle install 
bundle exec berks install --path ./cookbooks/
cd cookbooks
for x in `ls ../../../cookbooks/` ; do rm -rf $x ; ln -s ../../../cookbooks/$x . ; done
cd ..
# depending on what ingredients you will use
knife source ingredient chef client
knife source ingredient chef server
knife source ingredient emacs
knife source ingredient git
knife source ingredient sublimetext
knife source ingredient ubuntu
knife source ingredient synergy
knife source ingredient vagrant
knife source ingredient vim
knife source ingredient virtualbox
knife source ingredient visual studio
knife source ingredient windows

# If you already have a cach
ln -s /path/to/cache .chef/cache

chef-solo -c .chef/thesoloconfigyouwanttotry.rb
```
