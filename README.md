# *THIS CODE HAS NOT YET BEEN FULLY TESTED! USE AT YOUR OWN RISK*

# Emergency Ringdown
## Inspiration
Deviant Ollam's story about his friend Kara from ["Lawyer. Passport. Locksmith. Gun. (A Talk About Risk & Preparedness)" (starting at 52:46)](https://www.youtube.com/watch?v=6ihrGNGesfI&t=52m46s) through the end of the video, but especially ["L.P.L.G.": 59:34-1:02:42](https://www.youtube.com/watch?v=6ihrGNGesfI&t=59m34s) (if you only have 60s to spare, please watch ["L.P.L.G.": 1:01:44-1:02:42](https://www.youtube.com/watch?v=6ihrGNGesfI&t=1h01m44s) to understand why this system and ones like it might be important).

Kara's story hit home for me in a very serious way as a fellow transwoman. She's living/lived my literal worst nightmare, and especially the part about her not being able to get help has always terrified me, and has prevented me from doing/pursuing some of the activism I wanted to take part in. I'm so incredibly sorry she went through everything she did, and I hope she recovers/recovered quickly and that her circumstances improve/improved even more quickly. While I can't do anything to help Kara, I can publish this code to help others like her get access to folks/activate support nets as quickly as possible.

## What does this code do?
The system being implemented here is a version of what Dev describes at ["L.P.L.G.": 1:03:29-1:04:56](https://www.youtube.com/watch?v=6ihrGNGesfI&t=1h03m29s). It creates **one phone number** for you/your loved ones to remember, where, if/when it is called by anyone, a phone call blast is sent out to all of your emergency contacts (so **everyone** knows something is wrong with someone on the list), and then it dials everyone individually in sequence (in case the first person to pick up is an answering machine/you didn't get the person/people that are most able to help you).

This solution is a more affordable version of the solution that Dev presents at ["L.P.L.G.": 1:03:29-1:04:56](https://www.youtube.com/watch?v=6ihrGNGesfI&t=1h03m29s). I can't afford $20+/mo right now on a worst case/will hopefully never need to use it solution, but I can spend $2/mo or less for the peace of mind it brings. The Basic Implementation Guide is meant so that anyone can use it, regardless of technical knowledge, because I found Twilio's UI to be somewhat unfriendly to the beginner and I don't want that to be a barrier. If any of it is found to be out of date, please log this under Issues on GitHub, with as much detail as possible.

# Basic Implementation
This system uses [Twilio.com](https://twilio.com) to implement a version of an automatic ring-down list in the most light-weight way possible (to my knowledge) and with minimal technical skill required. Copy-Paste and simple editing of names and phone numbers only.

1. Make an account at [Twilio.com](https://twilio.com)
2. Verify Email Address and set up 2FA: "Account Name" in Top Right Corner -> User Settings
3. Upgrade from Trial Account: "Upgrade" in Top Bar -> Go through prompts to add address/credit-card/etc.
    - You must have non-Trial account for Twilio to dial phone numbers other than those verified in Twilio
    - I recommend using the auto-top up feature, you want this to work, even if you've forgotten about it.
4. Have Twilio Host Your Code: Explore Products (Sidebar) -> Developer Tools -> TwiML Bins
    - Add Friendly Name
    - Copy and Paste Code from [here]()
    - Change the numbers and names as needed
    - Make sure the TwiML sytax is valid
    - Create
    - Copy the URL
5. Save App URL to a Friendly Name: Explore Products (Sidebar) -> Programmable communications -> Voice -> Manage -> TwiML Apps -> Create new TwiML App
    - Give your app a friendly name
    - Put the URL from step for into the Voice Configuration -> Request URL Field
    - Leave Request Method as HTTP POST
    - Hit Create
6. Add your Verified Caller ID: Explore Products (Sidebar) -> Super Network Section -> Phone Numbers -> Manage -> Verified Caller IDs
    - You must have Verified Caller ID to buy a phone number
7. Get a phone number: Explore Products (Sidebar) -> Super Network Section -> Phone Numbers -> Manage -> Buy a number 
    - Search for a number you/your trusted circle will remember!
    - Hit Buy!
    - Save the phone number to your phone, share with friends, and add it to a slip of paper inside of your phone case (just in case!)
8. Link Code to Phone Number(s): Explore Products (Sidebar) -> Super Network Section -> Phone Numbers -> Manage -> Active Numbers -> [The Number You Just Purchased]
    - (Optional) Give this number a friendly name (e.g. the "OH F*CK LINE")
    - Voice & Fax Section: Use the following settings
      - Accept Incoming: Voice Calls
      - Configure With: TwiML App
      - TWIML App: [The TwiML App Name you created in Step 5.]
    -Hit Save
9. Test Your System By Calling the Line
    - "*" Should disconnect you from any given call
    - It will ring everyone first to alert your entire network (the first person or answering machine to pick up is connected, all others are disconnected, but everyone should have a missed call notification).
    - Then it will go down the list individually until you hang up or it has tried every number.

# To Do List
- Test Implementation Proceedure and Take Screenshots to Add
- Implement phone tree to activate different levels of help (i.e. only activate close friends for a flat tire, activate everyone for a legal situation)
  - Add Menu Option with Default Numbers for Lawyer's Guild for Various Regions
  - Add Menu Option for Your Lawyer's Numbers
  - Add Menu Option for Important Things like ALOA's http://findalocksmith.com
- Record phone calls (where legal) and save/blast to group
- Record and send SMS with inbound call number/location/etc. if applicable.
- SMS Activation of Group
- Pin to prevent spam calls from going through (?)
- Conference Call Functionality (?)

## Deviant's List of 20 Preparedness Goals: If you're already here, why not implement some of these too?
Dev's take-away lessons from ["Lawyer. Passport. Locksmith. Gun. (A Talk About Risk & Preparedness)" (starting at 1:10:24)](https://www.youtube.com/watch?v=6ihrGNGesfI&t=1h10m24s): 

### All of these can be done without putting on pants:
1. Get (and Use!) a Good Password Manager
2. Get your Closest Friends' Contact Info (Most un-changing email address/phone number and their FULL birthdate/legal name.)
3. Establish Your Trusted Circle 
    - Give them your Top-Level MFA Backup Codes
    - Establish Check-Ins
    - Talk about the "If I have to leave my house at the drop of a hat, can I stay with you?", "I'll put up bail for you, if you'd put up bail for me." types of situations.
4. Obtain (Good!) Criminal Legal Representation 
    - Through friends, work, or just by sitting in court and seeing who does well.
    - Or start with estate planning and ask for recommendations/trusted colleagues.
5. Prepare Key Life Documents
    -E.g., Will, Personal Property Memorandum, Advance Directives, Medical Power of Attorney/Medical Authority Letters
    -Make Copies, Give to Trusted Circle
6. Get 3-4 Copies of your Birth Certificate
7. Get a Passport (or Multiple!)
8. Data Backup Solution (Make sure you have copies in case your house burns down!)
9. Insurance & Banking (Life Insurance, Valuable Personal Property Insurance, etc.; Know who gets your stuff when you die! And make sure your trusted circle knows!)
10. Shared Vault Framework (Make sure your top level password does not die with you!)

### Step outside:
11. Take a Stop the Bleed/Traumatic Wound Care Class
12. If you don't know how to shoot, go with a friend that can take you shooting. If you do know, go to a competition.
13. Find a Locksmith (During the day! http://findalocksmith.com Get their after-hours/emergency number. Test it, see if they answer!)
14. Meet your Neighbors (Get to trust them? Share a key?)

### Reach Goals: 
15. Develop Soft Skills (De-Escalation Training. Therapy! Get your head right so you can do real good when you're under stress!)
16. Go Bag & Evac Drills (Not the prepper kind!) 
    - Hardcopies and electronic copies of important documents, medicine, old glasses, diapers/pet food as needed, phone charger/power bank.
    - Run a drill: Evac the house as if you weren't coming back.
17. Second Passport

### The easy/simple ones: ;D
18. Divest from Policing
19. Abolish Prisons

20. **Never miss the opportunity to tell everyone in your life how much you love them, and how much they matter to you.**

### **__The Cavalry isn't coming, it's just us. We keep us safe.__**
