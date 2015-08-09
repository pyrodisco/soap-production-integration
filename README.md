# soap-production-integration

This repository is an integration between soapmaker and quickbooks software.

## History
My wife runs a home based soap making business.  She recently formed a LLC and as a result needed to begin tracking all of her inventory, expenses, and income through professional accounting software for insight and tax purposes.  She had QuickBooks 2011 already and since I had worked to keep track of finances before, I nominated myself to help in this area.

After taking an initial look at how she does her business, I found some problems pretty quickly.  First she uses a tracking software called SoapMaker.  Soapmaker allows her to input her raw materials, amounts, and costs.  It also allows her to record her recipes and then subsquently make batches of soap from them.  This then reduces inventory and tells her how much the cost of the soap she's making.  Since this software uses the appropriate ubiquitous language of their users, she naturally understands how this works.  

However translating this into quickbooks doesn't come as naturally to her.  Couple this with the fact that the version of Quickbooks (pro version) she has doesn't natively support manufacturering and she doesn't want to invest the money to purchase the premier version, we needed to find another solution.  

Since I'm also a software architect, I see an oppurtunity here to bridge the gap between these two software products.  The thought is to allow her to use the soapmaker software to track all her raw materials, works in progress (batches curing), and finished goods (soaps ready for sale) and then integrate those costs (in terms of credits and debits to journal entries) in quickbooks.  This way quickbooks would reflect the appropriate transactions, without her having to understand the details of invnetory tracking in quickbooks.  She can just use soapmaker while making her soap the the accounting portion of it just "happens." 

As a sidenote, I'm also going to be building out her website for sale of this soap.  This is probably going to include the website, etsy, and social media.  The "extended" thought here would be as "finished goods" becomes populated the for sale portion of the web presence reflects actual inventory.  Also we could automatically post to twitter, facebook, etc. when new products are avaiable.  This would all be triggered from events inside the soapmaker software.  

I find this the appropriate place to bring out my domain driven design (DDD) hat and see what we can accomplish here.

## Bounded Contexts

So I see three main contexts that are going on here. 
1. Tracking and Making Soap - Handled already by soapmaker software.  This would be considered a legacy applcation and most likely going to be implemented using an anti-corruption layer. 
2. Accounting for inventory - Handled by quickbooks software. This would be considered a legacy applcation and most likely going to be implemented using an anti-corruption layer. 
3. Publishing for sale.

## The software

1. SoapMaker.  It's a access database.  Need I say more?  But, it works for her and is very popular in the soap making community.  Sometimes the cards are already dealt for you and you have to make it work.  There are no services which to integrate with.  There are no events published to subscribe to.  
