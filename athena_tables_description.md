# Athena database description
---
First attempt to disambiguate some of the names we use. This list is non exhaustive. Please add to this document if you find ambiguities. 

 > **Question 1:** Can you confirm the following? We have all the information of all impression that we bid on, either in the notifications table or in the win_calls table. We don't have any information on bid requests that we did not bid on.
 
 > **Question 2:** Could you confirm that that the descriptions provided in the table below are correct?
 
 > **Question 3:** Could you remove the incorrect option if 2 options are given, or both and provide the correct answer?

| Table name | Column name| Description |
| - | - | - |
| win_calls |  | Info on won auctions received from mopub through use of nURL. **Also** information on auctions that we won, but didn't clear |
| | bid-request.id | The unique id of the impression generated by mopub. We use it in every message during the ad lifecylce to connect the messages with the original bid request. |
| | bid.price-in-cpm | The price that AdGoji currently bids for this campaign in price per mille. **Not** paid price per mille |
| | bid.timestamp | Moment bid was sent to mopub in POSIX time millisec.  |
| | win.price | Price that was paid for this single impression * 1000 **if** it cleared|
| | event.timestamp | Moment mopub used nURL to notify us that we won the bid |
| | bid-request.app.id	 | The id of the application in which ad will be shown |
| pixel_calls |  | Info we have on loading ads through use of pixel |
| |  | |
| | event.timestamp | Moment mopub used nURL to notify us that we won the bid in POSIX time millisec.|
| | **OR** | |
| | event.timestamp | (One of the) moment(s) device used pixel to notify us that the ad is loading in POSIX time millisec.|
| |  | |
| notifications | | Info on lost auctions, received from mopub through the use of nURL |
| | Latency | The interval between mopub sending us the bid request and receiving our bid response in seconds |
| | id | The bid-request.id to identify which auction was lost |
| | bidfloor | The minimum bid price that would be accepted. This bidfloor is **not** known when the bid is made |
| | timestamp | The moment mopub sends the message using nURL to notify us that we lost the auction in POSIX time millisec.| |
| | seatbid |  |
| | | id : ?| 
| | | price : our bid price| 


