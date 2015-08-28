# Comparison of JavaScript WYSIWYG editors

*Comparison as of August 28, 2015.*

While building [iDoRecall](http://idorecall.com), we looked for WYSIWYG editor to enable our users to create and paste rich text recalls. While Markdown is great, it can't carry on much of the formatting that our audience is likely to encounter in the wild, so we looked for a WYSIWYG editor with the following features:

* correct pasting of minimally rich text from a variety of online sources (Google Docs, StackOverflow)
* paste images from clipboard directly, the way Slack, Imgur, GitHub, Google Docs and StackOverflow work
* usable on modern browsers and mobile devices; IE < 9 support not important
* relatively lightweight
* preferrably open source licensed, preferrably MIT

## Candidates

We have evaluated every single editor listed [here](https://github.com/cheeaun/mooeditable/wiki/Javascript-WYSIWYG-editors) and [here](http://designhuntr.com/jquery-text-editor-plugins/). Surprisingly, out of ~45 editors tested, only one (!) satisfies these requirements.

For an alternative comparison table (no longer maintained by us), check out [SocialCompare](http://socialcompare.com/en/comparison/javascript-online-rich-text-editors).

### Can paste images and rich text

1. [Summernote](http://summernote.org) (jQuery+Bootstrap) - about 400/400 open/closed [GitHub issues](https://github.com/summernote/summernote/issues). ~84kB minified.
2. [AlloyEditor](http://alloyeditor.com/demo/) - based on CKEditor, with a modern UI built with React. [800Kb minified, 180kB gzipped](https://github.com/liferay/alloy-editor/issues/229) is smaller than CKEditor out of the box. [No mobile support](https://github.com/liferay/alloy-editor/issues/226).
3. [Hackpad](https://github.com/dropbox/hackpad) - real-time collaborative editor, quite popular with the open source community

## Can't paste images or rich text

Images can be "pasted" in two ways:

* From other web pages. In that case, a link to the remote image will actually be pasted.
* From the system clipboard. This is equivalent to a drag&drop event, and the image needs to be effectively uploaded or converted to base64. This is [not that easy to implement](https://github.com/JohnMcLear/ep_copy_paste_images).
 
Rich formatting is often tricky to paste. Two samples were used:

* StackOverflow code
* A [code block](http://addyosmani.com/resources/essentialjsdesignpatterns/book/#constructorpatternjavascript) from @addyosmani's *JavaScript Patterns* online book 

Results:

1. [Froala WYSIWYG](https://froala.com/wysiwyg-editor) (jQuery) - can paste images from the clipboard, but [loses most of the rich formatting when pasting](https://github.com/froala/wysiwyg-editor/issues/552) before version 2
- [Trumbowyg](http://alex-d.github.io/Trumbowyg/) (jQuery + 15KB minified) - can paste rich text with images from other web pages, but [not images alone](https://github.com/Alex-D/Trumbowyg/issues/135)
- [woofmark](http://bevacqua.github.io/woofmark/) - Promising Markdown/WYSIWYG/HTML editor. [Can't paste images from the system clipboard](https://github.com/bevacqua/woofmark/issues/17).
- [Squire](http://neilj.github.io/Squire/) - used at Fastmail. [Rich text formatting loss](https://github.com/neilj/Squire/issues/95), [demo can't paste images from the system clipboard](https://github.com/neilj/Squire/issues/93) (only if they're copied from other web pages).
- the [Guardian's Scribe](http://guardian.github.io/scribe/) - 3,000+ GitHub stars. Built because [TinyMCE, CKEditor, Medium.js, Redactor, ZenPen, wysihtml5](https://www.theguardian.com/info/developer-blog/2014/mar/20/inside-the-guardians-cms-meet-scribe-an-extensible-rich-text-editor) (that is the entire list of solutions they've investigated) either didn't produce clean markup, or weren't extensible. [Can't paste images](https://github.com/guardian/scribe/issues/424).

    > Scribe exposes a simple, browser-agnostic, low-level framework to manage and extend interactions with contentEditable.
- [Etherpad](http://etherpad.org) - famous collaborative editor. Can't paste images of any kind in the demo.
- [Etherpad Lite](https://github.com/ether/etherpad-lite) - a [rewrite of Etherpad](https://github.com/ether/etherpad-lite/wiki/FAQ) with ~5000 stars on GitHub. Can paste images from other web pages (i.e. via the URL), but [not from the system clipboard](https://github.com/ether/etherpad-lite/issues/2227#issuecomment-135898136) into [the demo](https://beta.etherpad.org/). There is a [plugin for pasting and uploading images](https://github.com/JohnMcLear/ep_copy_paste_images) but it's unstable.
- [Raptor](http://www.raptor-editor.com/) - [can't paste images](https://github.com/PANmedia/raptor-editor/issues/56)
- [Dante](https://github.com/michelson/Dante) (jQuery, Underscore) - [image pasting is supposed to work, but doesn't](https://github.com/michelson/Dante/issues/33)
- [Wysihtml](http://wysihtml.com/) (vanilla) - actively-maintained fork of the Xing project; [loses rich text formatting when pasting](https://github.com/Voog/wysihtml/issues/180), [can't paste images from the clipboard](https://github.com/Voog/wysihtml/issues/163)
- [MediumEditor](https://yabwe.github.io/medium-editor/) (vanilla) - [GitHub](https://github.com/yabwe/medium-editor) - [can't paste images](https://github.com/yabwe/medium-editor/issues/657) and loses formatting when pasting rich text
- [Quill](http://quilljs.com/) - collaborative editor; [can't paste images](https://github.com/quilljs/quill/issues/137)
- [Minislate](https://github.com/olivier-m/minislate/) (vanilla) - [can't paste images](https://github.com/olivier-m/minislate/issues/7)
- [Medium.js](https://github.com/jakiestfu/Medium.js/) (vanilla), [can't paste images from the clipboard](https://github.com/jakiestfu/Medium.js/issues/102#issuecomment-107349252)
- [ZenPen](http://zenpen.io) - [can't paste images from clipboard](https://github.com/tholman/zenpen/issues/119)
- [Pen](https://github.com/sofish/pen) (vanilla) - [can't paste images from the clipboard](https://github.com/sofish/pen/issues/151)
- [Hallo.js](http://hallojs.org/) - minimalistic jQueryUI plugin with floating toolbar; [can't paste images](https://github.com/bergie/hallo/issues/234)
- [SCEditor](http://www.sceditor.com/) - [can't paste images](https://github.com/samclarke/SCEditor/issues/386)
- [bootstrap3-wysiwyg](http://bootstrap-wysiwyg.github.io/bootstrap3-wysiwyg/) - [can't paste images from the clipboard](https://github.com/bootstrap-wysiwyg/bootstrap3-wysiwyg/issues/143)
- [Suyati line control](https://github.com/suyati/line-control/), [can't paste images from the clipboard](https://github.com/suyati/line-control/issues/26)
- [KindEditor](https://github.com/kindsoft/kindeditor/issues/184) - Korean project, can't paste images
- [wysiwyg.js](http://wysiwygjs.github.io/) (vanilla or jQuery, <12KB) - [can't paste images](https://github.com/wysiwygjs/wysiwyg.js/issues/33)
- [dijit.Editor](http://dojotoolkit.org/reference-guide/1.10/dijit/Editor.html) - part of the Dojo toolkit; nothing about images mentioned on the page
- [Content Kit Editor](https://github.com/bustlelabs/content-kit-editor) - comes up with a new platform-agnostic serialization format, [mobiledoc](https://github.com/bustlelabs/content-kit-editor/blob/master/MOBILEDOC.md). [Can't paste images](https://github.com/bustlelabs/content-kit-editor/issues/101).
- [Redactor](http://imperavi.com/redactor/) (jQuery) - commercial license starts at $99; not on GitHub; can't paste images


## Heavyweight editors

1. [TinyMCE](http://tinymce.com/) - 380kB minified. Can [paste rich text, but not images directly](http://www.tinymce.com/develop/bugtracker_view.php?id=7537).
- [CKEditor](http://ckeditor.com/) (next generation of FCKeditor)
- [Aloha Editor](http://aloha-editor.com/) - [can't paste images](https://github.com/alohaeditor/Aloha-Editor/issues/1408). GPLv2 or commercial starting at 200 EUR
- [Mercury Editor](http://jejacks0n.github.com/mercury/) (jQuery, CoffeeScript, Rails) - [no updates since August 2014](https://github.com/jejacks0n/mercury/issues/478), [can't paste images](https://github.com/jejacks0n/mercury/issues/480)
- [WebODF](http://webodf.org/) - Powerful WYSIWYG editor that can import ODF files. Can insert images via file upload, but [can't paste images](https://github.com/kogmbh/WebODF/issues/916). AGPL license (free to use in open source projects), with commercial offering from KO GMBH.


## Couldn't evaluate, or don't quite do WYSIWYG

1. [bootstrap-wysiwyg](https://github.com/mindmup/bootstrap-wysiwyg/) (jQuery) - 4K GitHub stars, built for MindMup, [no demo](https://github.com/steveathon/bootstrap-wysiwyg/issues/39)
- [WysiBB](https://github.com/wbb/WysiBB) - returns BBCode. Mobile-friendly.
- [goog.editor](https://github.com/google/closure-library/tree/master/closure/goog/demos/editor) in the Google Closure Library
- [WYMeditor ](http://wymeditor.github.io/wymeditor/) (jQuery) - [GitHub](https://github.com/wymeditor/wymeditor); markup, not WYSIWYG editor


## No longer or dubiously maintained

1. [demarcate](https://github.com/will-hart/demarcate.js/issues/41) - convert Markdown to HTML. No update since Sep 2014. Can't paste images.
- [jWYSIWYG](https://github.com/akzhan/jwysiwyg/) (jQuery) - [no issue tracking](https://github.com/akzhan/jwysiwyg/pull/23), [upstream seems dead](https://github.com/jwysiwyg/jwysiwyg/issues/317)
- [grande.js](https://github.com/mduvall/grande.js) (vanilla) - [no update since July 2014](https://github.com/mduvall/grande.js/issues/79)
- [jHtmlArea](http://jhtmlarea.codeplex.com/) (jQuery) - no updates since Apr 2014, can't paste images
- [rataeditor](http://github.com/jfuentesa/rataeditor) (jQuery) - [abandoned since Feb 2014](https://github.com/jfuentesa/rataeditor/issues/2)
- ~~YUI Rich Text Editor - Editor (YUI) http://developer.yahoo.com/yui/editor/~~ [DEPRECATED]
- [WYSIWYG](http://maccman.github.com/wysiwyg/) (jQuery) - [abandoned](https://github.com/maccman/wysiwyg/issues/3)
- [jQueryTE](http://jqueryte.com/) - 19KB. [GitHub](http://jqueryte.com/) is apparently abandoned.
- [Yellow text](https://github.com/stefanvermaas/yellow-text/issues/36)
- [TinyEditor](https://github.com/jessegreathouse/TinyEditor/) (jQuery) - dead since Oct 2013
- [elRTE](https://github.com/Studio-42/elRTE/issues/15)
- [jQuery Notebook](https://github.com/raphaelcruzeiro/jquery-notebook/issues/125)
- [CLEditor](https://groups.google.com/forum/#!topic/cleditor/npHzAY9RbD4); can't paste standalone images or from Word
- [freshereditor](https://github.com/mquan/freshereditor/issues/12)
- [NicEdit](https://github.com/danishkhan/NicEdit/issues/13) - [can't paste images](https://github.com/danishkhan/NicEdit/issues/14)
- [mooeditable](http://cheeaun.github.io/mooeditable/) - "on hiatus" since 2013
- [OpenWebWare](http://www.openwebware.com) - no updates since 2007


## Commercial-only projects

* [Textbox.io](http://textbox.io/pricing/)
