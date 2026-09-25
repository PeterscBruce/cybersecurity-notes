# Digital Forensics

Digital forensics investigates cyber crime, criminal activity on digital devices, using tools and techniques to find and analyze evidence for legal action.

* Digital devices make life easier but fuel a rise in cybercrime

## NIST (National Institute of Standards and Technology)

* Works on providing frameworks for different areas of technology, including cybersecurity
* Four Phases: Collection, Examination, Analysis, Reporting

## Types of Digital Forensics

* Disk Forensics
* Network Forensics
* Database Forensics
* Memory Forensics
* Mobile Forensics
* +more

## Acquiring Evidence

Acquiring evidence is a critical job. The forensics team must collect all evidence securely without tampering with original data.

### Proper Authorization

* Proper authorization before collecting data is essential
* If not, evidence may be deemed inadmissible in court
* Contains private and sensitive info

### Chain of Custody

A chain of custody is a formal document containing all the details of the evidence.

* Prevents any data from going missing
* Creates a proper trail of evidence

### Use of Write Blockers

* Using one will not alter any original data/docs while collecting evidence
* Ensures data integrity

## Common Evidence Sources

Desktop PCs and laptops are the most common evidence collected from crime scenes.

* **Disk Image** - contains all data present on a storage device
* **Memory Image** - all data inside OS RAM
  * This memory is volatile, meaning data will get lost after system power off

 Personal Reflection:
 There is a lot to memorise with Digital Forensics, 
 I have learned the importance of upholding the correct procedures to insure integrity is kept intact.
 Everything must be done in a certain order and following the chain of custody.
 To reinforce this area of cybersecurity, I did a crime scene simulation using Kali linux, terminal, and tools such as Autopsy.
 The crime scene- My cat had been stolen, the thief's demanded payment in crypto and they left docs containing a letter and a photo
 1. I used pdfinfo DOCUMENT.pdf- this allowed me to enter the doc and see details, the thief had left their name as the author
 2. Using Exiftool + Autopsy allowed me to extract data from the image.jpg- now I have the date, time and location of image
 3. Entering the co-ordinates into Google Maps, then I had the location of my "cat". Milk Street.

This is my explanation of the practice environment i completed.
