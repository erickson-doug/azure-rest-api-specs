# Authoring good descriptions in Swagger 2.0
> C+E CSI SDK Documentation Team


> **The descriptions you write for the code elements in Swagger become the baseline public Azure REST API documentation on http://docs.microsoft.com.**

These descriptions are also passed through by AutoREST to become triple-slash (///) comments in the corresponding client SDKs, which are likewise transformed into published baseline ref documentation.

This means that these docs are part of your product, and as ScottGu notes, a key part of your user experience. They're not just served up on docs.microsoft.com; they can also be discovered through Swagger UI (or other REST documentation client tools), command-line tools, and IntelliSense (for client SDKs). These descriptions represent your product and the hard work you put into making great APIs, and as Microsoft, folks expect a polished experience.
Therefore, take the time to craft your descriptions well! This doc provides some basic advice from the C+E CSI content team, as well as various tips to ensure that your public Azure ref documentation looks clean, consistent, and great!

## Getting started

1. If you don't feel you have strong English grammar or spelling skills, or if you're nervous about putting your documentation on display for the world to see, contact a content developer or manager from CSI. We have some basic in-person training to help you start off on the right foot. A content developer should also be part of your code review, to check your descriptions and ensure that what we deliver is consistent and professional and ready for publication.

2. Set yourself up with some good content support tools.
    - [Grammarly](http://www.grammarly.com) is a web site that provides an English language grammark checker. Just cut-and-paste your description strings into it and review the suggested fixes.
    - If you're using VSCode to edit your Swagger, consider one of these Swagger doc previewer extensions:
        - [swagger-doc-viewer](https://marketplace.visualstudio.com/items?itemName=mimarec.swagger-doc-viewer) renders your Swagger file to a more readable format. Note that this format is not the same style as what will be generated for docs.microsoft.com.
        - [Arjun Swagger Viewer](https://marketplace.visualstudio.com/items?itemName=Arjun.swagger-viewer) is another Swagger preview extension, but has less validation warnings.

3. Treat these descriptions like the rest of your code. Plan to have them throughly reviewed, either by a content developer or an engineering team member with English language writing experience. CodeFlow and the CodeFlow GitHub Chrome extension are a great way to do this.

## Basic rules for public docs (descriptions)

Below is a list of common expectations for published description strings that you must observe.

1. **Start every description with a capital letter and end it with a period** (".").
2. **Use correct English spelling and grammar**. Even the best technical writers screw up from time to time, and when you're authoring a hundred descriptions in a 5000-line JSON file, typos and bad grammar are bound to happen. Use Grammarly or another spelling and grammar checking tool on your descriptions after you complete each one; or, break out your code skills, dump the descriptions (with line numbers) to a text file and pipe it through a grammar tool/library/service. (Note: This would be a great enhancement to the Linter.)
3. **Do not use the API's code symbol capitalization style for acronyms**. For example, use "URL", "not Url"; and use "ID", not "Id".
4. **Start the description for every operation with a verb phrase.** Try to use the same verb that you provided in the documentid (for AutoREST method naming) or for the HTTP operation (GET/PUT/DELETE, at least.) That said, some verbs are uncomfortable ("obtains") or unfriendly ("destroys) or may not make sense to a newer reader ("patches"), so put yourself in the reader's shoes (or look at similar, previously documented APIs) and choose a good, readable verb to open with. We prefer the imperative form ("get...") over the third-person singular ("gets..."), but that's mostly a grammar nerd dispute. 
5. **Document the HTTP status codes your REST operations return**. Yeah, that's a pain, since you're probably thinking more out the client SDK APIs than the REST ones, but since we're publishing public docs for your REST APIs, it's pretty sloppy to have those fields empty -- and since someone **can** call these APIs through an HTTP interface directly, they will want to know what to do with those codes or what happened. If you have good logic for handling these codes in your SDK implementations, share that briefly in the response status code descriptions.
6. **Explicate parameter and response objects as best you can**. When someone reads a doc page for the first time, they're looking to see if the API is something they can use. They want to quickly assess the input and the output of the API, **not** parse through nested object definitions and large examples. (They'll do that after they've decided that this API is right for their coding needs.) You don't need to provide a ridiculous level of detail, but let them know what they need to provide in what MIME type format, or what they can expect to get back (and in what format). For example, a parameter description for a POST operation that takes an object describing a database configuration should **not** say "The database configuration"; rather, it should provide some salient details like "A JSON file that contains the database configuration, including the provider information and basic options."
7. The same for object definitions themselves. 

## Good practices

1. Spell out uncommon or overloaded acronyms on first usage. Example: "Gets a GitHub-Flavored Markdown (GFM) formatted document that contains the current release notes." Common or well-known acronyms, such as REST, API, URL, URI, and ID do not need to be spelled out.

2. Previewing your content is a good practice. It takes you out of the curly-brace world of JSON, and lets you view your writing with a reader's eye, not a coder's. Empathy is important for great docs.


## Notes and Caveats

1. Right now, description strings are very limited in their expressiveness. Our tooling does not support the rendering of GFM syntax, nor does it support any documentation-friendly vendor extensions at this time. (This will change.) Some HTML elements are whitelisted, and we will update this document with those in the future. Ultimately, this means that you must be both efficient and detailed in your prose, and this can be a challenge starting out!

2. Some level of redundancy is good! For example, if you have an operation "GET <path>/notes/latest", it's okay to have a description "Gets the latest notes." and to leave it at that. While any dev worth her salt can look at the operation and the path and come to the same conclusion, this adds a level of scanability to the page -- especially for newer developers, their eyes will go to the prose before attempting to parse the API syntax. Also, an empty operation description on a doc page makes it look we don't care and that the docs are autogenerated from sources without any respect for the human beings that might read them.

3. Need to provide more detail for a critical or complex API? Contact your content developer in CSI, and we can create an "overwrite" Markdown file that adds remarks, code samples, and formatted descriptions for your published API doc. We won't do this for every API, but we're also aware that there are some serious limitations with our early tools and approach -- and that some APIs are more equal than others.
