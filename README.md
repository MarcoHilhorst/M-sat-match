# M-sat-match
A small tool to automate the identification of matching microsatellite profiles and potential parent-offspring relationships. Takes in a JSON file and spits out results, beautiful!

**Link to project:** https://m-sat-match.netlify.app/

![screenshot](https://m-sat-match.netlify.app/images/M-sat-match-image.jpg)

## How it's made:
**Tech used:** <img height="20" src="https://user-images.githubusercontent.com/25181517/192158954-f88b5814-d510-4564-b285-dff7d6400dad.png" alt="HTML" title="HTML" /> HTML <img height="20" src="https://user-images.githubusercontent.com/25181517/183898674-75a4a1b1-f960-4ea9-abcb-637170a00a75.png" alt="CSS" title="CSS" /> CSS <img height="20" src="https://user-images.githubusercontent.com/25181517/117447155-6a868a00-af3d-11eb-9cfe-245df15c9f3f.png" alt="JavaScript" title="JavaScript" /> Javascript

The app uses the FileReader api and .JSON parser to allow for local files to be loaded. Uses client side Javascript to run the tests and manipulate the DOM. Can be used offline by opening the .html document.

## Optimisations:
The first working version compared all samples to all samples, resulting in each sample being compared to itself and being recorded as a positive match. I added a conditional that stopped this by checking the sample names weren't identical.
Positive matches would also duplicate , E.G:

* Sample 1 matches sample 5
* Sample 5 matches sample 1

To remedy this, the sample ids of positive matches are checked against an array of previous positive results. If the two sample ids aren't contained in an array inside of the results array they are added to the results array and updated in the DOM. If the two sample ids are contained as a pair within the results array, the result is not posted in the DOM. Example below:

Results = [[sample 1, sample 5], [sample 3, sample 4]]. 

When the program finds that sample 5 matches sample 1, it will not post it to the DOM as the results array has a pair(array) that contains both sample 5 and sample 1 already.


In the future I would like to move the positioning of the above optimisations to run before the third loop to save a bit of time. I would also like to add some validation to ensure that the first three property names are the same as those specified in the 'how to use the program' dropdown. And finally, having a message to inform users if they have loaded a file that isn't a .JSON file.

## Lessons learned:
