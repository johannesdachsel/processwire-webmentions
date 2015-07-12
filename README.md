# Webmentions for Processwire

Module for [Processwire](#)(https://processwire.com) that provides basic [Webmentions](http://indiewebcamp.com/Webmention) support. Currently only for receiving webmentions.

## Usage

The module is currently tailored to my needs. I’ll try and make it more flexible shortly but basically this is how it works right now (more features to come):

1. Set up a Repeater field and name it `responses`
2. Add create the following fields and add them to the repeater:
	* `rsp_author_name` (Text)
	* `rsp_author_photo` (URL)
	* `rsp_author_url` (URL)
	* `rsp_pubdate` (Datetime)
	* `rsp_type` (Select or Text)
	* `rsp_source_url` (URL)
	* `rsp_content` (Textarea)
5. Add the repeater field to any templates you wish to receive webmentions on
4. Install the module
5. Create a template containing the following code:  
	`$webmentions = $modules->get('Webmentions');`  
	`$webmentions->endpoint();`
6. Create a page and assign the template to it
7. Add the URL of that page to your `<head>` element like so: `<link rel="webmention" href="http://your-domain.com/your-webmention-endpoint/" />`

When a page receives a webmention, the module will parse the source URL and populate the fields with any information it can find. It then adds the response to the repeater and saves the page.

So far I’ve been receiving webmentions for my tweets from [brid.gy](https://www.brid.gy) which works as expected.
