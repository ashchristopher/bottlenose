Bottlenose
==========

Description
-----------

Bottlenose is a thin Python wrapper over the Amazon Product Advertising API. There is practically no overhead. Before you get started, make sure you have both Amazon Product Advertising and AWS accounts (yes, they are separate--confusing, I know).

Features
--------

* Compatible with Python versions 2.4 and up
* Support for CA, CN, DE, ES, FR, IT, JP, UK, and US Amazon endpoints
* No requirements, except simplejson for Python pre-2.6

Usage
-----

Creation::

     >>> import bottlenose
     >>> amazon = bottlenose.Amazon(AMAZON_ACCESS_KEY_ID, AMAZON_SECRET_KEY, AMAZON_ASSOC_TAG)
     >>> response = amazon.ItemLookup(ItemId="0596520999", ResponseGroup="Images",
         SearchIndex="Books", IdType="ISBN",
         Style="http://xml2json-xslt.googlecode.com/svn/trunk/xml2json.xslt")
     {"ItemLookupResponse":{"OperationRequest":{"HTTPHeaders":{"Header":null},"Re...

Notice that I do not like XML. Despite this, you are free to omit the `Style`
parameter when making your calls to Amazon. I like using an amazing XSLT
stylesheet written by Doeke Zanstra that does its best to convert XML to JSON.
As far as I can tell, it does a pretty amazing job with Amazon's responses.
I've included the stylesheet in this project if you'd like to host it yourself.

Want to grab some other data? No problem! Bottlenose to the rescue::

     >>> response = amazon.ItemSearch(Keywords="Kindle 3G")
     <?xml version="1.0" encoding="UTF-8"?><HelpResponse xmlns="http://webserv...

Any valid API call from the following is supported (in addition to any others
that may be added in the future). Just plug in appropriate request parameters
for the operation you'd like to call, and you're good to go::

     BrowseNodeLookup
     CartAdd
     CartClear
     CartCreate
     CartGet
     CartModify
     ItemLookup
     ItemSearch
     SellerListingLookup
     SellerListingSearch
     SellerLookup
     SimilarityLookup

For more information about these calls, please consult the [Product Advertising
API Developer Guide](http://docs.amazonwebservices.com/AWSECommerceService/latest/DG/index.html).

License
-------

Copyright &copy; 2011 Dan Loewenherz

See LICENSE for details.

