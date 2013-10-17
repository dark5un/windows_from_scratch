# Windows from scratch (my way)

This is a copy (as an idea at least) of the original ["windows from scratch"][0] but without all the chef recipes and with specific versions of veewee / chef that work for me. The general idea is the same though so SPECIAL THANKS to [@hh][1] (Hippie Hacker) for showing the way!

## How to use this very small and simple "guideline"?

### 1. Install all the appropriate packages

This project needs [VirtualBox][2] and [Vagrant][3] installed. For the Ruby part, Ruby 1.9.3+ and Bundler gem are more than enough.
For the purpose of this example "7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso" ISO is needed and can be easily found from Microsoft download center as it is an evaluation version of windows 2008R2 for 180 days use.

If all the previous components exist in your development machine we can proceed.

### 2. Clone the project

`````
git clone windows_from_scratch
cd windows_from_scratch
bundle install
`````
### 3. Pick a windows version

`````
bundle exec veewee vbox templates | grep windows
`````

I prefer windows 2008R2 with winrm onboard.

`````
bundle exec veewee vbox define 'w2008r2-dev' 'windows-2008R2-serverstandard-amd64-winrm'
`````

### 4. Build the windows machine

`````
bundle exec veewee vbox build 'w2008r2-dev'
`````

And watch the magic... When it is done a reboot is needed for the virtualbox extensions to work properly. And this can be done from your console:

`````
be veewee vbox halt 'w2008r2-dev'
be veewee vbox up 'w2008r2-dev'

`````

### 5. Ready to go

Easy eh?

[0]: https://github.com/hh/windows-fromscratch
[1]: https://github.com/hh
[2]: https://www.virtualbox.org
[3]: http://www.vagrantup.com
