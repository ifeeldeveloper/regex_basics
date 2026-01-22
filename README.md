# regex_basics

txt = """I love Python. I have started my class from 2025-12-01. I think it will be completed by 2026-02-01. We learned python first. Our class start from 8 AM and ends in 8:30 AM. Material links can be found at sapkotarabindra.com.np. We do practice at colab.google.com. We are now looking at www.regex101.com. My email is rabindrasapkota2@gmail.com. Some people create email as test@yahoo.com. Our class members are Mr Kalyan, Mr Roshan, Ms. Barsha, Mr. Jagdish but Mr. Bishal is absent today. Python is fun. We see 2+2=4 but interestingly 2*2 is also 4. What is this? Rat, Cat and Hat have similar sound.Bat, Sat is also same. Bat BatBat BatBatBat BatBatBatBat  BatBatBatBatBat. My number is 9876543210 another one is 9868584838. Non Nepali number i guess 1234567890 and random number 98745632101236547890.
Dates 2025.05.01 2024/01/03 20210908 2025-02/05 2022-02-02. I bought pen for Rs 20, Apple for Rs 300 and Orange for Rs 200. Their weights were 1kg and 2kg.
9874563210
9876541230123456789868546987
9856320147 asdf
asdf 9865742310
asdf 98657423101235
jkl 9856320147 asdf
"""

# Quantifier
+ ==> One or more repetition of preceding regex
* ==> Zero or more repetition of preceding regex
? ==> Zero or one repetition of preceding regex

+ = {1, }
? = {0, 1}
* = {0, }

# Group 
() -> default capturing group
(?:) -> non capturing group

# Look Ahead and Look Behind
look behind => eg.->(?<=Rs )\d+
look ahead => eg.->\d+(?=kg)

# Special Character with special meaning
. ==> Matches any character except new line
+ ==> [A-Za-z]+ -> matches one or more
* ==>
? ==> May or may not matches
^ ==> Match happens at beginning of string 
$ ==> Match happens at the end of string
| ==> Matches regex expressions preceeding or following it
[...] ==> Matches range of values inside the given brackets (eg. [A-Za-Z0-9]
(...) ==> Provide regex inside it and Match for it
[^...] ==> Matches characters that doesn't matches regex inside bracket (eg. [^0-9] matches except numbers)
(R|S) ==> R and S are multiple regexes. Matches R or S
\ ==> escape character

# Special Character section 2
\t ==> Tab
\n ==> New Line
\d ==> Any digits between 0-9
\D ==> Any non-digit character or ([^\d])
\s ==> White Space, Space, Tab, New Line
\S ==> Non White Space
\w ==> Any alphanumeric characters (A-Z,a-z,0-9)
\W ==> Non alphanumeric characters
\b ==> Space around words
\B ==> Non word boundary. i.e no space around word

# Regular Expressions
1. Literal match
->Python
->Cat
->at
->python

2. Character Class
->[BHC]at 
->[A-Z]
->[a-z]
->[0-9]
->[e-s]
->[A-Za-z0-9]
->[E-Sa-j]
->[A-Za-z248]

3. (exp|exp|exp)
->(Cat|Hat|Rat)
->(Mr|Ms)
->(Mr|Ms)\. [A-Za-z]+
->(Mr|Ms)\. ([A-Za-z]+)

4. gmail/ site matching from above string
->[A-Za-z0-9]+@[a-z]+\.[a-z]+ 
->[A-Za-z0-9]+\.[a-z]+\.[a-z]+
->[A-Za-z0-9]+\.[a-z0-9]+\.[a-z]+
-> (www\.)?[A-Za-z0-9]+\.[a-z]+\.([a-z]+)?

5. 
->(Bat){2}
->(Bat){2,3}
->(Bat){3,}

6. Number Matching
->[0-9]{10}
->9[0-9]{9}

7. Date Matching
->[0-9]{4}-[0-9]{2}-[0-9]{2}
->[12][0-9]{3}-[0-9]{2}-[0-9]{2}
->[12][0-9]{3}[-\.][0-9]{2}[-\.][0-9]{2}
->[12][0-9]{3}[-\.\/][0-9]{2}[-\.\/][0-9]{2}
->[12][0-9]{3}[-\.\/]?[0-9]{2}[-\.\/]?[0-9]{2}
->[12][0-9]{3}([-\.\/])?[0-9]{2}\1?[0-9]{2}
->([12][0-9]{3})([-\.\/])?([0-9]{2})\2?([0-9]{2})
->([12][0-9]{3})([-\.\/])?([0-9]{2})\2?\3(matches same month and same date value)
->([12]\d{3})([-\.\/])?(\d{2})\2?\3
->([12]\d{3})([-\.\/])?(\d{2})\2?(\d{2})

8.
->Rs \d+
->Rs (\d+)
->(?<=Rs )\d+(look behind)
->(?<!Rs )\d+
->\d+(?=kg)(look ahead)

9.
->(Mr|Ms|Mrs)\.?\s[A-Za-z]+
->M[rs]\.?\s[A-Za-z]+
->(?<=M[rs]\.\s)[A-Za-z]+
->(?<=M[rs]\.\s)[A-Za-z]+|(?<=M[rs]\s)[A-Za-z]+

10. Anchor + bound
->9\d{9}
->^9\d{9}
->9\d{9}$
->^9\d{9}$
->9\d{9}\b
->\b9\d{9}
->\b9\d{9}\b
