# Pseudocode!

## Landing

Sign in/up
\[Skip, handled\]

## Sign Up

User enters email
Database updates with new User
Navigate to /profile

## Profile

First screen name - prompt/input/next button
No numbers, punctuation not in names (... wait do people? Nvm on this one from future-Integrity, my b)
Update DB (as you go, so if you lose someone in this critical phase, if they reconnect, zero friction to continue, was the idea)
Next, picture - prompt, input, display, next, back
On pic select, upload to service, link -> DB, update display, next button active
Next, location - prompt (for home location,) ... input ... display ... tricky, could ask for location permissions, pin on map, or town/city, or zip ...
US only until GDPR-compliant, encrypt location?
Bio, do this before location, same pattern, prompt, input, next, back, update DB

## Sign In

If name, picture, bio, location set, navigat to / w/ session, otherwise navigate to /profile in right state
If /profile is hit from / w/ session, redir to /

## Runners List

List populated based on proximity
I imagine this to be computationally expensive, so we'll think about mitigation, but from all runners not friended with User, sort based on proxitiy and send along names, bios, picture links, and request/requested status, probably paginated, and we have to think about where to put the list of inbound friend requests.
Tapping request should change the UI and update the datebase. Think about debouncing this, so someone doesn't spam the button and blow up the other user's notifications.
If no unfriended (and unblocked) users, show message

## Friends List

List populated based on proximity, from all runners friended with user, send names, pictures (links), and clicking/tapping will go to friend's profile or if no friends yet, show message, link to Runners List. Marker for planned runs?

## Friend Profile

Populate with name, bio, picture link, proximity, and a list of their planned runs, with datetime, distance, and proximity, sorted by datetime. (Future-Integrity: how about not sending more than the thumbnail down the line until profile is navigated to?)
Tapping should go to run page
Back should go back to Friends (back should be context-dependent from run page!)
Block should ask confirmation, show toast, navigate back to Friends List. (Future-Integrity is thinking very seriously, again, about platform moderation and how best to handle that people are wonderful, individuals can be awful, though.) (The turtle comes to mind.)

## Create/Edit Run

Inputs for datetimes, distance, location (map pin, button for 'Home',) description (optional) and a create/submit changes button, active when required fields filled out or changes made.
When fields are populated, where Back was, have Cancel, which should give a confirmation.
On submit should update the DB and navigate user to Run view, on Runs List tab

## Runs List

List populated by all runs user is part of and all runs friends have planned.
Could be a good use for segmented control.
Send all datetimes, distances, proximities, host names, and host picture links, sorted by datetime. Todo, how to fetch the pictures just once and cache

## Notifications

The logo is a big green stylized 'R', a notification should turn the top left part into a red badge and it should jiggle, and then tapping it pulls up a modal with the stream of notifications.

## Profile Editing

We can have Profile and Account (Log Out button?) in the More or Menu tab, tab 5 at this point in current thinking: 1. Runners List 2. Runs List 3. Create Run 4. Friends List 5. Menu and have it pop up an accordian
It might be smart to limit picture changes (uploads)
Have an Edit button (and then Cancel and Save when editing,) and each field's edit button would become visible or the field would become tappable

## Run Screen

Let's default the back button location to the Runs List, though you could get to it from Create Run and want to go back there, or a friend's profile, todo, make that work.
Datetime, distance, optional description, location, then a list of runners and either a join or leave button, depending. Join should not navigate away, the user should take the join button's place under the host. On leave, it should navigate to Runs List, after a confirm. Include leave in host's notifications?
