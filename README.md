# Regex Basics

### Text/String on regular expressions performed
txt = """I love Python. I have started my class from 2025-12-01. I think it will be completed by 2026-02-01. We learned python first. Our class start from 8 AM and ends in 8:30 AM. Material links can be found at sapkotarabindra.com.np. You can visit my portfolio website as well at jagadishbhatta.com.np. We do practice at colab.google.com. and Jupyter Notebook. We are now looking at www.regex101.com. My email is jagadishbhatta16@gmail.com. Some people create email as test@yahoo.com. Our class members are Mr Kalyan, Mr Roshan, Ms. Barsha, Mr. Jagdish but Mr. Bishal is absent today. Python is fun. We see 2+2=4 but interestingly 2*2 is also 4. What is this? Rat, Cat and Hat have similar sound.Bat, Sat is also same. Bat BatBat BatBatBat BatBatBatBat  BatBatBatBatBat. My number is 9876543210 another one is 9868584838. Non Nepali number i guess 1234567890 and random number 98745632101236547890.
Dates 2025.05.01 2024/01/03 20210908 2025-02/05 2022-02-02. I bought pen for Rs 20, Apple for Rs 300 and Orange for Rs 200. Their weights were 1kg and 2kg.<br>
9874563210<br>
9876541230123456789868546987<br>
9856320147 asdf<br>
asdf 9865742310<br>
asdf 98657423101235<br>
jkl 9856320147 asdf<br>
The cat sat on the mat.<br>
There are 3 apples and 12 oranges<br>
(+977) 456-7890<br>
+977 9868-888-764<br>
Hello, its me Jagadish.<br>
hello, I am learning regex and hello Hello<br>
\+ is a quantifier which match one or more repetition of preceding. There are two types of groups in regex, capturing(default group) and non capturing group.<br> 
It weights 12kg, 14m, 34kg<br>
9843468713 / 984-3468-713 / +9779843468713.<br>
abc.def.ghi.jkx
```html
<div>
<p> This is a paragraph tag </p> 
<a href = "www.jagadishbhatta.com.np"> visit my website</a>
</div>
```
"""

## Quantifier
* \+ => One or more repetition of preceding regex
* \* => Zero or more repetition of preceding regex
* ? => Zero or one repetition of preceding regex

## Repetitions or quantifier extended
* \+ = {1, } => one or more repetitions

* ? = {0, 1} => zero or one repetions

* \* = {0, } => zero or more repetitions

* {x} => number of x repetitions 

* {x, y} => repetitions between x and y, both are inclusive

## Special Character
* \t => Tab
* \n => New Line
* \d => Any digits between 0-9
* \D => Any non-digit character or (```[^\d]```)
* \s => White Space Characters ( Space, Tab, New line )
* \S => Non White Space Characters
* \w => Any alphanumeric characters (A-Z,a-z,0-9,_) ( word characters )
* \W => Non alphanumeric characters ( Non word characters )
* \b => Space around words
* \B => Non word boundary. i.e no space around word

## Special Character with special meaning
* . => Matches any character except new line
* \+ => ```[A-Za-z]+``` matches one or more character
* \* => matches zero or more characters
* ? => May or may not matches ( matches zero or one character )
* ^ => Match happens at beginning of string  ( Matching start )
* $ => Match happens at the end of string ( Matching end )
* | => Matches regex expressions preceeding or following it
* [...] => Matches range of values inside the given brackets (eg. ```[A-Za-Z0-9]```) ( character class )
* (...) => Provide regex inside it and Match for it ( group )
* [^...] => Matches characters that doesn't matches regex inside bracket (eg. ```[^0-9]``` matches except numbers)
* (R|S) => R and S are multiple regexes. Matches R or S
* \ => escape character

## Group 
* () -> default capturing group
* (?:) -> non capturing group
* ``\bcat\b`` -> word boundary ( not in group but i placed here )
* ``^\d\S{5}$`` -> matching start and end ( not in group bit i placed here )

## Assertions (Look Ahead and Look Behind)
* Positive look ahead => eg. ```\d+(?=kg)``` string = '**2**kg' => 2
* Negative look ahead => eg. ```c(?!o)``` string = '**c**hocolate' => c
* Positive look behind => eg. ```(?<=Rs )\d+``` string = 'Rs **200**' => 200
* Negative look behind => eg. ```(?<![a-z])[aeiou]``` string = 'he1**o**' => o

# Regular Expressions - Practice these on regex101.com
### 1. Literal match
* ```Python```
* ```Cat```
* ```at```
* ```python```

