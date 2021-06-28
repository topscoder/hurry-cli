
<p align="center">
<img src="https://user-images.githubusercontent.com/86197446/123507408-6d624900-d669-11eb-9606-4a022bc4a117.png" width="300" height="289" align="center">
</p>

Straight out of heaven. Hurry is a CLI tool to speed setting up [MoniGoMani](https://github.com/Rikj000/MoniGoMani) HyperStrategy & co. `#freqtrade` `#hyperopting` `#trading` `#strategy`

## Requirements

* Python 3.8+ is required
* These Python packages are required by Hurry:

### Install required Python packages using the [PIP package manager](https://pip.pypa.io/en/stable/installing/)

```shell
  pip3 install -r https://raw.githubusercontent.com/topscoder/hurry-cli/master/requirements.txt
```

## Installation

To install Hurry CLI:

```shell
  curl "https://raw.githubusercontent.com/topscoder/hurry-cli/master/hurry" --output hurry
```

(optional) Install [Freqtrade](https://github.com/freqtrade/freqtrade):

```shell
  python3 hurry install_freqtrade [--branch=develop] [--instal_dir=.]
```

(optional) Install [MGM Hyper Strategy](https://github.com/Rikj000/MoniGoMani):

```shell
  python3 hurry install_mgm [--branch=development] [--install_dir=.]
```

### Pro tip

Add an alias in your shell config (eg. ~/.zshrc) so you can use Hurry as `hurry` everywhere :)

```shell
  alias hurry="python3 /path/to/hurry-cli/hurry"
```

Or, if you use [`fish-shell`](https://fishshell.com) than `hurry.fish` is your friend.
Copy `hurry.fish` to your fish functions folder (`~/.config/fish/functions/hurry.fish`) and you are ready to roll!

## Usage

```shell

  $ python3 hurry --help

  Usage: python3 hurry [command] [options]

  CLI tool for Freqtrade and MGM Hyper Strategy.

  Options:
    -h, --help    display help for command

  Commands:
    install_freqtrade       [--branch=develop] [--target_dir=.]
    install_mgm             [--branch=development] [--target_dir=.]
    setup
    cleanup
    download_static_pairlist
    download_candle_data    [--timerange=yyyymmdd-yyyymmdd]
    hyperopt                [--timerange=yyyymmdd-yyyymmdd]
    hyperopt_show_results   EPOCH
    hyperopt_apply_epoch    EPOCH
    start_trader            [--dry_run=true]

```

### example: hurry setup

```shell
$ hurry setup
 _                                       _  _
| |__   _   _  _ __  _ __  _   _    ___ | |(_)
| '_ \ | | | || '__|| '__|| | | |  / __|| || |
| | | || |_| || |   | |   | |_| | | (__ | || |
|_| |_| \__,_||_|   |_|    \__, |  \___||_||_|
                           |___/

INFO:__main__: >> Freqtrade binary: `docker-compose run --rm freqtrade`
 + Let's save some answers to make our lifes easier

? Which way you want to use Freqtrade? source
? Please enter the default timerange you want to use 20201201-20210316
? Which HyperOpt Strategy do you want to use? MoniGoManiHyperStrategy
? Which HyperOpt Loss do you want to use? WinRatioAndProfitRatioLoss
? Which spaces do you want to HyperOpt? ['buy', 'sell']
? Please enter the default quotation you want to use USDT
? Please enter the amount of epochs you want to HyperOpt 800
? Do you want to also setup your exchange? Yes
? Which exchange do you want to use? binance
? Please enter the exchange API key ****************************************************************
? Please enter the exchange API secret:  ****************************************************************
 >> Configuration data written to .hurry file
 >> Exchange settings written to mgm-config-private.json

? Do you want to also setup your Telegram bot?  Yes
? Do you want to enable the Telegram Bot? Yes
? Please enter your Telegram Bot token:  **********************************************
? Please enter the chat ID:  1337
 >> Telegram bot settings written to mgm-config-private.json
```

## Development

### Yapf formatting

```shell
yapf hurry --diff
yapf hurry > hurry.diff
yapf hurry > hurry
```

### Generate pydoc

```shell
python3 -m pydoc -w ./hurry
```

### Timerange examples

|Trend    |Timerange            |
|-----    |---------            |
|Downtrend| `20210509-20210524` |
|Uptrend  | `20210127-20210221` |
|Sidetrend| `20210518-20210610` |
|Final    | `20210425-20210610` |
