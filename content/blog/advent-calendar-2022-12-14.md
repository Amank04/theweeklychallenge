---
title: "Advent Calendar - December 14, 2022"
date: 2022-12-14T00:00:00+00:00
description: "Advent Calendar - December 14, 2022."
type: post
image: images/blog/2022-12-14.jpg
author: Andinus
tags: ["Raku"]
---

## [**Advent Calendar 2022**](/blog/advent-calendar-2022)
### | &nbsp; [**Day 13**](/blog/advent-calendar-2022-12-13) &nbsp; | &nbsp; **Day 14** &nbsp; |
***

The gift is presented by `Andinus`. Today he is talking about his solution to [**"The Weekly Challenge - 187"**](/blog/perl-weekly-challenge-187). This is re-produced for **Advent Calendar 2022** from the original [**post**](https://andinus.unfla.me/pwc/challenge-187) by him.

***

<br>

## Task 1 - Days Together

<br>

Two friends, `Foo` and `Bar` gone on holidays seperately to the same city. You are given their schedule i.e. start date and end date.

To keep the task simple, the date is in the form DD-MM and all dates belong to the same calendar year i.e. between 01-01 and 31-12. Also the year is non-leap year and both dates are inclusive.

Write a script to find out for the given schedule, how many days they spent together in the city, if at all.

<br>

#### Example 1
    Input: Foo => SD: '12-01' ED: '20-01'
           Bar => SD: '15-01' ED: '18-01'

    Output: 4 days

#### Example 2
    Input: Foo => SD: '02-03' ED: '12-03'
           Bar => SD: '13-03' ED: '14-03'

    Output: 0 day

#### Example 3
    Input: Foo => SD: '02-03' ED: '12-03'
           Bar => SD: '11-03' ED: '15-03'

    Output: 2 days

#### Example 4
    Input: Foo => SD: '30-03' ED: '05-04'
           Bar => SD: '28-03' ED: '02-04'

    Output: 4 days

<br>

We convert the date to an integer representing number of days since the start of the year. Then simply subtract the minimum of end days with maximum of start days. The goal is to find the common days.

<br>

```perl
sub MAIN() {
    my @schedules = %( foo => <12-01 20-01>, bar => <15-01 18-01> ),
                    %( foo => <02-03 12-03>, bar => <13-03 14-03> ),
                    %( foo => <02-03 12-03>, bar => <11-03 15-03> ),
                    %( foo => <30-03 05-04>, bar => <28-03 02-04> );

    for @schedules -> %schedule {
        put days-together(%schedule) ~ " day(s)";
    }
}

#| date-to-int takes a date in "DD-MM" form and converts it to an
#| integer.
sub date-to-int(Str $date --> Int) {
    my @days-in-month = 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31;

    given $date.split("-").map(*.Int) {
        return $_[0] + ([+] @days-in-month[^ ($_[1] - 1)])
    }
}

#| days-together returns the days foo & bar are together.
sub days-together(%schedule --> Int) {
    my $foo-start = date-to-int %schedule<foo>[0];
    my $foo-end = date-to-int %schedule<foo>[1];

    my $bar-start = date-to-int %schedule<bar>[0];
    my $bar-end = date-to-int %schedule<bar>[1];

    return min($foo-end, $bar-end) - max($foo-start, $bar-start) + 1;
}
```

<br>

## Task 2 - Mask Code

<br>

You are given a list of codes in many random format.

Write a script to mask first four characters (a-z,0-9) and keep the rest as it is.

<br>

#### Example 1

    Input: @list = ('ab-cde-123', '123.abc.420', '3abc-0010.xy')
    Output: ('xx-xxe-123', 'xxx.xbc.420', 'xxxx-0010.xy')

#### Example 2

    Input: @list = ('1234567.a', 'a-1234-bc', 'a.b.c.d.e.f')
    Output: ('xxxx567.a', 'x-xxx4-bc', 'x.x.x.x.e.f')

<br>

Takes an array of codes as input. Loops over characters of a code and prints every character except first four matching the regex `"\w"`.

<br>

```perl
unit sub MAIN(*@codes);

for @codes -> $code {
    my Int $count;
    for $code.comb {
        given $_ {
            when /\w/ { print ($count++ < 4 ?? "x" !! $_) }
            default { .print }
        }
    }
    put "";
}
```

<br>

***

If you have any suggestion then please do share with us <perlweeklychallenge@yahoo.com>.

| &nbsp; [**Advent Calendar 2022**](/blog/advent-calendar-2022) &nbsp; |
