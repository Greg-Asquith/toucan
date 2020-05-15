# TOUCAN

<p>TOUCAN - Totally Open User Consented Ad Networks is an alternative proposal for the future of the ad ecosystem based around explicit user consent and choice. It combines elements similar to those in the TURTLEDOVE and SPARROW proposals and elements similar to how the ecosystem exists today, while utilising a different model and new browser technologies to guard user privacy.</p>

<p>The main objectives of TURTLEDOVE and SPARROW all remain satisfied:</p>

<ul>
<li>People who like ads that remind them of sites they're interested in can choose to keep seeing those sorts of ads.</li>
<li>People who don't like these types of ads can choose to avoid seeing them.</li>
<li>People who wonder "how the ad knew" what they were interested in can get a clear, accurate answer.</li>
<li>People who wish to sever their association with any interest group with which they are associated can do so and can expect to stop seeing ads targeting the group.</li>
<li>Advertisers cannot learn the browsing habits of specific people, even those who have joined multiple interest groups.
<li>Web sites cannot learn the interest groups of the people who visit them.</li>
<li>Advertisers can retain campaign control and performance in so far as this does not infringe user privacy.</li>
<li>Appropriate control over ad safety, brand safety and transparency in billing is provided to both advertisers and publishers.</li>
<li>Support for more advertising use cases, not only retargeting.</li>
<li>User experience while browsing the web is preserved.</li>
</ul>


<p>While extra objectives are also added:</p>
<ul>
<li>Users have even more control over which actors may add them to interest groups and which ads they see</li>
<li>Users may never be individually identified</li>
<li>Publishers without access to user data may also benefit from increased revenue through targeted advertising</li>
</ul>
<p>Only by providing a valuable experience to all involved (users, advertisers, publishers, intermediaries) with a privacy centric approach can the ecosystem thrive.</p>

<h2>Premise</h2>

<p>The user, within their browser, carries around an “ad profile” - a set of advertising preferences, interest groups and record of personalised ads served - that they may grant outside actors access to read or edit. 
The Ad Profile contains a central collection of optional choices (including user declared interests) and specific choices for other actors. These include:
<ul>
<li>Actor may display personalised adverts to the user</li>
<li>Actor may add the user to interest groups based on their actions on that property</li>
<li>Interest groups administered by the actor may be used to target ads to the user on other properties</li>
<li>Actor may read the user’s repository of personalised ads viewed</li>
<li>The settings for each outside actor are available to change at any point from that actors website and settings across all actors available to change on a central portal (the administrator of the profile).</li>
</ul>
</p>

<h2>Technology Used</h2>
<p>Counterintuitively, the technology on which this proposal currently exists is predominantly cookies.</p>

<p>Through the webkit Storage Access API, third party cookies can be accessed, where certain conditions (including explicit user interaction with a page element from the third party) are met. (Note: This proposal is dependent on webkit defining this as an appropriate use of this API and other browsers adopting the standard).</p>

<p>Choices for each specific actor are stored as first party cookies in that environment and, if granted access, the profile administrator also stores the choices (as a 3rd party in each different environment), which are continually synced (through dynamically created iframes passing postMessages) to ensure the users latest choices are being acted on in each environment. </p>

<p>The added effect of utilising the <a href="" target="_blank">Storage Access API</a> and requiring explicit user consent for the 3rd party administrator is that data gathering/sharing actors will no longer be able to obscure themselves deep in cookie notification lists of partners, that are often “consented” to without clear user knowledge/understanding due to the sheer length of partner lists.</p>

<h2>Working Example</h2>

<p>A very limited working example of this idea exists - you can view screencasts of the process here for <a href="" target="_blank">users</a> and <a href="" target="_blank">advertisers</a>. Please contact greg@adcessible.io for full details on the limitations if you would like to access the pages yourself.</p>

<p>The process shown is as below:</p>
<ul>
<li>User navigates to a new website</li>
<li>Profile administrator code checks for 1st and 3rd party cookies relating to choices for this site</li>
<li>None are found, so choice modal is loaded (containing administrator iframe and clear choice with explanation for users)</li>
<li>User makes choices - iframe stores choices as a 3rd party cookie and postMessages choice to parent, which stores as a 1st party cookie</li>
<ul><li>Each cookie is stored with a timestamp and every subsequent load of a page checked against one another to see if the user has changed their choice either on the site or the administrator portal</li>
<li>If the administrator loses access through the Storage API, an option appears for users to re-connect, otherwise decisions are made based on the first party cookies</li></ul>
<li>Administrator code creates the first part of a bid request (containing contextual data and the user choices) and ad container iframes in defined slots on the page</li>
<li>Bid request Id is passed to each iframe - here the administrator combines the initial bid request details with user interest groups (if permitted by the user) to create full bid request which is passed to advertiser bidders</li>
<li>Winning bid is calculated and ad code returned from advertiser server</li>
<li>Ad is displayed</li>
<ul><li>All details are logged by the administrator for billing and reporting purposes on publisher and advertiser side</li>
<li>Log of ad served is contained in the users profile - if advertisers is granted profile access in their own environment, they can then perform attribution/frequency capping</li></ul>
<li>User accesses administrator portal to check their choices (here they can change any setting, including:</li>
<ul><li>Preventing personalised ads on certain sites</li>
<li>Blocking advertisers they are not interested in/are displaying too frequently</li>
<li>Removing themselves from any interest group</li>
<li>Completely emptying profile</li></ul>
</ul>

<h2>Additional Considerations</h2>
<ul>
<li>The administrator logs only ad auctions that occur and their details for reporting - there is no way of linking this back to any specific user</li>
<li>Interest groups would only become available for use for targeting once the number of bid requests containing that interest group reaches a predefined threshold</li>
<ul><li>This could potentially not apply to exclusions (for example adding a user to an “interest group” after a purchase)</li></ul>
<li>3rd Party served ads would not be allowed to contain tracking (ads disapproved by administrator)</li>
<li>Limits imposed on the number of interest groups existing on one profile</li>
<li>Limits imposed on number (and lifetime) of ad logs existing on one profile</li>
<li>Publisher and advertiser entry to the system would be much more tightly controlled and extensive approval process than most operate currently</li>
<li>Users could opt to copy their profile across browsers/devices by submitting a request to the profile administrator</li>
<ul><li>This would cause the profile to be stored against a temporary Id, which the user could then enter on the second browser/device - the profile would be set in cookies in the new device and immediately removed from the administrator storage</ul></li>
</ul>

<h2>Conclusions</h2>
<p>This is obviously a proposal in it’s very early stages, with a number of key dependencies. However, hopefully it is clear in it’s aims to give the user ultimate choice over their experience, while maintaining where possible the capabilities that publishers and advertisers currently use.</p>

