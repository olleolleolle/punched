# Punchcard
## Minimal time tracking tool for cli

[![Build Status](https://travis-ci.org/pstaender/punchcard.svg?branch=master)](https://travis-ci.org/pstaender/punchcard)

### Requirements

  * ruby 2+
  * unix bash (maybe windows works as well?!?)

### Install

```sh
  $ gem install punched
```

Or choose your preferred filename and location:

```sh
  $ curl https://raw.githubusercontent.com/pstaender/punchcard/master/lib/punchcard.rb > /usr/local/bin/punched
  $ curl https://raw.githubusercontent.com/pstaender/punchcard/master/bin/punched >> /usr/local/bin/punched
  $ chmod +x /usr/local/bin/punched
```

### Usage

#### Start Project

```sh
  $ punched start "Punchcard (programming)"
```

#### Wildcard

Save keystrokes by using wildcard. The last active project, which matches the pattern (case insensitive) will be selected:

```sh
  $ punched start "Punch*"
```

#### Stop Project

```sh
  $ punched stop "Punch*"
```

#### Toggle

Toggle between start and stop:

```sh
  $ punched toggle "Punch*"
```

#### Status

```sh
  $ punched status "Punch*"

    Punchcard (programming)
    01:10:09
```

#### List details

```sh
  $ punched details "Punch*"

    Punchcard (programming) (stopped)

    00:00:08	2017-05-07 08:16:06 - 2017-05-07 08:16:14
    00:04:35	2017-05-07 08:22:02 - 2017-05-07 08:26:37
    ...
    ========
    01:10:04	(total)
```

#### Set Hourly Rate

```sh
  $ punched set "Punch*" hourlyRate 250€
```

#### Total time in seconds

```sh
  $ punched total "Punch*"
```

#### Rename and delete Project

```sh
  $ punched rename "Old Title" "New Title"
```

```sh
  $ punched remove "Punchcard (programming)"
```


#### List all projects with total time in CSV format

```sh
  $ punched all

    "project","status","last active on","total duration","hourly rate","earnings"
    "Website","stopped","2017-05-07 15:50:00","04:06:00","250.0 €","1025.00 €"
    "Punchcard (programming)","stopped","2017-07-11 12:47:42","01:10:04","",""
```

You can use `all` with any other action as well, e.g. `punched all stop` to stop all running projects.

Hint: Use your favorite output formatter to get a nicer project summary of your choice; e.g. with [csv2md](https://www.npmjs.com/package/csv2md):

```sh
  $ punched all | csv2md --pretty

    | project                   | status  | last active on      | total duration | hourly rate | earnings |
    |---------------------------|---------|---------------------|----------------|-------------|----------|
    | Website                   | stopped | 2017-05-07 15:50:00 | 04:06:00       | 250.0 €     | 1025.0 € |
    | Punchcard (programming)   | stopped | 2017-05-07 12:47:42 | 01:10:04       |             |          |
```

### Store projects files in a custom folder and sync them between computers

By default, PunchCard will store the data in `~/.punchcard/`. Define your custom destination with:

```sh
  export PUNCHCARD_DIR=~/Nextcloud/punchcard
```


### Tests

```sh
  $ bundle exec rspec
```
