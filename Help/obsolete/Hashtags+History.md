<script src="./html-generator/md-page.js"></script><noscript>

# Hashtags & History

There are two types of hashtags in ICL. Hashtags with text labels refer to macro definitions. Hashtags with numerics reference a command previously executed in the command history of AV-Bible.

##### Macro Hashtags *(text)*

As mentioned in the general overview, an optional directive can be issued that follows the selection criteria.  The Macro Directive can be used to tag a statement for subsequent execution. It has the following form:

| Directive Type               | Directive Syntax *(follows the Selection Criteria)* |
| ---------------------------- | --------------------------------------------------- |
| Macro (*apply* tag to macro) | ***\|\| tag***                                      |

We call a statement that has a tag applied, a "macro". Here is an example:

Macro tags must begin with a letter and cannot contain punctuation: only letters, numbers, hyphens, and underscores are permitted.


Let’s say we want to name our selection criteria for easier subsequent invocation; We’ll call it *eternal-power*. To accomplish this, we can apply a tag, as shown in the following example statement:

[ span: 7 similarity: 85% ] eternal power < Romans || eternal-power-romans

It’s that simple, now instead of typing the entire statement, we can utilize the macro with a simple hashtag. Here is how the macro is utilized:

#eternal-power-romans

##### History Hashtags *(numerics)*

The *use* command works for command-history works exactly the same way as it does for macros.  After issuing a *@review* command, the user might receive a response as follows.

*@review* -history

1>  @set %span = 7

2>  @set %similarity=85

3> "Jesus answered ... and"

And the *use* command can utilize any command listed.

#3

would be shorthand to for the search specified as:

"Jesus answered ... and"

### Viewing & Managing Macros

| Action      | Syntax                                                       |
| ----------- | ------------------------------------------------------------ |
| **@delete** | *tag* <u>or</u> *wildcard* <u>or</u> -tags FROM <u>and/or</u> UNTIL<br/>**FROM parameter :** *from* yyyy/mm/dd<br/>**UNTIL parameter :** *until* yyyy/mm/dd |
| **@view**   | *tag* <u>or</u> *wildcard* <u>or</u> -tags <u>optional</u> FROM <u>and/or</u> UNTIL<br/>**FROM parameter :** *from* yyyy/mm/dd<br/>**UNTIL parameter :** *until* yyyy/mm/dd |
| **@absorb** | **permitted:** *tag*                                         |

##### Additional explicit macro commands:

Two additional explicit commands exist whereby a macro can be manipulated. We saw above how they can be defined and referenced. There are two additional ways commands that operate on macros: expansion and deletion.  In the last macro definition above where we created  #another-macro, the user could view an expansion by issuing this command:

\@view another-macro

If the user wanted to remove this definition, the \@delete action is used.  Here is an example:

\@delete another-macro

If you want the same settings to be persisted to your current session that were in place during macro definition, the \@absorb command will persist all settings for the macro into your current session

\@absorb my-favorite-settings-macro 

**NOTE:**

​       \@absorb also works with command history.

### Viewing & Managing History

| Verb        | Syntax Category | Parameters                                                   |
| ----------- | --------------- | ------------------------------------------------------------ |
| **@invoke** | Configuration   | ***id***                                                     |
| **@delete** | Configuration   | -history FROM <u>and/or</u> UNTIL<br/>**FROM parameter :** *from* *id* <u>or</u> *from* yyyy/mm/dd<br/>**UNTIL parameter :** *until* *id* <u>or</u> *until* yyyy/mm/dd |
| **@view**   | Configuration   | *id* <u>or</u> -history <u>optional</u> FROM <u>and/or</u> UNTIL<br/>**FROM parameter :** *from* *id* <u>or</u> *from* yyyy/mm/dd<br/>**UNTIL parameter :** *until* *id* <u>or</u> *until* yyyy/mm/dd |
| **@absorb** | Configuration   | ***id***                                                     |

**COMMAND HISTORY** 

*@view* allows you to see your previous activity.  To show the last ten searches, type:

*@view* -history

To reveal all history up until now, type:

\@view until now

To reveal all searches since January 1, 2024, type:

*@view* from 2024/1/1

To reveal for the single month of January 2024:

*@view* from 2024/1/1 until 2024/1/31

To reveal all history since id:5 [inclusive]:

*@view* from 5

All ranges are inclusive. 

**RESETTING COMMAND HISTORY**

The \@delete command can be used to remove <u>all</u> command history.

To remove all command history:

\@delete -history -all

FROM / UNTIL parameters can limit the scope of the \@delete command.

#### Hashtag Utilization

The *use* command behaves identically, whether for macro utilization or history utilization.

In the selection block of a search expression, every aspect of the hashtag is utilized (Search, scope, and settings). This is called full hashtag utilization. There is one caveat however:

- If a settings block accompanies the search expression block, the settings block overrides that portion of the hashtag
- If a scoping block accompanies the search expression block, the scoping block overrides that portion of the hashtag

The other two block types also support hashtags. Those hashtags are always partial utilization. A settings block will only utilize the settings portion of the hashtag. A scoping block will only utilize the scoping portion of the hashtag.

A maximum of three hashtags can occur in the selection criteria. Each block can have zero or one hashtags. Here is an example with three hashtag utilizations in a single statement:

[ #3 ] #eternal-power-romans < #4