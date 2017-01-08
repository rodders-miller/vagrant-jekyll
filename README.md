# vagrant-jekyll

Jekyll Vagrant Box based on the ubuntu/trusty64 base box.

The Vagrant file uses the libvirt provider, so use a base-box suitable or covertusing the box coversion plugin for vagrant.

The box will fire up a new Jekyll blog and serve it ready to use.  Access is via http://localhost:4000

The intended use is clone a Git Hub page repo into the box and then use it to check the build / work on the site and posts locally.

When cloning a site from git first run 'bundler install'  to fetch and install any missing gem that are listed in the Gemfile 









