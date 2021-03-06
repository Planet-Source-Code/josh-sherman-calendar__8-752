﻿<div align="center">

## Calendar


</div>

### Description

This script displays a calendar (built out of a table) for the specified month and year, and allows you to skip forward and backwards between months. This is a small component of another (larger) project of mine.
 
### More Info
 
month and year on the Querystring

A calendar for the specified month

This code might make you want to be a better person


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Josh Sherman](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/josh-sherman.md)
**Level**          |Intermediate
**User Rating**    |4.8 (19 globes from 4 users)
**Compatibility**  |PHP 4\.0
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__8-1.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/josh-sherman-calendar__8-752/archive/master.zip)

### API Declarations

```
* Copyright (C) 2002 Calendar by Josh Sherman <josh@cleancode.org>
 *
 * This source and program come as is, WITHOUT ANY WARRANTY and/or
 * WITHOUT ANY IMPLIED WARRANTY.
 *
 * Users of said software should realize that they cannot and will not hold
 * myself or Clean Code reliable or responsible for any purpose WHAT SO EVER.
 * Please read all documentation and use said software responsibly.
 *
 * ANY COMMERCIAL REDISTRIBUTION OR ANY PROPRIETARY REDISTRIBUTION OF THIS OR
 * ANY SOURCE FROM CLEANCODE.ORG IS PROHIBITED UNDER CERTAIN CONDITIONS AND
 * SHALL NOT BE RE-SOLD OR REDISTRIBUTED WITHOUT PRIOR AGREEMENTS WITH
 * CLEANCODE.ORG
 *
 * I can be reached by electronic mail if there are any questions or concerns
 * about this software, or any other software that was written and / or
 * distributed by Cleancode.org <josh@cleancode.org>
 *
 * Software supplied and written by Josh Sherman, http://www.cleancode.org/
```


### Source Code

```
<?
/* Print out the HTML headers, and calendar header */
echo "<HTML>\n"
 . " <HEAD>\n"
 . " <STYLE>\n"
 . "  BODY, TD, TH\n"
 . "  {\n"
 . "   font-family: Verdana;\n"
 . "   font-size: 8pt;\n"
 . "  }\n"
 . " </style>\n"
 . " </head>\n"
 . " <BODY>\n";
/* Grab the month and year */
if ($month == "" || $year == "")
 {
 $this_month = date("n");
 $month_name = date("F");
 $this_year = date("Y");
 }
else
 {
 $this_month = date("n", mktime(0, 0, 0, $month, 1, $year));
 $month_name = date("F", mktime(0, 0, 0, $month, 1, $year));
 $this_year = date("Y", mktime(0, 0, 0, $month, 1, $year));
 }
/* This is for the navigation */
$last_month = $this_month - 1;
$next_month = $this_month + 1;
/* Same with all this stuff */
if ($last_month == 12)
 $last_year = $this_year - 1;
else
 $last_year = $this_year;
/* DITTO!!! */
if ($next_month == 1)
 $next_year = $this_year + 1;
else
 $next_year = $this_year;
/* Display the calendar header */
echo " <CENTER><B>Calendar for $month_name, $this_year</b></center><BR>\n"
 . " <TABLE align=\"center\" border=\"2\" bordercolor=\"#000000\" cellpadding=\"5\" cellspacing=\"0\">\n"
 . "  <TR bgcolor=\"#DDDDDD\">\n"
 . "  <TH width=\"50\">Sun</th>\n"
 . "  <TH width=\"50\">Mon</th>\n"
 . "  <TH width=\"50\">Tue</th>\n"
 . "  <TH width=\"50\">Wed</th>\n"
 . "  <TH width=\"50\">Thu</th>\n"
 . "  <TH width=\"50\">Fri</th>\n"
 . "  <TH width=\"50\">Sat</th>\n"
 . "  </tr>\n";
/* Grab the first day of the month, and total days */
$first_day = date("w", mktime(0, 0, 0, $this_month, 1, $this_year));
$total_days = date("t", mktime(0, 0, 0, $this_month, 1, $this_year));
/* Start on the day of the first week */
$week_num = 1;
$day_num = 1;
/* While the day of the week isn't '7' */
while ($week_num <= 6)
 {
 echo "  <TR>\n";
  /* Loop through the week days */
  for ( $i = 0; $i <= 6; $i++ )
   {
   /* If it's the first week then... */
   if ($week_num == 1)
    {
    /* If it's not the first day yet, then use a space */
    if ($i < $first_day)
     $the_day = " ";
    /* If it is the first day, then start with a '1' */
    else if ($i == $first_day)
     {
     $the_day = 1;
     }
    }
   else
    {
    /* If we're past the total days, then use spaces */
    if ($the_day > $total_days)
     $the_day = " ";
    }
   /* Display the day (or space) */
   echo "  <TD height=\"50\" width=\"50\" valign=\"top\">$the_day</td>\n";
   /* Incrememnt the day of the month */
   if ($the_day != " ")
    $the_day++;
   }
 echo "  </tr>\n";
 /* Increment the week number */
 $week_num++;
 }
/* Finish off with closing out our tags */
echo " </table>\n"
 . " <BR>\n"
 . " <CENTER>\n"
 . "  << <A href=\"?month=$last_month&year=$last_year\">Last Month</a> || <A href=\"?month=$next_month&year=$next_year\">Next Month</a> >>\n"
 . " </center>\n"
 . " </body>\n"
 . "</html>\n";
?>
```

