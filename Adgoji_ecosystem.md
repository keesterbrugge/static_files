
**Goal:** Try to make explicit that domain knowledge which you don't know even know you know

---

> - How and when does metamarkets get their data from mopub?
> - which data gets stored by the db and which doesn't?
> - which time stamps get stored?
> - duplicates of both win notifications and pixel messages?
> - what kind of message and data do we get from mopub if we lose bid?
> - What more data do we collect by at least putting out a very unrealistically low bid. 
> - When do we receive the hourly information about auctions cleared from metamarket?

#### AdGoji 

**TODO: Conform the diagram below to the terms used above**
```sequence 
Title: message sequence and data

user->mopub: HTTP get request {idfa, ..}
mopub-> adgoji: bid request {bid-id, timestamp, idfa, ..}
note over adgoji: Determine bid price
adgoji->mopub: Bid response {bid-id, bid-price, ..} 

adgoji->db_athena: store bid won information {bid-id, timestamp, idfa ..}

mopub->user: ad markup {ad,imptracker, nUrl, pixel,..}

user->adgoji: pixel  notification triggered in loading/caching state {..}

mopub->adgoji: nUrl s2s notification. Auction won, not necessarily cleared {idfa, bid-price, bid-time,..}

adgoji->db_athena: store bid won information {bid-id, timestamp, idfa ..}

mopub->user: ad markup {ad,imptracker, nUrl, pixel,..}

user->adgoji: pixel  notification triggered in loading/caching state {..}

note over user: ad is shown in app
user->adgoji: Win notification triggered by imprtracker being fired{..}

note over user,metamarkets:a day later




metamarkets->adgoji: Per day, per campaigns statistics

note over user,metamarkets: a month later


mopub->adgoji: Bill

```



> **Please help me make the diagram above more complete!**
> Feedback is very welcome, especially for clarification of the used terms,  additional sent messages, additional fields of messages, additional message senders/receivers when and which db's store which messages, etc.