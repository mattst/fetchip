
## fetchip - Fetch IP Address


fetchip is a BASH script used to retrieve the wide area network (WAN) IPv4 address, this is sometimes referred to as the external IP address or the public IP address.

fetchip is different from other IP address fetching scripts because it gets the IP address from multiple web sources in order to verify that they are the same. The script uses a large list of web page sources which all provide the IP address in HTML or plain text. Once retrieved and confirmed, using a minimum of 2 sources, the IP address is printed to the terminal (stdout). The list of web page sources is held on Github and is downloaded each time the script is run so that the most up to date list is always used. Note that the list is randomized before use so that undue pressure is not placed on servers at the top of it.

Despite using 2 web sources by default fetchip still retrieves the IP address quickly. It uses a low timeout of 1.5 seconds (default) for each web source. When a web source is slow to respond, fetchip simply moves on to the next one. On average it will provide the IP address within 1-3 seconds, but often in less than a second.

The default timeout should be fine for most users but those using a high latency network (slow to respond) may want to use a longer timeout and then set up an alias so that that timeout is always used. Tweaking the timeout for your network's latency can result in improved performance (on average) for all users. Running the script repeatedly using different timeout values, and with verbose switched on, allows users to see how many sources timeout, if it is a lot then the timeout should be raised. A sensible range to try would be 0.75 to 3 seconds, e.g. `$ fetchip -v -t 0.75`, `$ fetchip -v -t 3` Bare in mind that, because the source list is randomized, different web sources are used each time the script is run so each timeout value should be tried several times.

Users are advised to read the manual, see the "Usage" section below.

#### Requirements

- UNIX / Linux / OSX (untested but should work)
- Bash
- Wget or Curl (download program used to retrieve the web sources)

It would be helpful if OSX users could let me know if fetchip works well with OSX.

#### Features

- Set the number of web sources to use for verification.
- Set the timeout for each web source (fractions of a second are permitted).
- Web sources list is downloaded from Github each time the script is run so the most up-to-date list is always used.
- Use a custom web sources list or a local copy (file or url).
- Verbose; display detailed output while the script runs.
- Bare output; use fetchip from within other scripts easily.
- List maintenance; check all web sources or test an url for use as a source.

#### Installation

- Download and extract the zip file.
- Make sure the `fetchip` file has executable permission.
- Copy the `fetchip` file into a directory which is in your `PATH`.

For example:

    $ cd fetchip_extracted_dir
    $ chmod 755 fetchip
    $ cp fetchip ~/Scripts/

If you have no user `~/Scripts/` directory or such like, and do not want to create one, then you should copy fetchip to the `/usr/local/bin/` directory instead. For example:

    $ cd fetchip_extracted_dir
    $ chmod 755 fetchip
    $ sudo cp fetchip /usr/local/bin/

#### Usage

fetchip has two help options.

- `-h` displays usage and help summary (effectively a cheat sheet).
- `--help` displays the full manual in the form of a built-in man page.

A man page, `fetchip_man_page`, is also supplied for users who would like to install it.

#### Contribute

If you have a web server and would like to allow it to be used as a source in the web sources list file then please follow the submissions link below. It needs only a 2 line PHP program and would generate very little bandwidth. If lots of people did so it would be helpful to the project.

Alternatively please feel free to submit new IP address providing web pages to be added to the web sources list file. You should first check they are not already in the latest web sources list file and that they are suitable for inclusion by using the `-u url` (Test Url) option.

[Submissions of urls to use as web sources](https://github.com/mattst/fetchip/issues/1)

#### License

Copyright (c) 2015 [mattst](https://github.com/mattst)

The fetchip script is licensed under [The GNU General Public License v.3](http://www.gnu.org/licenses/gpl-3.0.en.html).
