#Critical Editions and the Data Model as Interface

I'm going to talk today about ongoing work to develop standards and tools for publishing digital critical editions for the Digital Latin Library. The DLL is a joint project of the Society for Classical Studies, the Medieval Academy of America, and the Renaissance Society of America, with funding from the Andrew W. Mellon Foundation. The project is hosted at the University of Oklahoma and Sam Huskey, the chair of the OU Classics department, is the principal investigator.

When I went and looked at the definition of interface, I kind of expected to find a Latin derivation, probably from *interfio* (to put between), the passive form of *interficio*, which means, among other things, to murder someone. But I was surprised to find it's actually a very recent coinage, a hybrid word, the Latin *inter* plus French/English *face* as in *surface*. In the context of this conference, we pretty obviously mean it in the sense of "user interface", a mediation between a digital system and the human beings who use it.

What do interfaces do?
 * They hide implementation details and complexity
  * All kinds of different things may happen in the background when you type something in a search box, but all you need to know is "I type something here, hit Enter or the button next to it, and I get results."
 * They serve as a contract governing the interaction between two parties
  * A good interface tells you what it will or won't do for you. An API, for example, is just a list of functions you can call, with hopefully an idea of what will happen if you call them.
 * They serve as generalizable protocols. Different systems can implement the same interface, and you'll know how to operate the system even if you've never seen it before, because you understand its contract.
  * Once you understand how restaurant menus work, you can order at pretty much any restaurant
 * Because interfaces do all these things, they act to steer you in a particular direction as you interact with them. Interfaces have a rhetoric.

So basically, interfaces simplify things. They present you with a surface beneath which you can't see, and that surface has on it whatever switches and knobs you're allowed to use to do things with the larger object. They clarify (saying "this is what you can do here"), but they can also obscure (saying "don't look behind the curtain"). Interfaces are everywhere once you start to look for them. Languages are interfaces. Computer languages obviously so, but even human languages. To interface with someone, after all, is to talk to them.

When it comes to editions as interfaces then, the idea must be that here I, as an editor, give you a text, and along with that text, I'm giving you some (filtered) insight into that text's history and why I decided to construct the text the way I did. But I'm not giving you everything, just what I've decided is important for your understanding of the text. I'm hiding complexity; I'm promising you some view into that complexity via the apparatus, description of the sources, and stemma; I'm doing this in a standard way.

So a printed edition has a surface that we see, and that surface reveals information about the constitution of the text that the editor considered important. This surface hides a lot of the work that went into the edition's construction—the collation that the editor used, for example. It defines what it's going to give you, by listing its sources and the symbols in the apparatus used to identify them, and a rationale for deciding on which variants were promoted to the text. And, by using what has become a pretty standard form, it guarantees that anyone who knows how to use a critical edition will be able to read it.

Now, I'm going to have to digress a little here, because the kinds of edition I'm talking about may be different from what you think of as an edition. I'm a Classicist by training, and our texts are a dire mess. The originals are almost always gone, really gone. Past the event horizon. All we have are old (but way younger than the original) copies and editions. And we usually don't even know if there was a thing like a singular "original". In fact, we can often be confident that there wasn't. So when we talk about critical editions, what we usually mean, at least in the Anglo-American tradition, is a painstaking attempt to construct a text that asymptotically approaches an idea of what the author might have written. Not a task for the faint of heart. But also I think not precisely what all of you imagine when you think of a critical edition. And that's ok, but I think it's important to be aware that our interfaces, human language in this case, can be a bit treacherous. They may hide too much. "Critical Edition" has different meanings to different people in this room.

So back to the messy implementation details: What of the traditional critical edition should we carry over into a digital critical edition? What can we do better? For the Digital Latin Library Project, we talked for a long time about this during our planning period. There were a lot of opinions out there. Some people think you should do away with the idea of an editor-mediated edition, and just provide access to all the sources, along with tools for comparing them, allowing users to see what the textual tradition is really like. This is again at root the argument that interfaces are treacherous.

We decided in the end, though, that there's still a place for "traditional" critical editions, where an editor has considered the textual tradition and produced an argument for a particular text. Not that there's anything wrong with giving people access to the sources, but we felt, and still feel, that turning the full firehose on to people who just want a text to work with was unkind. And that feeling applies not just to students, but to advanced scholars too. After all, how can you do any higher criticism if there's no agreement on the text you're dealing with? You've got to have some ground to stand on if you're going to make an argument about style, for example. Of course, one might argue that the textual tradition is such a mess that there is no safe ground to stand on. But I'm not sure I buy that argument. I think editors have a function, and that function, in a nutshell, is to comprehend the messy history of a text, and distill it down to an interface, an edition, that you can use without having to confront the mess at every point. You should be able to confront that mess in all its glory if you want to, but you shouldn't have it forced on you.

In the end, we decided our take on the digital editions should look a lot like the print versions people are used to, but a) be more accessible, and b) give readers more control over the text they're reading. The great thing about digital objects, after all, is that they're mutable. Innovation is great, but it brings with it risks and burdens. We're already doing something really hard. Why make it harder? We decided to do a soup-to-nuts prototype using Cesar Giarratano's 1910 edition of Calpurnius Siculus.

Along the way, our decisions about interfaces have affected not just what our users will be able to do with our texts, but what we've done with them. And this is where I'll transition into demo mode. Just so you're aware of the rhetoric of our current interface, I'll outline some of those decisions:

 * We chose to keep the basic form of the critical edition.
  * This led us to focus more on the text than on the system. We didn't have to invent an architecture for marshalling arbitrary collections of related texts. Crucially, we wouldn't be telling editors to stop doing what they do and instead focus on finding and transcribing every version of the text.
 * We chose to mark our texts up in TEI.
  * This meant we were working within an existing framework. An imperfect one, to be sure, but one which we could adapt to and even change if necessary. We had a language we could use to model our texts.
 * We chose not to use XSLT transform our texts into standard HTML for display
  * This is where we did decide to innovate, albeit based on prototypes that had been demonstrated to work. Again, languages are interfaces. We decided we would convert our texts to HTML5 Custom Elements instead of going the normal route and using XSLT to turn them into ordinary HTML. Normal HTML is semantically impoverished, so you have to throw information away in a TEI-to-HTML conversion. And, again, languages are interfaces, and the affordances of XSLT mean that the default treatment of an element without a template is to keep the text, but throw away the markup. So if you do nothing, you lose information. If you do things our way, though, if you do nothing, you get a copy of the markup almost exactly as it was.
 * We chose to define sigla for the apparatus, but provide immediate expansions of them via mouseovers
  * If you haven't thrown any information away, and you gave the definition of a siglum an id, and referenced that id in the apparatus, then it's almost no work to grab the definition whenever you need it.
 * We chose to let our users manipulate the reading text using the apparatus criticus
  * If you haven't lost any of your data model, then you can effect changes to the reading text by manipulating the model itself.