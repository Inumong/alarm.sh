Alarm with Weather
=====

About
-----

Alarm is a small shell script that can aid you in alerting you of things at
specified times. It does this by displaying a message in X (using one of
the variety of X message displaying tools) at the time of the alert.

It supports a very flexible time input format (i.e. 'tomorrow', '5 may
2005', 'tomorrow 20:00'), one-time alerts and repeated alerts.


Installation and setup
----------------------

### Requirements

Alert requires the following to be installed:(X11설치)
		
*   X11
		
And at least ONE OF THE FOLLOWING programs to be installed: (이 프로그램들 중 적어도 하나는 설치해야합니다.)

*   xmessage 
*   dialog in combination with a terminal emulator 
*   gdialog


### Installation

1.  Copy the 'alarm' script to a directory that is present in the path.
2.  Add the following line to the .xinitrc file in your home directory:
		
    alarm --daemon&
	
Usage
-----

Alarm can run in two modes. The first is the daemon mode in which it will
notify you of events when they occur and the other is the edit mode through
which you can add, change, delete and list events. Alarm in daemon mode
should be run under X.

Below is the output of alarm --help:
	
	Usage: alarm [ACTION] [PARAMETERS]                          
                                                               
	Actions:
	
	  Additionally required parameters are listed in parenthesis.
	  
	  -n, --new    (-t, -m)       Create a new alert at timespec   
	  -c, --change (-i, -t, -m)   Change the alert identified by id
	  -d, --delete (-i)           Delete the alert identified by id
	  -l, --list   ([-i])         List alert(s)                    
		  --daemon            Start the alert daemon           
		  --weather           Show weather
                  --sun               Show sunrise and sunset														   
	Parameters                                                     
	  -t, --timespec TIMESPEC     Date/time specification at which 
								  the alert should be triggered    
	  -m, --message MESSAGE       Message that should be displayed 
	  -i, --id ID                 Alarm ID that should be changed, 
								  deleted or listed                
	  -f, --file FILE             Use FILE as alarm file instead of
								  the default ~/.alarms            
	  -r, --repeat                Repetative alarm                 

### Adding alerts

Here are some examples of adding one-time alerts:
	
	$ alarm -n -t "1 april 2005" -m "Watch out for any pranks." 
	$ alarm -n -t "20:15" -m "Appointment with Some Person" 
	$ alarm -n -t "+15 minutes" -m "Call back client" 
	$ alarm -n -t "tomorrow" -m "Do a good deed" 

Here are some examples of adding repeating alerts:
	
	$ alarm -n -r -t "friday" -m "Every Friday: beer-drinking competition"
	$ alarm -n -r -t "0:00" -m "Hey\! It's twelve o'clock. Get to sleep\!"

### Listing set alarms

Here is an example of the output of alerts:

	$ alarm -l

	 id | m |                 date | message
	----+---+----------------------+---------------------------------------------
	  1 |   |     2005-04-01 00:00 | Watch out for any pranks.
	  2 |   |     2005-04-11 20:15 | Appointment with Some Person
	  3 |   |     2005-04-11 16:31 | Call back client
	  4 |   |     2005-04-12 16:16 | Do a good deed
	  5 | r |               friday | Every Friday: beer-drinking competition
	  6 | r |                 0:00 | Hey! It's twelve o'clock. Get to sleep!

	
The fields are:

    id      = Notification ID (use with -i).
    m       = Mode ('n'ormal, 'r'ecurring).
    date    = The absolute ('2005-04-11 20:00') or relative ('friday') date & 
              time of the event.
    message = The message to show when the event is triggered.

### Changing alerts

Here is an example of how to change an alert:
	
	$ alarm -c -i2 -t "thursday" -m "Thursday beer-drinking competition tonight"

### Deleting alerts

Here is an example of deleting an alert.

	$ alarm -d -i2
	
### show sunrise, sunset
    
        $ alarm --sun
	
## show weather

        $ alarm --weather

Copyright
---------

Copyright (C), 2005-2013 Ferry Boender. Released under the General Public
License For more information, see the COPYING file supplied with this program.                                                          

