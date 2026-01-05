# Metasyntactic variable - Wikipedia

{% code title="example.py" %}
```python
# Define a function named spam
def spam():

    # Define the variable ham
    ham = "Hello World!"

    # Define the variable eggs
    eggs = 1

    return
```
{% endcode %}

#### IETF Requests for Comments

Both the [IETF](/broken/pages/64f97925b3d8b080a3fc35c5cf82d1112830fb24) [RFCs](/broken/pages/2ed4aa49f4fe925ccfd729ce89854ffada9b103d) and [computer programming languages](/broken/pages/592dbd2c6837b8708fa02218ee958b6f591a6666) are rendered in [plain text](/broken/pages/c9581f5bd2f00589442cd05ac080d8bfb324741a), making it necessary to distinguish metasyntactic variables by a naming convention, since it would not be obvious from context.

Here is an example from the official [IETF](/broken/pages/64f97925b3d8b080a3fc35c5cf82d1112830fb24) document explaining the [e-mail](/broken/pages/1eff3cc8498d124e128050f4541f9252da3f53bc) protocols (from RFC 772 - cited in RFC 3092):

```
 All is well; now the recipients can be specified.

     S: MRCP TO:<Foo@Y> <CRLF>
     R: 200 OK

     S: MRCP TO:<Raboof@Y> <CRLF>
     R: 553  No such user here

     S: MRCP TO:<bar@Y> <CRLF>
     R: 200 OK

     S: MRCP TO:<@Y,@X,fubar@Z> <CRLF>
     R: 200 OK

  Note that the failure of "Raboof" has no effect on the storage of
  mail for "Foo", "bar" or the mail to be forwarded to "fubar@Z"
  through host "X".
```

(The documentation for texinfo emphasizes the distinction between metavariables and mere variables used in a programming language being documented in some texinfo file as: "Use the @var command to indicate metasyntactic variables. A metasyntactic variable is something that stands for another piece of text. For example, you should use a metasyntactic variable in the documentation of a function to describe the arguments that are passed to that function. Do not use @var for the names of particular [variables](/broken/pages/911354cbf3fb288a56646385a9757f2eeb8940b2) in programming languages. These are specific names from a program, so @code is correct for them.")

Another point reflected in the above example is the convention that a metavariable is to be uniformly substituted with the same instance in all its appearances in a given schema. This is in contrast with [nonterminal](/broken/pages/e4d37a20144e9f2b8f4ea62dee8a1af859ae673c) symbols in [formal grammars](/broken/pages/79e8b183665f5d063d0208579fffd70cdef7edcb) where the nonterminals on the right of a production can be substituted by different instances.

### Example data

#### SQL

It is common to use the name [ACME](/broken/pages/a320574dcd119ce7a05835638e3ef9f3becc9861) in example [SQL](/broken/pages/0b1fff78eb8d441356b51f0652806d0a06e8f485) [databases](/broken/pages/27fc402d12c0db2f58949cbf330b19f7472ca52f) and as a placeholder company-name for the purpose of teaching. The term 'ACME Database' is commonly used to mean a training or example-only set of database data used solely for training or testing. ACME is also commonly used in documentation which shows SQL usage examples, a common practice with in many educational texts as well as technical documentation from companies such as [Microsoft](/broken/pages/3e123123c97583409c703e0be1d5d405c04ceb42) and [Oracle](/broken/pages/da45a00df11d35c96270748c5ced7af12f997a71).

### See also