### 2. Character Class
* ```[BHC]at```
* ```[^A-Z]```
* ```[a-z]```
* ```[0-9]```
* ```[e-s]```
* ```[A-Za-z0-9]```
* ```[E-Sa-j]```
* ```[A-Za-z248]```

### 3. (exp|exp|exp)
* ```(Cat|Hat|Rat)```
* ```(Mr|Ms)```
* ```(Mr|Ms)\. [A-Za-z]+```
* ```(Mr|Ms)\. ([A-Za-z]+)```

### 4. gmail/ site matching from above string
* ```[A-Za-z0-9]+@[a-z]+\.[a-z]+```
* ```[A-Za-z0-9]+\.[a-z]+\.[a-z]+```
* ```[A-Za-z0-9]+\.[a-z0-9]+\.[a-z]+```
*  ```(www\.)?[A-Za-z0-9]+\.[a-z]+\.([a-z]+)?```

### 5. Repetitions
* ```(Bat){2}```
* ```(Bat){2,3}```
* ```(Bat){3,}```

### 6. Number Matching
* ```[0-9]{10}```
* ```9[0-9]{9}```

### 7. Date Matching
* ```[0-9]{4}-[0-9]{2}-[0-9]{2}```
* ```[12][0-9]{3}-[0-9]{2}-[0-9]{2}```
* ```[12][0-9]{3}[-\.][0-9]{2}[-\.][0-9]{2}```
* ```[12][0-9]{3}[-\.\/][0-9]{2}[-\.\/][0-9]{2}```
* ```[12][0-9]{3}[-\.\/]?[0-9]{2}[-\.\/]?[0-9]{2}```
* ```[12][0-9]{3}([-\.\/])?[0-9]{2}\1?[0-9]{2}```
* ```([12][0-9]{3})([-\.\/])?([0-9]{2})\2?([0-9]{2})```
* ```([12][0-9]{3})([-\.\/])?([0-9]{2})\2?\3``` (matches same month and same date value)
* ```([12]\d{3})([-\.\/])?(\d{2})\2?\3```
* ```([12]\d{3})([-\.\/])?(\d{2})\2?(\d{2})```

### 8. Assertions 
* ```Rs \d+```
* ```Rs (\d+)```
* ```(?<=Rs )\d+``` (look behind)
* ```(?<!Rs )\d+```
* ```\d+(?=kg)``` (look ahead)

### 9. 
* ```(Mr|Ms|Mrs)\.?\s[A-Za-z]+```
* ```M[rs]\.?\s[A-Za-z]+```
* ```(?<=M[rs]\.\s)[A-Za-z]+```
* ```(?<=M[rs]\.\s)[A-Za-z]+|(?<=M[rs]\s)[A-Za-z]+```

### 10. Anchor + bound
* ```9\d{9}```
* ```^9\d{9}```
* ```9\d{9}$```
* ```^9\d{9}$```
* ```9\d{9}\b```
* ```\b9\d{9}```
* ```\b9\d{9}\b```

### 11. Backreference
* ```([12][0-9]{3})([-\.\/])?([0-9]{2})\2?\3``` (matches same month and same date value)

# Regex Exercises with questions
1. Match the word "cat" in a sentence. (Example text: "The cat sat on the mat.“)
* rgx >> ```cat```
2. Find digit in a sentence. ("There are 3 apples and 12 oranges.“) [3,1,2]
* rgx >> ```\d```
3. Match any lowercase letter from word.
* rgx >> ```[a-z]```
4. Match all 5-letter word in a text
* rgx >> ```\b[A-Za-z]{5}\b```
5. Match email address from the text
* rgx >> ```\w+@[a-z]+\.com```
6. Match phone numbers in the format (+977) 456-7890 (+977 9868-888-764)
* rgx >> ```\+977 \d{4}-\d{3}-\d{3}```
7. Match string that starts with hello at beginning of line
* rgx >> ```^[Hh]ello\b```
8. Match word that ends with ing. [Match word only ensuring ing is after it]
* rgx >> ```\b[A-Za-z]+ing\b```
9. You have a document with text: 12kg, 14m, 34kg … . Capture weights from it
* rgx >> ```\d+(?=kg|m)```
10. You have a html document. Match tag names on it. Example: div, a, p
* rgx >> ```(?<=<)[a-zA-Z]+[0-9]*```
11. You can have numbers as 9843468713 / 984-3468-713 / +9779843468713. Capture all phone
number following these patterns from the document
* rgx >> ```(?:\+977)?9\d{2}-?\d{4}-?\d{3}```
12. Match this pattern "abc.def.ghi.jkx"
* rgx >> ```^...\....\....\....$```
