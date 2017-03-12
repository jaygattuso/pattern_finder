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

  <i>`Files used to make pattern: 3192, Start offset: 0, End offset: 10`</i>
  
The second line either shows you the raw hex pattern, or tells you if didn't find a common pattern
(e.g. at least one byte that is commonly found in the same sequence location in all given files):

  <i>`7b5c727466315c***`</i>
  
or 

  <i>`No pattern detected`</i>
  
The third line tries to UTF8 encode the pattern and display pattern as text. (using python `repr()`):
N.B the wildcard "*" is replaced with a "space" character for legibility. 

  <i>`{\\rtf1\\   `</i>
  
# how to use
 
Using what ever method makes sense, put together a list of valid filepaths. 
  
Instantiate the Pattern_Detector() class, giving the list and start and end byte offsets
  
These default as follows if not given:
start offset: `start = 0`
end offset: `end = 50`
files: `files_list = []` 
  
or 
  
  `patterns = Pattern_Detector(files_list = my_list)`
  
  `patterns = Pattern_Detector(start = 10, files_list = my_list)`
  
  `patterns = Pattern_Detector(start = 10, end = 1000, files_list = my_list)`
  
These can addressed in code as a class object
  
  `patterns.start = 0`
  
  `patterns.end = 0`
  
  `patterns.files_list = ["my_file_1.ext","my_file_2.ext","my_file_3.ext"]`
  
THe script is currently configured to just run when given a list. 