* [Metavariable (logic)](/broken/pages/4db27d720913e67466502dedd70bd23880496a3d)
* [xyzzy](/broken/pages/a81e1bcd590090d5c53601b96ed2f88fec8998d9)
* [Alice and Bob](/broken/pages/88706cfa6f65b469bea76b74aa82caf2a165cb79)
* [John Doe](/broken/pages/146b004fbd853b1085e13ce6db20e85f420f36df)
* [Fnord](/broken/pages/db7955db9b816b8e79fa323b11cf2bfa07c850b9)
* [Free variables and bound variables](/broken/pages/9431d9436b47868c4edfdaa90ded4e9c7689357b)
* [Gadget](/broken/pages/2fd1ec394752eafffc097cb7ba48596a88a48458)
* [_Lorem ipsum_](/broken/pages/d4252573b13fea2242b8514e02b711a0d623aa33)
* [Nonce word](/broken/pages/3732d705f4b75d926b046dbb98bf13afd5c61a36)
* [Placeholder name](/broken/pages/a0091dab3bb227ee2719d950945b0fd12dfc39ec)
* [Widget](/broken/pages/9ad5c3de1cd1bd6781b76adf5692afe45e5c234c)
* [Smurf](/broken/pages/324e68757da66b5e8c3d3c94250520f9ee4fb380#Language)

<details>

<summary>References</summary>

1. Eastlake 3rd, Donald E.; Manros, Carl-Uno; Raymond, Eric S. "Etymology of "Foo"". https://www.rfc-editor.org/rfc/rfc3092. doi:10.17487/RFC3092. RFC 3092.
2. "Document Retrieval". https://www.rfc-editor.org/retrieve/.
3. Laughlin, Stuart (November 18, 2016). "Metasyntactic variable". programming@ProgClub (Mailing list). Archived: https://web.archive.org/web/20221202085628/https://www.progclub.org/pipermail/programming/2016-November/002305.html.
4. Crowther, Will (1977-03-11). "advdat.77-03-11". Colossal Cave Adventure Source Code. https://jerz.setonhill.edu/if/crowther/advdat.77-03-11.
5. "hogeの意味・使い方 - 英和辞典 Weblio 辞書". https://ejje.weblio.jp/content/hoge.
6. メタ構文変数 (in Japanese). https://ja.wikipedia.org/wiki/%E3%83%A1%E3%82%BF%E6%A7%8B%E6%96%87%E5%A4%89%E6%95%B0.
7. LeMan Dergisi 1376. Sayı (in Turkish). https://books.google.com/books?id=dRxdDwAAQBAJ\&dq=hede+h%C3%B6d%C3%B6\&pg=PA12.
8. "The Jargon File - metasyntactic variable". http://www.catb.org/jargon/html/M/metasyntactic-variable.html.
9. Mongan, John; Kindler, Noah; Giguere, Eric (2012). Programming Interviews Exposed: Secrets to Landing Your Next Job. John Wiley & Sons. p. 242. ISBN 978-1-118-28720-0.
10. "The Python Tutorial — Python 3.8.1 documentation". https://docs.python.org/3/tutorial/.
11. "General Python FAQ — Python 3.9.7 documentation". https://docs.python.org/3/faq/general.html.
12. "Marking Words and Phrases". Texinfo 4.0. The GNU Documentation Format. Archived: https://web.archive.org/web/20091106004856/http://sunsite.ualberta.ca/Documentation/Gnu/texinfo-4.0/html\_chapter/texinfo\_10.html.
13. R. D. Tennent (2002). Specifying Software: A Hands-On Introduction. Cambridge University Press. pp. 36–37 and 210. ISBN 978-0-521-00401-5.
14. Kriegel, Alex (2008). SQL bible. Wiley. ISBN 978-0-470-22906-4.
15. Ruel, Chris (2014). Oracle 12c for dummies (in Danish). John Wiley & Sons. ISBN 978-1-118-74531-1.
16. "Work with data in ASP.NET Core Apps". https://docs.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/work-with-data-in-asp-net-core-apps. 25 April 2023.

</details>

### External links

* Definition of _metasyntactic variable_, with examples.: http://www.catb.org/jargon/html/M/metasyntactic-variable.html
* Examples of metasyntactic variables used in _Commonwealth Hackish_: http://www.catb.org/jargon/html/C/Commonwealth-Hackish.html
* Variable "foo" and Other Programming Oddities: http://blog.codinghorror.com/variable-foo-and-other-programming-oddities/

Retrieved from "https://en.wikipedia.org/w/index.php?title=Metasyntactic\_variable\&oldid=1313108528"
