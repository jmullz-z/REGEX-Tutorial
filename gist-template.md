## Computer Science for JavaScript Challenge: Regex Tutorial
Regular expressions can be used to find certain patterns of characters within a string. You can also find and replace a character or sequence of characters within a string. They are also frequently used to validate input. This regex matches character information for valid e-mail addresses.

## Summary
The regex code that I will be anaylizing today is: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components
A regex is considered a literal, so the pattern must be wrapped in slash characters (/). If we examine the “Matching a Username” regex, you'll see that this is true:

/^[a-z0-9_-]{3,16}$/
Note: JavaScript provides two ways to create a regex object. The first, shown in our example, uses literal notation. The second is to use a RegExp constructor. The constructor function's parameters are not enclosed within slashes; instead, they use quotation marks.

### Anchors
The anchors used to contain this regular expression are: ^ to start, and $ to finish.

### Quantifiers
In this example, we used + to communicate there is another sequence to be matched as a greedy quantifier. We also used {2,6} as another greedy quantifer to specify the input should be a minimum of 2 characrtors to a maximum of 6 characters.

### OR Operator
/^#?([a-f0-9]{6}|[a-f0-9]{3})$/
The "or" operator within a regular expression is defined using the | element. The or operator indicates that it could either of the components that we are separating with the |. For our hex value regular expression we have ([a-f0-9]{6}``|``[a-f0-9]{3}). Note the or operator separating these 2 components. This means that our hex value could either be 6 characters [a-f0-9]{6} or 3 characters [a-f0-9]{3}.

### Character Classes
In this regular expression, the charactor class /d is used which in Javasctipt classifies the use of any digit from 0 to 9.

### Flags
As a literal, a regex must be wrapped in slash characters. The one exception to this rule is with the component known as flags. Flags are placed at the end of a regex, after the second slash, and they define additional functionality or limits for the regex. There are six optional flags that can be used, either separately or together and in any order, but these are the three you're most likely to encounter:

g—Global search: the regex should be tested against all possible matches in a string.

i—Case-insensitive search: case should be ignored while attempting a match in a string

m—Multi-line search: a multi-line input string should be treated as multiple lines

### Grouping and Capturing
There are three groups being captured in this example. Group #1 is the username of the e-mail account [a-z0-9_\.-]. The second group captures the domain name or e-mail service being used [\da-z\.-]. Lastly, the third group captures the domain extention (i.e .com or .net) [a-z\.]{2,6}


### Bracket Expressions
Much like the groups in this example, there are also 3 bracket expressions. The information in the bracket expressions is opened and closed between brackets like this []. This indentifies which information is allowed to be matched.

Bracket Expression #1: [a-z0-9_\.-] - includes case sensitive characters from a-z, numbers from 0-9 an underscore, periods and hyphens.

Bracket Expression #2: [\da-z\.-] - includes all digits, case sensitive characters from a-z, periods and hyphens

Bracket Expression #3: [a-z\.] - includes case sensitive characters from a-z and periods.


### Greedy and Lazy Match
In this example we have only used greedy quantifiers + and {}, meaning that it will allow the match to expand as long as it neess to go. If these quantifiers were lazy quantifiers, they would appear as +? or {}?, this will direct the system to make the shortest match.

### Boundaries
The metacharacter \b is an anchor like the caret and the dollar sign. It matches at a position that is called a “word boundary”. This match is zero-length.

There are three different positions that qualify as word boundaries:

-Before the first character in the string, if the first character is a word character.
-After the last character in the string, if the last character is a word character.
-Between two characters in the string, where one is a word character and the other is not a word character.

### Back-references
Back referencing is a way to refer to previously matched patterns inside a regular expression. For example:

-Set up an array of matches:
$matches = array();

-Create a String:
$str = ""This is a 'string'"";

-Traverse it with regular expressions:
preg_match( "/("|').*?("|')/", $str, $matches );

-Print the whole match:
echo  $matches[0];

-This will not correctly match the string. Instead, it will print: 'This is a';

-This regular expression matches the opening double quote but finds a different type of quote to close it. This is because it was given the option of picking a double or single quote at the end. In order to fix this, you can use back referencing. The expressions 1, 2, …., 9 hold references to previously captured subpatterns. The first matched quote, in this case, will be held by the variable 1.

How to use it:
-preg_match( '/("|').*?1/', $str, $matches );
-This will return: "This is a 'string'";
-Back referencing may also be used by preg_replace. Note that instead of 1 … 9, you should use $1 … $9 … $n (any number of these will work).
$text = preg_replace( '/<p>(.*?)</p>/', 
"&lt;p&gt;$1&lt;/p&gt;", $html );
-The $1 back reference holds the text inside the paragraph and is being used in the replace pattern itself. This completely valid expression shows an easy way to access matched patterns even while replacing.

### Look-ahead and Look-behind
Collectively, lookbehinds and lookaheads are known as lookarounds. A lookahead or a lookbehind does not "consume" any characters on the string. (i.e. After the lookahead or lookbehind 's closing "()", the regex engine is left standing on the very same spot in the string fromw which it started looking: it hasn't moved. Then the engine can start matching characters again, or, look ahead (or behind) for something else.
- Lookahead After the Match: \d+(?= dollars);
- Lookahead Before the Match: (?=\d+ dollars)\d+,
This pattern achieves the same result as \d+(?= dollars) from above, but it is less efficient because \d+ is matched twice.;
- Negative Lookahead After the Match: \d+(?!\d| dollars);
- Negative Lookahead Before the Match: (?!\d+ dollars)\d+;

*Javascript doesn't support lookbehind, though it supports lookahead.

## Author

My name is Jessica Mulliken and I am currently in a full-stack web programing bootcamp and am becoming a professional web developer. I have worked on many projects now. Here is the link to my portfolio that shows some of the work that I have done: https://github.com/jmullz-z/portfolio-assignment.git
