# Tech Test Makers WK10 - Gilded Rose 

This Kata was originally created by Terry Hughes (http://twitter.com/TerryHughes). It is already on GitHub [here](https://github.com/NotMyself/GildedRose). See also [Bobby Johnson's description of the kata](http://iamnotmyself.com/2011/02/13/refactor-this-the-gilded-rose-kata/).

The purpose of this exercise was to take some legacy code and refactor it, using a coherent TDD process and making sure it's easier to read and edit/update. 

## Specification 
* The Gilded Rose does a stock take every night on items it sells.
* Each item has a sell_in value and quality value.
* The majority of items decrease in sell_in and quality value every night (with some exceptions on special items).
* On the item "Elixir of the Mongoose" the sell_in and quality value reduces by -1 on a stock update.
* The below example shows the legacy code run in IRB.

```
$ irb 
require './lib/gilded_rose'
require './lib/item'
items = [Item.new(name="Elixir of the Mongoose", sell_in=5, quality=7)]
inn = GildedRose.new(items)
inn.update_quality()

=> [#<Item:0x00007fbde811c210 @name="Elixir of the Mongoose", @sell_in=4, @quality=6>] 
```

## My Approach 

There are multiple languages you can attempt this challenge in and my preference was Ruby. I decided to focus on a **test-first approach**, making sure first that the current code was working. 

First, I wrote tests covering all scenarios for the legacy code. This gave me a thorough understanding of the program before I started refactoring and meant the testing process was accelerated as the existing tests written just needed to be updated.

Starting point was to split the update_quality method into two methods: update_quality_value and update_sell_in_value.
This would give me a clearer view on how to structure the additional methods to account for each sceanrio on the various items and unearth further refactoring opportunities. 

End goal, single public method being required to update the stock of the famous Gilded Rose!

## Running Gilded Rose 

1. Clone this repo to your local dir.
2. Make sure you have RSpec installed ```gem install rspec```
3. Run ```rspec``` in your cmd line to run all tests which should pass first time.
4. You can test-drive the Giled Rose yourself! Use IRB.

## Makers Review Of My Tech Test 

* Great work on your Gilded Rose submission, I thought it was very well done. Here are just a couple of notes on it:
* Nice work on covering the existing code with tests before getting started with the refactoring!
* Nice use of switches to make really well readable methods, over if/elses. I think your methods in GildedRose are really concise and cleanly written.
* There are a couple of magic numbers dotted around that you could also assign to constants: https://en.wikipedia.org/wiki/Magic_number_(programming)
* You probably don’t need multiple describe blocks for #update_quality tests, as the context blocks separating the tests for different items will be enough organisation to make them easily readable.
* Really comprehensive unit testing, nice work.
