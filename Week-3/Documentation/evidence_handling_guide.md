Practical secnario & step by step what to do in this 

Step 1 Using a Write Blocker safely deliver suspious things to workstation(lab)

Step 2 create forensics image of hard drive so copies so we can get back real data if something get wrong 
          "sudo dd if=/dev/sdb of=evidence.dd bs=4M status=progress" manually using GUI in Screenshot folder too
          
Step 3 generate Hash value for the image & suspisious things so we know if any change happned in that 
          "shasum -a 256 evidence.dd" GUI in screenshot folder using Hash app from GITHUB

Step 4 perform analysis using FTK & Autopsy tools and their SS for analysis & check deleted or suspisius thing in analysis 

Step 5 Verify Integrity after analysis making report before so both hash matches that means evidance integrity & no tempuring in data 

Step 6 Secure all Data, report & suspisious things too, locked that so no human intraction so all safe in our hand without any risk!
