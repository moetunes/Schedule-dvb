##Schedule DVB recordings

There's two bash scripts with declarations at the top. Uses the channels
in a channel.conf, which should be edited so the channels don't have a space in
the name.

###TV_SCHED

**The interface to the schedule file.**

It displays the available channels from the channel.conf, 
shows any existing schedules, gives an example of an entry, 
takes a new entry and checks for time conflicts and format, 
adds the entry to the schedule file then loops in case there's more entries.

Press enter to exit when done.

Date is YearMonthDay with Month and Day zero padded.

e.g. 20120601

No leading zeros on the time and time is in 24hr format

e.g. 745 1130 1900

Press   *r space number*   to remove an entry from the list

For convenience:

    * one dot for today

    * two dots for tomorrow

    * three dots for the day after tomorrow


Declarations

    * declare CHANNEL_CONF="$HOME/Mychannels.conf"

	* Make sure this is the same in tv-record

    * declare SCHED_FILE="$HOME/.sched-tv"

    * File which has the schedule


###TV_RECORD

**Sits in the background periodically checking the schedule file for something to record.**

Declarations

	* declare -i DVB_DEVICE_NUM="0"

	* /dev/dvb/adapter? - should be ok with zero if there's only one dvb device

	* declare CHANNELS_CONF="$HOME/Mychannels.conf"

 	* Make sure this is the same in tv-sched

 	* declare SAVE_FOLDER="$HOME/TV/tele"

	* Directory to save recordings to.

	* declare SCHED_FILE="$HOME/.sched-tv"

	* File which has the schedule

	* declare ZAP_COMMAND="tzap"

	* tzap for dvb-t, szap for dvb-s etc

	* declare -i SLEEP=15

	* Time (in seconds) to wait between checks for something to record

**Bonus for Gold Members**

###TV_SELECT

**Select DVB channel to watch with mplayer**

Reads the channels from ~/.mplayer/channels.conf

and displays them separately on buttons using xmessage

for easy selection.

Opens selected DVB channel in mplayer.