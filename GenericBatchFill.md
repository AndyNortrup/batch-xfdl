# Generic Batch Fill #

My concept is to create a wizard type interface:

  1. User selects an XFDL document and a data file (Excel really needs to be the end target for anything that is going to work for people in the Army, but comma separated may be an intermediate step).
  1. Program pulls a listing of all fields in the document (all 

&lt;field&gt;

 nodes), as well as a listing of data from the data file (first record?).
  1. User associates data to form fields. Once association is complete the program can batch create completed files.

## Issues ##

At present there is no identifiable method to collect all of the fields and then present the user with human readable information about what the field is.  Each field has an SID and an acclabel (accessibility label).  Unfortunately, the SID is a machine unique identifier, and the acclabel is intended to be read by a screen reader, and would not necessarily be the best choice for printing in a UI.  Example field is listed below:

```
<field sid="RECPTNR">
         <itemlocation>
            <ae>
               <ae>absolute</ae>
               <ae>1083</ae>
               <ae>101</ae>
            </ae>
            <ae>
               <ae>extent</ae>
               <ae>136</ae>
               <ae>24</ae>
            </ae>
         </itemlocation>
         <value/>
         <borderwidth>0</borderwidth>
         <fontinfo>
            <ae>Times New Roman</ae>
            <ae>10</ae>
            <ae>plain</ae>
         </fontinfo>
         <scrollhoriz>wordwrap</scrollhoriz>
         <scrollvert>fixed</scrollvert>
         <format>
            <ae>string</ae>
            <ae>optional</ae>
         </format>
         <next>ENDITEMS</next>
         <previous>TO</previous>
         <acclabel>enter hand receipt number.
</acclabel>
      </field>

```

### Possible solution ###
Render the form in a java window and allow the user to drag and drop the columns they want to fill from into the fields they want filled.

I think that the above is probably the best solution, but requires a huge effort to implement the XFDL standard in the code, which hurts.  So until then I'm going to drop back and shoot for something more realistic.

Current plan is to display all of the fields in order down the page along with the SID, and hope that they are readable enough that people can figure out what they are trying to fill.  Testing will show if this is viable or not.