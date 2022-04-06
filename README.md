# beancount-black [![CircleCI](https://circleci.com/gh/LaunchPlatform/beancount-black/tree/master.svg?style=svg)](https://circleci.com/gh/LaunchPlatform/beancount-black/tree/master)
Opinionated code formatter, just like Python's [black](https://pypi.org/project/black/) code formatter but for Beancount

## Features

- **MIT licensed** - based on [beancount-parser](https://github.com/LaunchPlatform/beancount-parser), a [Lark](https://github.com/lark-parser/lark) based LALR(1) Beancount syntax parser
- **Extremely fast** - 5K+ lines file generated by `bean-example` can be formatted in around 1 second
- **Section awareness** - entries separated by Emac org symbol mark `*` will be formatted in groups without changing the overall structure
- **Comment preserving** - comments are preserved and will be formatted as well

# Sponsor

The original project beancount-black was meant to be an internal tool built by [Launch Platform LLC](https://launchplatform.com) for 

<p align="center">
  <a href="https://beanhub.io"><img src="https://github.com/LaunchPlatform/beancount-black/raw/master/assets/beanhub.svg?raw=true" alt="BeanHub logo" /></a>
</p>

A modern accounting book service based on the most popular open source version control system [Git](https://git-scm.com/) and text-based double entry accounting book software [Beancount](https://beancount.github.io/docs/index.html).
While SaaS businesses won't be required to open source an internal tool like this, we still love that the service is only possible because of the open-source tool we are using.
We think it would be greatly beneficial for the community to access a tool like this, so we've decided to open source it under MIT license, hope you find this tool useful 😄

## Install

To install the formatter, simply run

```bash
pip install beancount-black
```

## Usage

Run

```bash
bean-black /path/to/the/file.bean
```

Then the file will be formatted.
Since this tool is still in its early stage, a backup file at `<filepath>.backup` will be created automatically by default just in case.
The creation of backup files can be disabled by passing `-n` or `--no-backup` like this

```bash
bean-black -n /path/to/the/file.bean
```

It's highly recommended to use [BeanHub](https://beanhub.io), Git or other version control system to track your Beancount book files before running the formatter against them without a backup.

If you want to run the formatter programmatically, you can do this

```python
import io

from beancount_parser.parser import make_parser
from beancount_black.formatter import Formatter

parser = make_parser()
formatter = Formatter()

tree = parser.parse(beancount_content)
output_file = io.StringIO()
formatter.format(tree, output_file)
```

## Future features

- Add argument for renaming account and commodity
- Add argument for following other files from `include` statements and also format those files
 
Feedbacks, bugs reporting or feature requests are welcome 🙌, just please open an issue.
No guarantee we have time to deal with them, but will see what we can do.
