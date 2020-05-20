# bday

![screenshot](https://i.imgur.com/3jPwKR7.png)

## Install
~~~~shell
wget https://raw.githubusercontent.com/kkristof200/bday/master/bday -O /usr/local/bin/bday && chmod u+x /usr/local/bin/bday
# or
curl https://raw.githubusercontent.com/kkristof200/bday/master/bday > /usr/local/bin/bday && chmod u+x /usr/local/bin/bday
~~~~

## Usage
~~~~
Examples
bday -a 'john doe/5.13'
bday t -s


Usage:          bday [options]

today, t        Desctiption: Show birthdays for today
--full, -f      Description: pass together with today, to show full names
--short, -s     Description: pass together with today, to show short names

--add, -a       Desctiption: Add new birthday(s)
                Format:      name/month.year
                             or if file
                             '\\n' separated lines, each line a birthday in the format from above
                Usage:       bday -a 'john doe/4.23'
                             or
                             bday -a ~/path/to/file_name.txt
~~~~

## ADD TO POWERLEVEL10K AS PROMPT ELEMENT
Download bdaysh, since it's fasteer for this task
~~~~shell
cd /usr/local/bin && wget https://raw.githubusercontent.com/kkristof200/bday/master/bdaysh && chmod u+x bdaysh
~~~~
~~~~
SPEED COMPARISON bday v bdaysh

#bday
real    0m0.061s
user    0m0.034s
sys     0m0.020s

#bdaysh
real    0m0.037s
user    0m0.008s
sys     0m0.019s
~~~~
Open iterm and run
~~~~shell
nano ~/.p10k.zsh
~~~~

Add bday to prompt elements
~~~~shell
typeset -g POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(
  ... other elments ...
  bday
  ... other elments ...
)
~~~~

Add this function to the bottom
~~~~shell
function prompt_bday() {
  bday_str=$(bdaysh)

  if [ "$bday_str" != "" ]; then
    p10k segment -f 208 -i '' -t $bday_str
  fi
}
~~~~
 - is the cake font used from [nerd-fonts](https://github.com/ryanoasis/nerd-fonts). Either install it and add it to terminal/iterm or change the icon in the script above

Close editor and run
~~~~shell
source ~/.p10k.zsh
~~~~

## Dependencies
python
