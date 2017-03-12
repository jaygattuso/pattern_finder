# pattern_finder
Helps find common binary patterns in a list of files that appear to be of the same format. 


# Usage 

Still emerging... 

The pattern finder is basic. 

It inspects the given files one by one. 
The first file becomes the master sequence
Subsequent files each are compared byte for byte against the master. 
If they match, there is no change to the master. 
If they don't match - the byte at the nonmatching sequence location is removed. 

Once all the files have been iterated over, the script prints what it knows. 
The first line tells you the parameters:

  <i>Files used to make pattern: 3192, Start offset: 0, End offset: 10</i>
  
The second line either shows you the raw hex pattern, or tells you if didn't find a common pattern
(e.g. at least one byte that is commonly found in the same sequence location in all given files):

  <i>7b5c727466315c***</i>
  
or 

  <i>No pattern detected</i>
  
The third line tries to UTF8 endcode the pattern and display pattern as text. (using python repr()):
N.B the wildcard "*" is replaced with a "space" character for legibility. 

  <i>'{\\rtf1\\   '</i>

