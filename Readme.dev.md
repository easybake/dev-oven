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

#populate cache here: knife source ingredient *

ln -s /path/to/cache .chef/cache

chef-solo -c .chef/solo.rb
