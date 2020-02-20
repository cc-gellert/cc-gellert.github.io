---
layout: post
title:      "Ruby CLI Data Gem: First Portfolio Project  "
date:       2020-02-20 17:43:18 +0000
permalink:  ruby_cli_data_gem_first_portfolio_project
---


It took me a bit longer than I thought it would, but I am ecstatic to say that today I am submitting my first Flatiron portfolio project, the ruby CLI Data Gem. While it may not look the most exciting, at the heart I'm very happy to have built something useful - at least to me!

My gem is called "Garden-Helper". It can be used to lookup spacing requirements for a list of over 60 plants as well as to plan out garden beds using the square-foot gardening method. For those unfamiliar with it, gardening traditionally uses row spacing for planting. However, for gardeners in areas with constrained space such as cities or suburbs, square-foot gardening is a more efficient usage of space. My gem scrapes the plant details from a table on a website page from [Mary's Heirloom Seeds](http://www.marysheirloomseeds.com/blogs/news/square-foot-garden-plant-spacing-chart). Users can lookup spacing requirements for plants by plant name, lookup the list of plants, and create new garden beds by name and square footage. They can then add and remove plants, delete plots or add more if they wish. The program adds and subtracts footage left and whether there is room to add the plants the user desires. 

As it is February in Cincinnati, all the hobby gardeners such as myself are itching to start planning what we're going to grow this year. Now, with this gem, I can do it from the command-line, easy-peasy. 

Of course, it is easy-peasy now but it wasn't necessarily so easy to build. I originally targeted a webapp called Seed to Spoon for this as it had more in-depth information that I would have liked to incorporate. Unfortunately, the website, it turns out, in actually unscrapeable! So, I had to change targets and reform my Scraper and Plant classes to adjust. Building the classes themselves was not too difficult as I only had four: CLI class, GardenPlot class, Plant class, and Scraper class. The Scraper class offered some trouble due to the scraping target change, but the Plant class is really quite "dumb" - not dynamic and has only a few methods such as #print_self and #display. The GardenPlot class was a bit more complicated. But the real trouble was the CLI class. 

Firstly, I had to capture input and convert it correctly. As plants sometimes have two words in the name and needed to match how they were in the system to find exactly, every plant input had to be put through gets.strip.split(" "), then each word had to be capitalized, and then rejoined into a string. Any number inputs had to be converted into an integer from a string. The Scraper class also went through this process for each Plant object in the table. To complicated things the chart also included ranges (i.e. 2-4 plants per square foot). I opted to go for the lowest recommended number as the program can't do arithmetic with ranges, and while you can always plant more seedlings if some don't take, it's much more of a pain to have to uproot them if you have planted them too close together. 

The methods for CLI #ask_for_input and #edit_plot also quickly became VERY LONG due to how many options the main menu had. I first built out the #ask_for_input method, then pulled out what I could into smaller helper methods to cut down on the length of the method. I later did the same with the #edit_plot method, which was originally a helper method to #ask_for_input that quickly became almost 30 lines long. I also wanted to program to be as flexible as it could, so I added in multiple options for the case input portion of the #ask_for_input method. 

Of course, after that I needed to add error handling for all the methods: if a plant isn't found, if a user tries to remove plants that aren't on that plot, or add a plant that doesn't exist, or remove more plants than there are on a plot, or add more plants than there is room for, edit a plot that doesn't exist, etc. I put in as much error handling as I could think of, but it may be that a truly determined user could break the program anyhow. 

Either way, this is a useful little gem, and once it (finally!) warms up here in Cincinnati, I can't wait to use it for my spring gardening. 
