# XMLParser
Project Title: XMLParser<Enter>
Prject description: 
	This project reads XML files and displays any problems with the format of
	the file. When the program has finished analyzing the file, it will display 
	"Finished analyzing file."

	The program checks different types of tags:
		start tags:		<tag>
		end tags:		</tag>
		Self closing tag:	<tag/>
		Processing tags:	<?tag?>
		Comment tags: 		<!-- tag -->
----------------------------------------
 <ul>
   <li>The algorithm used to analyze the XML file is by Kitty Wong.</li>
   <li>The project uses the classes in the utilities package in the src folder.</li>
   <li>The rules this program follows for XML documents are as follows:</li>
  <ol>
    <li>An opening tag has the format <tag>, a closing tag has the format</tag>.</li>
    <li>XML tags may contain attributes in the format of name=”value” pairs, these attributes are to be ignored for this assignment.</li>
    <li>For every closing tag, there is an earlier matching opening tag.</li>
    <li>An exception to the above is a self-closing tag, a self-closing tag has the format <tag/>. Self-closing tags require no closing tag.</li>
     <li>The sub phrase between a pair of matching tags is itself well-constructed.</li>
    <li>All tags are case-sensitive.</li>
    <li>Every XML document must have one and only one root tag.</li>
    <li>Tags that are in the following format <?xml somedata=”data”?> are processing instructions and can be ignored for this assignment.</li>
    <li>If nested, the tag pairs cannot intercross.</li>
  </ol> 
  </ul>

### H3 Kitty’s XML Parser Algorithm
```
If Self_Closing_Tag
	Ignore
If Start_Tag
	Push on stack
If End_Tag
	If matches top of stack, pop stack and all is well
	Else if matches head of errorQ, dequeue and ignore
	Else if stack is empty, add to errorQ
	Else
		Search stack for matching Start_Tag
		If stack has match
			Pop each E from stack into errorQ until match, report as error
		Else
			Add E to extrasQ
Repeat until EOF

If stack is not empty, pop each E into errorQ
If either queue is empty (but not both), report each E in both queues as error
If both queues are not empty, peek both queues
	If they don’t match, dequeue from errorQ and report as error
	Else dequeue from both
Repeat until both queues are empty
  ```

# Execusion
  To run this program use the following format in the command prompt:<br>
  (note: replace the "file" in this command with the XML file wanting to analyze
	and add the location of the file at the begining of the name of the file if the file 
	is not in the same directory as Parser.jar)
  
```java -jar Parser.jar file```
  
# Authors
  <ul>
    <li>Mahdiyeh Abbaspour(<a href="https://github.com/m-abbaspour">m-abbaspour</a>)</li>
    <li>Travis Milne (<a href="https://github.com/TAMilne">TAMilne</a>)</li>
    <li>Kyle Helmer</li>
    <li>Minjong Park (<a href="https://github.com/mjp9404">mjp9404</>)</li>
    
  </ul>


# Known deficiencies
<ol>
	<li>Closing tags with no start tags are not considred incorrect (This is because of the 
    Kitty Algorithm)</li>
	<li>values between tags are not processed (e.g. a ">" in between tags is not considred 
    incorrect.</li>
  <li>Any deficiencies in the Kitty Algorithm.</li>
</ol>
  
********************************************************************************************
Created: July 17, 2022
	

