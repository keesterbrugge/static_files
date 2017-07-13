# Athena database description
---

 > **Question 1: ** Can you confirm the following? We have all the information of all impression that we bid on, either in the notifications table or in the win_calls table. We don't have any information on bid requests that we did not bid on.
 > **Question 2: ** Could you confirm that that the descriptions provided in the table below are correct?
 > **Question 3:** Could you remove the incorrect option if 2 options are given, or both and provide the correct answer?

| Table | Column| Description |
| - | - | - |
| win_calls |  | Info on won auctions received from mopub through use of nURL. **Also** information on auctions that we won, but didn't clear |
| | bid.price-in-cpm | The price that AdGoji currently bids for this campaign in price per mille. **Not** paid price per mille |
| | bid.timestamp | Moment bid was sent to mopub in POSIX time millisec.  |
| | win.price | Price that was paid for this single impression * 1000 **if** it cleared|
| | event.timestamp | Moment mopub used nURL to notify us that we won the bid |
| | bid-request.app.id	 | The id of the application in which ad will be shown |
| pixel_calls |  | Info we have on loading ads through use of pixel |
| |  | |
| | event.timestamp | Moment mopub used nURL to notify us that we won the bid |
| | **OR** | |
| | event.timestamp | (One of the) moment(s) device used pixel to notify us that the ad is loading |
| |  | |
| notifications | | Info on lost auctions, received from mopub through the use of nURL |
| | latency | |
| |  | |
version.tag.campaign-id	bid.price-in-cpm	bid.timestamp	win.price	event.timestamp	bid-request.id	bid-request.app.id	bid-request.device.geo.country	bid-request.device.ext.idfa	year	month	day	hour
| notifications    |   |  info on lost bids  |
| Pipe     | $1    |  234  |

