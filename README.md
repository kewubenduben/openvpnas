# OpenVPN Access Server Chef Cookbook

[![Build Status](https://travis-ci.org/rjocoleman/openvpnas.svg?branch=master)](https://travis-ci.org/rjocoleman/openvpnas)

A Chef cookbook to install and do basic configuration OpenVPN Access Server.

Includes support for:

* Own company name
* SSL certificate (optional)
* Backup and restore to/from S3 (optional).

Designed (very loosly) for use in AWS.


# Attributes

Attributes listed with their default values:

```ruby
default['openvpnas']['url'] = 'http://swupdate.openvpn.org/as/openvpn-as-2.0.6-CentOS6.x86_64.rpm'
default['openvpnas']['dir'] = '/usr/local/openvpn_as/'
default['openvpnas']['company_name'] = ''
default['openvpnas']['logo'] = ''
default['openvpnas']['backup']['enabled'] = false
default['openvpnas']['backup']['bucket'] = ''
default['openvpnas']['ssl'] = false
default['citadel']['bucket'] = node['openvpnas']['backup']['bucket']
```

`default['citadel']['bucket']` is the source for the SSL certificate and private key.


# Recipes

* `openvpnas::default` - recipe to install, configures and enables+runs.
* `openvpnas::backup` - creates backup script and schedules it in the cron.
* `openvpnas::restore` - restores from backup on convergence.


## Contributing

* File bug reports via GitHub issues.
* Pull requests are welcome.

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
