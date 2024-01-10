# Matryoshka Doll

### Description

Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one?

The file provided is aptly named “dolls.jpg” and is, of course, a picture of a Matryoshka doll. This already gives us a hint on what to do with the file. Using GHex to analyse the file shows that there’s a directory hidden inside of the actual .jpg at offset 0x4288A.


Using `binwalk -e -M dolls.jpg` (-e extract -M Matryoshka mode, who would’ve guessed) extracts all files & .zip archives from the picture and puts them in a new directory. After a few `cd`s through all the directories inside, the flag.txt file is found. Easy peasy.
