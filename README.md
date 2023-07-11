# <img src="assets/backend.png" alt="drawing" width="40" height="40"/> Backend Guidelines
###### *This guidelines will help the Back-end Software Engineering Division to craft their code and will be use on the company's KPI and technical compliance.*

## Contents
* #### **PHP**
    * [Principles](#principle)
    * [PSR-12: Extended Coding Style](#psr-12-extended-coding-style)
    * [Do's and Dont's](#dos-and-donts)
*  **Testing**
*  **Git**
*  **Microservice**
*  **Laravel**
*  **Typescript <span style="color:red">(Coming Soon!)</span>.**
*  **Onboarding**

# Principle

# PSR-12: Extended Coding Style

The key words **"MUST"**, **"MUST NOT"**, **"REQUIRED"**, **"SHALL"**, **"SHALL NOT"**, **"SHOULD"**, **"SHOULD NOT"**, **"RECOMMENDED"**, **"MAY"**, and **"OPTIONAL"** in this document are to be interpreted as described in [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).


#### <span style="color:green">Basic Coding Standard</span>

* Code **MUST** follow all rules outlined in PSR-1.

* The term '**StudlyCaps**' in PSR-1 **MUST** be interpreted as **PascalCase** where the first letter of each word is capitalized including the very first letter.

#### <span style="color:green">Files</span>

* All PHP files **MUST** use the Unix LF (linefeed) line ending only.
* All PHP files **MUST** end with a non-blank line, terminated with a single LF.
* The closing **?>** tag **MUST** be omitted from files containing only PHP.

#### <span style="color:green">Lines</span>

* There **MUST NOT** be a hard limit on line length.

* The soft limit on line length **MUST** be [120 characters](# 'ADD this in your VSCode settings.json "editor.rulers": [80,120]').

* Lines **SHOULD NOT** be longer than [80 characters](# 'ADD this in your VSCode settings.json "editor.rulers": [80,120]'); lines longer than that **SHOULD** be split into multiple subsequent lines of no more than [80 characters](# 'ADD this in your VSCode settings.json "editor.rulers": [80,120]') each.

* There **MUST NOT** be trailing whitespace at the [end of lines](# 'ADD this in your VSCode settings.json "files.trimTrailingWhitespace": true').

* Blank lines **MAY** be added to improve readability and to indicate related blocks of code except where explicitly forbidden.

* There **MUST NOT** be more than one statement per line.

#### <span style="color:green">Indenting</span>

* Code **MUST** use an indent of 4 spaces for each indent level, and **MUST NOT** use tabs for indenting.

#### <span style="color:green">Keywords and Types</span>

* All PHP reserved keywords and types **MUST** be in lower case.

* Any new types and keywords added to future PHP versions **MUST** be in lower case.

* Short form of type keywords **MUST** be used i.e. bool instead of boolean, int instead of integer etc.

#### <span style="color:green">Declare Statements, Namespace and Import Statements</span>

The header of a PHP file may consist of a number of different blocks. If present, each of the blocks below **MUST** be separated by a single blank line, and **MUST NOT** contain a blank line. Each block **MUST** be in the order listed below, although blocks that are not relevant may be omitted.

* Opening ```<?php``` tag.
* File-level docblock.
* One or more declare statements.
* The namespace declaration of the file.
* One or more class-based use import statements.
* One or more function-based use import statements.
* One or more constant-based use import statements.
* The remainder of the code in the file.


When the opening ```<?php``` tag is on the first line of the file, it **MUST** be on its own line with no other statements unless it is a file containing markup outside of PHP opening and closing tags.

Import statements **MUST** never begin with a leading backslash as they must always be fully qualified.


#### <span style="color:green">Classes, Properties, and Methods</span>

The term "class" refers to all **classes, interfaces, and traits**.

Any closing brace **MUST NOT** be followed by any comment or statement on the same line.

When instantiating a new class, parentheses **MUST** always be present even when there are no arguments passed to the constructor.

```
new Foo();
```


#### <span style="color:green">Extends and Implements</span>

The extends and implements keywords **MUST** be declared on the same line as the class name.

The opening brace for the class **MUST** go on its own line; the closing brace for the class **MUST** go on the next line after the body.

Opening braces **MUST** be on their own line and **MUST NOT** be preceded or followed by a blank line.

Closing braces **MUST** be on their own line and **MUST NOT** be preceded by a blank line.

```
?php

namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // constants, properties, methods
}
```

Lists of ```implements``` and, in the case of interfaces, ```extends``` **MAY** be split across multiple lines, where each subsequent line is indented once. When doing so, the first item in the list **MUST** be on the next line, and there **MUST** be only one interface per line.

```
<?php

namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // constants, properties, methods
}
```

#### <span style="color:green">Using Traits</span>

The ```use``` keyword used inside the classes to implement traits **MUST** be declared on the next line after the opening brace.

```
<?php

namespace Vendor\Package;

use Vendor\Package\FirstTrait;

class ClassName
{
    use FirstTrait;
}
```

Each individual trait that is imported into a class **MUST** be included one-per-line and each inclusion **MUST** have its own ```use``` import statement.

```
<?php

namespace Vendor\Package;

use Vendor\Package\FirstTrait;
use Vendor\Package\SecondTrait;
use Vendor\Package\ThirdTrait;

class ClassName
{
    use FirstTrait;
    use SecondTrait;
    use ThirdTrait;
}
```

When the class has nothing after the use import statement, the class closing brace **MUST** be on the next line after the ```use``` import statement.

```
<?php

namespace Vendor\Package;

use Vendor\Package\FirstTrait;

class ClassName
{
    use FirstTrait;
}

```

Otherwise, it **MUST** have a blank line after the ```use``` import statement.

```
<?php

namespace Vendor\Package;

use Vendor\Package\FirstTrait;

class ClassName
{
    use FirstTrait;

    private $property;
}
```

#### <span style="color:green">Properties and Constants</span>

Visibility **MUST** be declared on all properties.

Visibility **MUST** be declared on all constants if your project PHP minimum version supports constant visibilities (PHP 7.1 or later).

The ```var``` keyword **MUST NOT** be used to declare a property.

There **MUST NOT** be more than one property declared per statement.

Property names **MUST NOT** be prefixed with a single underscore to indicate protected or private visibility. That is, an underscore prefix explicitly has no meaning.

There **MUST** be a space between type declaration and property name.
\
A property declaration looks like the following:

```
<?php

namespace Vendor\Package;

class ClassName
{
    public $foo = null;
    public static int $bar = 0;
}
```

#### <span style="color:green">Methods and Functions</span>

Visibility **MUST** be declared on all methods.

Method names **MUST NOT** be prefixed with a single underscore to indicate protected or private visibility. That is, an underscore prefix explicitly has no meaning.

Method and function names **MUST NOT** be declared with space after the method name. The opening brace MUST go on its own line, and the closing brace MUST go on the next line following the body. There **MUST NOT** be a space after the opening parenthesis, and there **MUST NOT** be a space before the closing parenthesis.
\
A method declaration looks like the following. **Note the placement of parentheses, commas, spaces, and braces**:

```
<?php

namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```

Argument lists **MAY** be split across multiple lines, where each subsequent line is indented once. When doing so, the first item in the list **MUST** be on the next line, and there **MUST** be only one argument per line.

When the argument list is split across multiple lines, the closing parenthesis and opening brace **MUST** be placed together on their own line with one space between them.

```
<?php

namespace Vendor\Package;

class ClassName
{
    public function aVeryLongMethodName(
        ClassTypeHint $arg1,
        &$arg2,
        array $arg3 = []
    ) {
        // method body
    }
}
```

When you have a return type declaration present, there **MUST** be one space after the colon followed by the type declaration. The colon and declaration **MUST** be on the same line as the argument list closing parenthesis with no spaces between the two characters.

```
<?php

declare(strict_types=1);

namespace Vendor\Package;

class ReturnTypeVariations
{
    public function functionName(int $arg1, $arg2): string
    {
        return 'foo';
    }

    public function anotherFunction(
        string $foo,
        string $bar,
        int $baz
    ): string {
        return 'foo';
    }
}
```

In nullable type declarations, there **MUST NOT** be a space between the question mark and the type.

```
<?php

declare(strict_types=1);

namespace Vendor\Package;

class ReturnTypeVariations
{
    public function functionName(?string $arg1, ?int &$arg2): ?string
    {
        return 'foo';
    }
}

```

When using the reference operator ```&``` before an argument, there **MUST NOT** be a space after it, like in the previous example.

There **MUST NOT** be a space between the variadic three dot operator and the argument name:

```
public function process(string $algorithm, ...$parts)
{
    // processing
}
```

When combining both the reference operator and the variadic three dot operator, there **MUST NOT** be any space between the two of them:

```
public function process(string $algorithm, ...$parts)
{
    // processing
}
```

#### <span style="color:green">Methods and Functions Calls</span>

When making a method or function call, there **MUST NOT** be a space between the method or function name and the opening parenthesis, there **MUST NOT** be a space after the opening parenthesis, and there **MUST NOT** be a space before the closing parenthesis. In the argument list, there **MUST NOT** be a space before each comma, and there **MUST** be one space after each comma.

```
<?php

bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);
```

Argument lists **MAY** be split across multiple lines, where each subsequent line is indented once. When doing so, the first item in the list MUST be on the next line, and there MUST be only one argument per line. A single argument being split across multiple lines (as might be the case with an anonymous function or array) does not constitute splitting the argument list itself.

```
<?php

$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);
```
```
<?php

somefunction($foo, $bar, [
  // ...
], $baz);

$app->get('/hello/{name}', function ($name) use ($app) {
    return 'Hello ' . $app->escape($name);
});
```

#### <span style="color:green">Control Structures</span>

The general style rules for control structures are as follows:

* There **MUST** be one space after the control structure keyword
* There **MUST NOT** be a space after the opening parenthesis
* There **MUST NOT** be a space before the closing parenthesis
* There **MUST** be one space between the closing parenthesis and the opening brace
* The structure body **MUST** be indented once
* The body **MUST** be on the next line after the opening brace
* The closing brace **MUST** be on the next line after the body

##### ```if```

An ```if``` structure looks like the following. **Note the placement of parentheses, spaces, and braces**. ```elseif``` and ```else``` **MUST NOT** not be used and do an early return instead.

```
<?php`

if ($expr1) {
    // if body
}
```

Expressions in parentheses **MAY** be split across multiple lines, where each subsequent line is indented at least once. When doing so, the first condition **MUST** be on the next line. The closing parenthesis and opening brace **MUST** be placed together on their own line with one space between them. Boolean operators between conditions **MUST** always be at the beginning or at the end of the line, not a mix of both.

```
<?php

if (
    $expr1
    && $expr2
) {
    // if body
}
```

##### ```switch```, ```case```

A ```switch``` structure looks like the following. **Note the placement of parentheses, spaces, and braces**. The ```case``` statement **MUST** be indented once from ```switch```, and the ```break``` keyword (or other terminating keywords) **MUST** be indented at the same level as the case body. There **MUST** be a comment such as ```// no break``` when fall-through is intentional in a non-empty ```case``` body.

```
<?php

switch ($expr) {
    case 0:
        echo 'First case, with a break';
        break;
    case 1:
        echo 'Second case, which falls through';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'Third case, return instead of break';
        return;
    default:
        echo 'Default case';
        break;
}
```

Expressions in parentheses **MAY** be split across multiple lines, where each subsequent line is indented at least once. When doing so, the first condition **MUST** be on the next line. The closing parenthesis and opening brace **MUST** be placed together on their own line with one space between them. Boolean operators between conditions **MUST** always be at the beginning or at the end of the line, not a mix of both.

```
<?php

switch (
    $expr1
    && $expr2
) {
    // structure body
}
```

##### ```while```, ```do while```

A ```while``` and ```do while``` statement looks like the following. **Note the placement of parentheses, spaces, and braces**.

```
<?php

while ($expr) {
    // structure body
}
```

```
<?php

do {
    // structure body;
} while ($expr);
```


Expressions in parentheses **MAY** be split across multiple lines, where each subsequent line is indented at least once. When doing so, the first condition **MUST** be on the next line. The closing parenthesis and opening brace **MUST** be placed together on their own line with one space between them. Boolean operators between conditions **MUST** always be at the beginning or at the end of the line, not a mix of both.

```
<?php

while (
    $expr1
    && $expr2
) {
    // structure body
}
```

```
<?php

do {
    // structure body;
} while (
    $expr1
    && $expr2
);
```

##### ```for```

A ```for``` statement looks like the following. **Note the placement of parentheses, spaces, and braces**.

```
<?php

for ($i = 0; $i < 10; $i++) {
    // for body
}
```

##### ```foreach```

A ```foreach``` statement looks like the following. **Note the placement of parentheses, spaces, and braces**.

```
<?php

foreach ($iterable as $key => $value) {
    // foreach body
}
```

##### ```try```, ```catch```, ```finally```

A ```try-catch-finally``` block looks like the following. **Note the placement of parentheses, spaces, and braces**.

```
<?php

try {
    // try body
} catch (FirstThrowableType $e) {
    // catch body
} catch (OtherThrowableType | AnotherThrowableType $e) {
    // catch body
} finally {
    // finally body
}
```

#### <span style="color:green">Operators</span>

Style rules for operators are grouped by arity (the number of operands they take).

When space is permitted around an operator, multiple spaces **MAY** be used for readability purposes.

All operators not described here are left undefined.

The increment/decrement operators **MUST NOT** have any space between the operator and operand.

```
$i++;
++$j;
```

Type casting operators **MUST NOT** have any space within the parentheses:

```
$intValue = (int) $input;
```

##### ```Binary Operators```

All **binary arithmetic, comparison, assignment, bitwise, logical, string, and type operators** **MUST** be preceded and followed by at least one space:

```
if ($a === $b) {
    $foo = $bar ?? $a ?? $b;
} elseif ($a > $b) {
    $foo = $a + $b * $c;
}
```

##### ```Ternary Operators```

The conditional operator, also known simply as the ternary operator, **MUST** be preceded and followed by at least one space around both the``` ?``` and ```:``` characters:

```
$variable = $foo ? 'foo' : 'bar';
```

When the middle operand of the conditional operator is omitted, the operator **MUST** follow the same style rules as other binary comparison operators:

```
$variable = $foo ?: 'bar';
```

#### <span style="color:green">Closures</span>

Closures **MUST** be declared with a space after the ```function``` keyword, and a space before and after the ```use``` keyword.

The opening brace **MUST** go on the same line, and the closing brace **MUST** go on the next line following the body.

There **MUST NOT** be a space after the opening parenthesis of the argument list or variable list, and there **MUST NOT** be a space before the closing parenthesis of the argument list or variable list.

In the argument list and variable list, there **MUST NOT** be a space before each comma, and there **MUST** be one space after each comma.

Closure arguments with default values **MUST** go at the end of the argument list.

If a return type is present, it **MUST** follow the same rules as with normal functions and methods; if the ```use``` keyword is present, the colon **MUST** follow the ```use``` list closing parentheses with no spaces between the two characters.

A closure declaration looks like the following. **Note the placement of parentheses, commas, spaces, and braces**:

```
<?php

$closureWithArgs = function ($arg1, $arg2) {
    // body
};

$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // body
};

$closureWithArgsVarsAndReturn = function ($arg1, $arg2) use ($var1, $var2): bool {
    // body
};
```

Argument lists and variable lists **MAY** be split across multiple lines, where each subsequent line is indented once. When doing so, the first item in the list **MUST** be on the next line, and there **MUST** be only one argument or variable per line.

When the ending list (whether of arguments or variables) is split across multiple lines, the closing parenthesis and opening brace **MUST** be placed together on their own line with one space between them.

The following are examples of closures with and without argument lists and variable lists split across multiple lines.

```
<?php

$longArgs_noVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {
   // body
};

$noArgs_longVars = function () use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};

$longArgs_longVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};

$longArgs_shortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {
   // body
};

$shortArgs_longVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};
```

Note that the formatting rules also apply when the closure is used directly in a function or method call as an argument.

```
<?php

$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
        // body
    },
    $arg3
);
```

#### <span style="color:green">Anonymous Classes</span>

Anonymous Classes **MUST** follow the same guidelines and principles as closures in the above section.

```
<?php

$instance = new class {};
```

The opening brace **MAY** be on the same line as the ```class``` keyword so long as the list of ```implements``` interfaces does not wrap. If the list of interfaces wraps, the brace MUST be placed on the line immediately following the last interface.

```
<?php

// Brace on the same line
$instance = new class extends \Foo implements \HandleableInterface {
    // Class content
};

// Brace on the next line
$instance = new class extends \Foo implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // Class content
};
```

# Do's and Dont's