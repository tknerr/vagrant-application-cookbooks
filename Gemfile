source "https://rubygems.org"

gemspec

group :development do
  # We depend on Vagrant for development, but we don't add it as a
  # gem dependency because we expect to be installed within the
  # Vagrant environment itself using `vagrant plugin`.
  gem "vagrant", "1.2.7",
    :git => "https://github.com/mitchellh/vagrant.git",
    :ref => "v1.2.7"
  gem "berkshelf", "2.0.8"
  gem "vagrant-omnibus", "1.1.0"
end
