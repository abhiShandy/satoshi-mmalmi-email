# Email #1
Date: Sat, 02 May 2009 18:06:58 +0100
From: Satoshi Nakamoto <satoshin@gmx.com>
Subject: Re: Bitcoin
To: Martti Malmi <sirius-m@users.sourceforge.net>
Thanks for starting that topic on ASC, your understanding of bitcoin is 
spot on.  Some of their responses were rather Neanderthal, although I 
guess they're so used to being anti-fiat-money that anything short of 
gold isn't good enough.  They concede that something is flammable, but 
argue that it'll never burn because there'll never be a spark.  Once 
it's backed with cash, that might change, but I'd probably better 
refrain from mentioning that in public anymore until we're closer to 
ready to start.  I think we'll get flooded with newbies and we need to 
get ready first.

What we need most right now is website writing.  My writing is not that 
great, I'm a much better coder.  Maybe you could create the website on 
sourceforge, which is currently blank.  If you can write a FAQ, I can 
give you a compilation of my replies to questions in e-mail and forums 
for facts and details and ideas.

Codewise, there's not much that's easy right now.  One thing that's 
needed is an interface for server side scripting languages such as Java, 
Python, PHP, ASP, etc.  Bitcoin would be running on the web server, and 
server side script could call it to do transactions.  It's Windows, so I 
guess OLE/COM is the interface.

One easy thing that really helps is to run a node that can accept 
incoming connections (forward port 8333 on your firewall) to make sure 
that new users who try it out have someone to connect to.  If they run 
it and get no connections, they'll probably just give up.

Satoshi

# Email #3
Date: Sun, 03 May 2009 23:32:26 +0100
From: Satoshi Nakamoto <satoshin@gmx.com>
Subject: Re: Bitcoin
To: mmalmi@cc.hut.fi

> I have a feature suggestion for the program: a UI tool for creating 
> password protected private keys and saving them into a custom location. 
> Backups of the key will be needed to be safe from losing the control of 
> your coins, and for using the coins on more than one computers. Password 
> protection would be needed to make using your money more difficult for 
> someone who happens to find your key file.

Definitely.  This will be an absolutely essential feature once things 
get going, making it so you can lock your wealth up with strong 
encryption and back it up more securely than any physical safe.  So far 
I've been putting it off in favour of other features because it's not 
crucial yet until bitcoins start to have value.

I plan to work on the escrow feature next, which is needed to make 
actual trades for physical stuff safer and before backing the currency 
with fiat money can begin.


> I'm running a bitcoin node always when my PC is powered on, which means 
> about 24/7. Bitcoin is a great project, and it's really cool to 
> participate!

Thanks!  Right now there are a lot of people on the network who can't 
receive incoming connections, so every node that can really helps. 
Having more helps keep down the "(not accepted)" issue for now until I 
reduce the chances of that happening in v0.1.6.

I guess one answer for the FAQ should be how to set up your firewall to 
forward port 8333 so you can receive incoming connections.  The question 
could be something like "what if I have 0 connections" and that could be 
the answer that it might be because the nodes you can connect with is 
limited if you don't set that up.

Here's a compilation of questions I've answered in forums and e-mail 
that should help you see what questions are frequently asked and some 
answers I've used.  It's not intended to use all or most of the material 
here, just pick and choose.  This is just a dump of everything I've 
answered.

Some issues that we don't have easy answers for are best not to bring 
up.  Casual users seems content to assume that the system works as 
stated (which it does), and getting into the design details just opens a 
can of worms that can't be answered without a deep understanding of the 
system.  The advanced questions I've received have mostly been unique 
per person and best answered individually.



**** QUESTION AND ANSWER DUMP ****

Any questions used for the FAQ should probably be rephrased.

questions:

 > The bottom of the UI shows:
 >
 > Generating        4 connections     4024 blocks     164 transactions
 >
 > I understand "generating"; I assume I am connected to 4 other nodes; and
 > I know I have recorded 164 transactions (including failed generation
 > attempts).  I'm not clear what the "blocks" figure describes.  It's much
 > smaller than the total of all the blocks shown against all my 
transactions.
 >

It's the total number of blocks in the block chain, meaning the 
network's block chain, which everyone has a copy of.  Every Bitcoin node 
displays the same number and it goes up about every 10 minutes whenever 
someone generates a block.  When you haven't had it running for a while, 
once you're connected it spins up rapidly as it downloads what was 
generated while you were gone to catch up.  I'm not sure exactly how to 
describe it (that would fit on the status bar in 1 word, maybe 2 words 
max), any ideas?

The blocks number in the status column next to your transactions is the 
number of blocks that have come after that transaction.  Your 
transaction is essentially "in" that many blocks.

Satoshi




 > My best guess - it
 > is the length of the global chain, and the rapid advance at the start
 > is as the software downloads and verifies the preceding blocks in the
 > chain as being valid.

Right.  I'm trying to think of more clear wording for that, maybe "%d 
network blocks" or "%d block chain".





 > I'm having an unusual run of (block not-accepted) failures, and 
thought I'd let you know in
 > case this was of any significance.

What rate of not-accepted did you see?  I didn't see anything unusual on 
my end.  If you had more than, say, 4 in a row, that would be abnormal 
and probably a loss of network communication.  If it's scattered and 
less than 25%, just random bad luck.  It's normal and harmless to 
randomly get some per cent of not-accepted, and of course randomness can 
sometimes bunch up and look like a pattern.

The idea of an option to View/Hide unaccepted blocks is a good one, as 
well as View/Hide all generated blocks so you can more easily see 
incoming transactions.  Seeing the unaccepted blocks is just annoying 
and frustrating.  Everyone faces the same rate of unaccepted, it's just 
a part of the process.  It would probably be best to default to hide 
unaccepted blocks, so as not to show giving and taking away something 
that never was, and not show new generated blocks at all until they have 
at least one confirmation.  It would only mean finding out you have a 
generated block 15 minutes later than normal, and then you still have 
119 blocks to go before it matures anyway.  This is on the to-do list 
for v0.1.6.

Satoshi

[note: I have some improvements in 0.1.6 to reduce this problem somewhat,
and it'll also improve when the network is larger]







 > For some reason your transfer to me shows up as "From: unknown" even
 > though I added you to my address book.
 >
 > I have a "Generated (not accepted)" line in my transaction list, it
 > seems like an attempt to generate a coin went wrong somehow. Not sure
 > what happened here - presumably my node successfully solved a block
 > but then I went offline before it was sent to the network?

Transactions sent to a bitcoin address will always say "from: unknown". 
  The transaction only tells who it's to.  Sending by bitcoin address 
has a number of problems, but it's so nice having the fallback option to 
be able to send to anyone whether they're online or not.  There are a 
number of ideas to try to improve things later.  For now, if things work 
out like the real world where the vast majority of transactions are with 
merchants, they'll pretty much always make sure to set up to receive by 
IP.  The P2P file sharing networks seem fairly successful at getting a 
large percentage of their users to set up their firewalls to forward a port.

I badly wanted to find some way to include a comment with indirect
transfers, but there just wasn't a way to do it.  Bitcoin uses EC-DSA, which
was essential for making the block chain compact enough to be practical with
today's technology because its signatures are an order of magnitude smaller
than RSA.  But EC-DSA can't encrypt messages like RSA, it can only be used
to verify signatures.

The "Generated (not accepted)" normally happens if two nodes find a 
block at close to the same time, one of them will not be accepted.  It's 
normal and unavoidable.  I plan in v0.1.6 to hide those, since they're 
just confusing and annoying and there's no reason for users to have to 
see them.  While the network is still small like it is now, if you can't 
receive incoming connections you're at more of a disadvantage because 
you can't receive block announcements as directly.




 > ...So far it has two "Generated" messages, however the
 > "Credit" field for those is 0.00 and the balance hasn't changed.  Is
 > this due to the age/maturity requirement for a coin to be valid?

Right, the credit field stays 0.00 until it matures, then it'll be
50.00.  BTW, you can doubleclick on a line for details.





 > ...understand correctly, there is only one (or maybe a few) global
 > chain[s] into which all transactions are hashed. If there is only one
 > chain recording "the story of the economy" so to speak, how does this
 > scale? In an imaginary planet-wide deployment there would be millions
 > of even billions of transactions per hour being hashed into the chain...

 > ...I found the section on incentives hard to follow. In particular, I'm
 > not clear on what triggers the transition from minting new coins as a
 > reason to run a node, to charging transaction fees (isn't the point of
 > BitCoin largely to zero transaction costs anyway?). Presumably there's
 > some human in charge of the system...

 > ...How did you decide on the inflation schedule for v1? Where did 21
 > million coins come from? What denominations are these coins? You
 > mention a way to combine and split value but I'm not clear on how this
 > works. For instance are bitcoins always denominated by an integer or
 > can you have fractional bitcoins?...

 > ...it's rare that I encounter truly
 > revolutionary ideas. The last time I was this excited about a new
 > monetary scheme was when I discovered Ripple. If you have any thoughts
 > on Ripple, I'd also love to hear them.

There is only one global chain.

The existing Visa credit card network processes about 15 million 
Internet purchases per day worldwide.  Bitcoin can already scale much 
larger than that with existing hardware for a fraction of the cost.  It 
never really hits a scale ceiling.  If you're interested, I can go over 
the ways it would cope with extreme size.

By Moore's Law, we can expect hardware speed to be 10 times faster in 5 
years and 100 times faster in 10.  Even if Bitcoin grows at crazy 
adoption rates, I think computer speeds will stay ahead of the number of 
transactions.

I don't anticipate that fees will be needed anytime soon, but if it 
becomes too burdensome to run a node, it is possible to run a node that 
only processes transactions that include a transaction fee.  The owner 
of the node would decide the minimum fee they'll accept.  Right now, 
such a node would get nothing, because nobody includes a fee, but if 
enough nodes did that, then users would get faster acceptance if they 
include a fee, or slower if they don't.  The fee the market would settle 
on should be minimal.  If a node requires a higher fee, that node would 
be passing up all transactions with lower fees.  It could do more volume 
and probably make more money by processing as many paying transactions 
as it can.  The transition is not controlled by some human in charge of 
the system though, just individuals reacting on their own to market forces.

A key aspect of Bitcoin is that the security of the network grows as the 
size of the network and the amount of value that needs to be protected 
grows.  The down side is that it's vulnerable at the beginning when it's 
small, although the value that could be stolen should always be smaller 
than the amount of effort required to steal it.  If someone has other 
motives to prove a point, they'll just be proving a point I already concede.

My choice for the number of coins and distribution schedule was an 
educated guess.  It was a difficult choice, because once the network is 
going it's locked in and we're stuck with it.  I wanted to pick 
something that would make prices similar to existing currencies, but 
without knowing the future, that's very hard.  I ended up picking 
something in the middle.  If Bitcoin remains a small niche, it'll be 
worth less per unit than existing currencies.  If you imagine it being 
used for some fraction of world commerce, then there's only going to be 
21 million coins for the whole world, so it would be worth much more per 
unit.  Values are 64-bit integers with 8 decimal places, so 1 coin is 
represented internally as 100000000.  There's plenty of granularity if 
typical prices become small.  For example, if 0.001 is worth 1 Euro, 
then it might be easier to change where the decimal point is displayed, 
so if you had 1 Bitcoin it's now displayed as 1000, and 0.001 is 
displayed as 1.

Ripple is interesting in that it's the only other system that does 
something with trust besides concentrate it into a central server.

Satoshi






 > If we assume that 0.1% is a good risk rate, then z=5 thus
 > any transaction must wait a bit less than an hour before being
 > solidified in the chain. As micropayments for things like web content
 > or virtual goods are by definition something that requires low
 > overhead, waiting an hour seems like quite a significant hurdle.

For the actual risk, multiply the 0.1% by the probability that the buyer 
is an attacker with a huge network of computers.

For micropayments, you can safely accept the payment immediately.  The 
size of the payment is too small for the effort to steal it. 
Micropayments are almost always for intellectual property, where there's 
no physical loss to the merchant.  Anyone trying to steal a micropayment 
would probably not be a paying customer anyway, and if they want to 
steal intellectual property they can use the file sharing networks.

Currently, businesses accept a certain chargeoff rate.  I believe the 
risk with 1 or even 0 confirming blocks will be much less than the rate 
of chargebacks on verified credit card transactions.

The usual scam against a merchant that doesn't wait for confirming 
blocks would be to send a payment to a merchant, then quickly try to 
propagate a double-spend to the network before the merchant's copy. What 
the merchant can do is broadcast his transaction and then monitor the 
network for any double-spend copies.  The thief would not be able to 
broadcast during the monitoring period or else the merchant's node would 
receive a copy.  The merchant would only have to monitor for a minute or 
two until most of the network nodes have his version and it's too late 
for the thief's version to catch up and reach many nodes.  With just a 
minute or two delay, the chance of getting away without paying could be 
made much too low to scam.  A thief usually needs a high probability of 
getting an item for free to make it worthwhile.  Using a lot of CPU 
power to do the brute force attack discussed in the paper in addition to 
the above scam would not increase the thief's chances very much.

Anything that grants access to something, like something that takes a 
while to download, access to a website, web hosting, a subscription or 
service, can be cancelled a few minutes later if the transaction is 
rejected.


 > How is the required difficulty of each block communicated through the
 > network and agreed upon?

It's not communicated.  The formula is hardcoded in the program and 
every node does the same calculation to know what difficulty is required 
for the next block.  If someone diverged from the formula, their block 
would not be accepted by the majority.





 > Is the code free/open source or just open source?

It's free open source.  It's the MIT license, which just requires some 
disclaimer text be kept with the source code, other than that you can do 
just about anything you want with it.  The source is included in the 
main download.

Satoshi





 > Is there a way to be told of new versions? Does the app auto update
 > itself?  Some kind of mailing list would be excellent.

The list is:
bitcoin-list@lists.sourceforge.net
Subscribe/unsubscribe page:
http://lists.sourceforge.net/mailman/listinfo/bitcoin-list
Archives:
http://sourceforge.net/mailarchive/forum.php?forum_name=bitcoin-list

I'll always announce new versions there.  Automatic update, or at least 
notification of new versions, is definitely on the list.





[this inflation discussion was before the transaction fee mechanism and 
fixed plan of 21 million coins was posted, so it may not be as 
applicable anymore]

 > Since they can be created for free (or at the cost
 > of computer power people have anyway for other reasons),
 > monetizing them means simply giving away money.

You're still thinking as if the difficulty level will be so easy that 
people will be able to generate all the bitcoins they want.

Imagine you have to run your computer 24/7 for a month to generate 1 
cent.  After a year, you could generate 12 cents.  That's not going to 
make it so people can just generate all the bitcoin they want for spending.

The value of bitcoins would be relative to the electricity consumed to 
produce them.  All modern CPUs save power when they're idle.  If you run 
a computational task 24/7, not letting it idle, it uses significantly 
more power, and you'll notice it generates more heat.  The extra wattage 
consumed goes straight to your power bill, and the value of the bitcoins 
you produce would be something less than that.


 > Why would they, when they make money by generating
 > new ones

No, they can't make money that way.  It would cost them more in 
electricity than they'd be selling the bitcoins for.






Historically, people have taken up scarce commodities as money, if 
necessary taking up whatever is at hand, such as shells or stones.  Each 
has a kernel of usefulness that helped bootstrap the process, but the 
monetary value ends up being much more than the functional value alone. 
  Most of the value comes from the value that others place in it.  Gold, 
for instance, is pretty, non-corrosive and easily malleable, but most of 
its value is clearly not from that.  Brass is shiny and similar in 
colour.  The vast majority of gold sits unused in vaults, owned by 
governments that could care less about its prettiness.

Until now, no scarce commodity that can be traded over a communications 
channel without a trusted third party has been available.  If there is a 
desire to take up a form of money that can be traded over the Internet 
without a TTP, then now that is possible.

Satoshi






 > As more capable
 > computer hardware comes out, the natural supply per user
 > doubles at every cycle of Moore's law.

Actually, that is handled.  There's a moving average that compensates 
for the total effort being expended so that the total production is a 
constant.  As computers get more powerful, the difficulty increases to 
compensate.


 > I do not recall any economic history of a commodity subject
 > to natural inflation ever being used as money

There's gold for one.  The supply of gold increases by about 2%-3% per 
year.  Any fiat currency typically averages more inflation than that.



 > Won't there be massive inflation as computers get faster and are able 
to solve the proof-of-work problem faster?

The difficulty is controlled by a moving average that compensates for 
the total effort being expended to keep the total production constant. 
As computers get more powerful, the difficulty increases to compensate.






 > If someone double spends, then the transaction record
 > can be unblinded revealing the identity of the cheater?

Identities are not used, and there's no reliance on recourse.  It's all 
prevention.





 > ...You're saying
 > there's no effort to identify and exclude nodes that don't
 > cooperate? I suspect this will lead to trouble and possible DOS
 > attacks.

There is no reliance on identifying anyone.  As you've said, it's
futile and can be trivially defeated with sock puppets.

The credential that establishes someone as real is the ability to
supply CPU power.






 > But in the absence of identity, there's no downside to them
 > if spends become invalid, if they've already received the
 > goods they double-spent for (access to website, download,
 > whatever). The merchants are left holding the bag with
 > "invalid" coins, unless they wait that magical "few blocks"
 > (and how can they know how many?) before treating the spender
 > as having paid.
 >
 > The consumers won't do this if they spend their coin and it takes
 > an hour to clear before they can do what they spent their coin on.
 > The merchants won't do it if there's no way to charge back a
 > customer when they find the that their coin is invalid because
 > the customer has doublespent.

This is a version 2 problem that I believe can be solved fairly
satisfactorily for most applications.

The race is to spread your transaction on the network first.  Think 6
degrees of freedom -- it spreads exponentially.  It would only take
something like 2 minutes for a transaction to spread widely enough
that a competitor starting late would have little chance of grabbing
very many nodes before the first one is overtaking the whole network.
During those 2 minutes, the merchant's nodes can be watching for a
double-spent transaction.  The double-spender would not be able to
blast his alternate transaction out to the world without the merchant
getting it, so he has to wait before starting.

If the real transaction reaches 90% and the double-spent tx reaches
10%, the double-spender only gets a 10% chance of not paying, and 90%
chance his money gets spent.  For almost any type of goods, that's
not going to be worth it for the scammer.

Information based goods like access to website or downloads are
non-fencible.  Nobody is going to be able to make a living off
stealing access to websites or downloads.  They can go to the file
sharing networks to steal that.  Most instant-access products aren't
going to have a huge incentive to steal.

If a merchant actually has a problem with theft, they can make the
customer wait 2 minutes, or wait for something in e-mail, which many
already do.  If they really want to optimize, and it's a large
download, they could cancel the download in the middle if the
transaction comes back double-spent.  If it's website access,
typically it wouldn't be a big deal to let the customer have access
for 5 minutes and then cut off access if it's rejected.  Many such
sites have a free trial anyway.

Satoshi






[in response to a question about scale]

100,000 block generating nodes is a good ballpark large-scale size
to think about.  Propagating a transaction across the whole network
twice would consume a total of US$ 0.02 of bandwidth at today's
prices.  In practice, many would be burning off excess allocated
bandwidth or unlimited plans with one of the cheaper backbones.
There could be millions of SPV clients.  They only matter in how
many transactions they generate.  If they pay 1 or 2 cents
transaction fees, they pay for themselves.  I've coded it so you
can pay any optional amount of transaction fees you want.  When the
incentive subsidy eventually tapers off, it may be necessary to put
a market-determined transaction fee on your transactions to make
sure nodes process them promptly.

To think about what a really huge transaction load would look like,
I look at the existing credit card network.  I found some more
estimates about how many transactions are online purchases.  It's
about 15 million tx per day for the entire e-commerce load of the
Internet worldwide.  At 1KB per transaction, that would be 15GB of
bandwidth for each block generating node per day, or about two DVD
movies worth.  Seems do-able even with today's technology.

Important to remember, even if Bitcoin caught on at dot-com rates
of growth, it would still take years to become any substantial
fraction of all transactions.  I believe hardware has already
recently become strong enough to handle large scale, but if there's
any doubt about that, bandwidth speeds, prices, disk space and
computing power will be much greater by the time it's needed.

Satoshi






 > One other question I had... What prevents the single node with the most
 > CPU power from generating and retaining the majority of the BitCoins?
 > If every node is working independently of all others, if one is
 > significantly more powerful than the others, isn't it probable that this
 > node will reach the proper conclusion before other nodes? An
 > underpowered node may get lucky once in a while, but if they are at a
 > significant horsepower advantage I would expect the majority of BitCoins
 > to be generated by the most powerful node.

It's not like a race where if one car is twice as fast, it'll always
win.  It's an SHA-256 that takes less than a microsecond, and each guess
has an independent chance of success.  Each computer's chance of finding
a hash collision is linearly proportional to it's CPU power.  A computer
that's half as fast would get half as many coins.






[question about what to backup]

The files are in "%appdata%\Bitcoin", that's the directory to
backup.

%appdata% is per-user access privilege.  Most new programs like
Firefox store their settings files there, despite the headwind of
Microsoft changing the directory name with every Windows release
and being full of spaces and so long it runs off the screen.





[question about what to backup]

The directory is "%appdata%\Bitcoin"
It has spaces in it so you need the quotes
cd "%appdata%\bitcoin"

On XP it would typically be:
C:\Documents and Settings\[username]\Application Data\Bitcoin

Backup that whole directory.  All data files are in that
directory.  There are no temporary files.





[question about what to backup]

The crucial file to backup is wallet.dat.  If bitcoin is running
then you have to backup the whole %appdata%\bitcoin directory
including the database subdirectory, but even if it's not running
it certainly feels safer to always backup the whole directory.

The database unfortunately names its files "log.0000000001".  To
the rest of the world, "log" means delete-at-will, but to database
people it means delete-and-lose-everything-in-your-other-files.  I
tried to put them out of harm's way by putting them in the
database subdirectory.  Later I'll write code to flush the logs
after every wallet change so wallet.dat will be standalone safe
almost all the time.







 > > You know, I think there were a lot more people interested in the 90's,
 > > but after more than a decade of failed Trusted Third Party based 
systems
 > > (Digicash, etc), they see it as a lost cause. I hope they can make the
 > > distinction that this is the first time I know of that we're trying a
 > > non-trust-based system.
 >
 > Yea, that was the primary feature that caught my eye. The real trick
 > will be to get people to actually value the Bitcoins so that they become
 > currency.

Hal sort of alluded to the possibility that it could be seen as a
long-odds investment.  I would be surprised if 10 years from now
we're not using electronic currency in some way, now that we know
a way to do it that won't inevitably get dumbed down when the
trusted third party gets cold feet.

Once it gets bootstrapped, there are so many applications if you
could effortlessly pay a few cents to a website as easily as dropping
coins in a vending machine.

[this next bit turned out to be very controversial.  there is extreme
prejudice against spam solutions, especially proof-of-work.]

It can already be used for pay-to-send e-mail.  The send dialog is
resizeable and you can enter as long of a message as you like.
It's sent directly when it connects.  The recipient doubleclicks
on the transaction to see the full message.  If someone famous is
getting more e-mail than they can read, but would still like to
have a way for fans to contact them, they could set up Bitcoin and
give out the IP address on their website.  "Send X bitcoins to my
priority hotline at this IP and I'll read the message personally."

Subscription sites that need some extra proof-of-work for their
free trial so it doesn't cannibalize subscriptions could charge
bitcoins for the trial.




[again, I don't know why I'm including this, as it's best to stay
away from claims about spam.  people automatically react violently
against any suggestion of a spam solution.]

 > Spammer botnets could burn through pay-per-send email filters
 > trivially (as usual, the costs would fall on people other than the
 > botnet herders & spammers).

Then you could earn a nice profit by setting up pay-per-send
e-mail addresses and collecting all the spam money.  You could
sell it back to spammers who don't have big enough botnets to
generate their own, helping bootstrap the currency's value.  As
more people catch on, they'll set up more and more phony addresses
to harvest it.  By the time the book "How I got rich exploiting
spammers and you can too" is coming out, there'll be too many fake
addresses and the spammers will have to give up.




 > > * Spammer botnets could burn through pay-per-send email filters
 > >   trivially
 > If POW tokens do become useful, and especially if they become money,
 > machines will no longer sit idle. Users will expect their computers to
 > be earning them money (assuming the reward is greater than the cost to
 > operate). A computer whose earnings are being stolen by a botnet will
 > be more noticeable to its owner than is the case today, hence we might
 > expect that in that world, users will work harder to maintain their
 > computers and clean them of botnet infestations.

One more factor that would mitigate spam if POW tokens have value:
there would be a profit motive for people to set up massive
quantities of fake e-mail accounts to harvest POW tokens from
spam.  They'd essentially be reverse-spamming the spammers with
automated mailboxes that collect their POW and don't read the
message.  The ratio of fake mailboxes to real people could become
too high for spam to be cost effective.

The process has the potential to establish the POW token's value
in the first place, since spammers that don't have a botnet could
buy tokens from harvesters.  While the buying back would
temporarily let more spam through, it would only hasten the
self-defeating cycle leading to too many harvesters exploiting the
spammers.

Interestingly, one of the e-gold systems already has a form of
spam called "dusting".  Spammers send a tiny amount of gold dust
in order to put a spam message in the transaction's comment field.
  If the system let users configure the minimum payment they're
willing to receive, or at least the minimum that can have a
message with it, users could set how much they're willing to get
paid to receive spam.





 > The last thing we need is to deploy a system designed to burn all
 > available cycles, consuming electricity and generating carbon dioxide,
 > all over the Internet, in order to produce small amounts of bitbux to
 > get emails or spams through.
 >
 > Can't we just convert actual money in a bank account into bitbux --
 > cheaply and without a carbon tax?  Please?

Ironic if we end up having to choose between economic liberty and
conservation.

Unfortunately, proof of work is the only solution I've found to
make p2p e-cash work without a trusted third party.  Even if I
wasn't using it secondarily as a way to allocate the initial
distribution of currency, PoW is fundamental to coordinating the
network and preventing double-spending.

If it did grow to consume significant energy, I think it would
still be less wasteful than the labour and resource intensive
conventional banking activity it would replace.  The cost would be
an order of magnitude less than the billions in banking fees that
pay for all those brick and mortar buildings, skyscrapers and junk
mail credit card offers.

Satoshi






 > BTW I don't remember if we talked about this, but the other day some
 > people were mentioning secure timestamping. You want to be able to
 > prove that a certain document existed at a certain time in the past.
 > Seems to me that bitcoin's stack of blocks would be perfect for this.

Indeed, Bitcoin is a distributed secure timestamp server for
transactions.  A few lines of code could create a transaction with
an extra hash in it of anything that needs to be timestamped.
I should add a command to timestamp a file that way.






 From a thread on p2presearch which starts with my rant about trust 
being the root weakness of all conventional financial systems.
http://listcultures.org/pipermail/p2presearch_listcultures.org/2009-February/thread.html

I've developed a new open source P2P e-cash system called Bitcoin.  It's
completely decentralized, with no central server or trusted parties,
because everything is based on crypto proof instead of trust.  Give it a
try, or take a look at the screenshots and design paper:

Download Bitcoin v0.1 at http://www.bitcoin.org

The root problem with conventional currency is all the trust that's
required to make it work.  The central bank must be trusted not to
debase the currency, but the history of fiat currencies is full of
breaches of that trust.  Banks must be trusted to hold our money and
transfer it electronically, but they lend it out in waves of credit
bubbles with barely a fraction in reserve.  We have to trust them with
our privacy, trust them not to let identity thieves drain our accounts.
Their massive overhead costs make micropayments impossible.

A generation ago, multi-user time-sharing computer systems had a similar
problem.  Before strong encryption, users had to rely on password
protection to secure their files, placing trust in the system
administrator to keep their information private.  Privacy could always
be overridden by the admin based on his judgment call weighing the
principle of privacy against other concerns, or at the behest of his
superiors.  Then strong encryption became available to the masses, and
trust was no longer required.  Data could be secured in a way that was
physically impossible for others to access, no matter for what reason,
no matter how good the excuse, no matter what.

It's time we had the same thing for money.  With e-currency based on
cryptographic proof, without the need to trust a third party middleman,
money can be secure and transactions effortless.

One of the fundamental building blocks for such a system is digital
signatures.  A digital coin contains the public key of its owner.  To
transfer it, the owner signs the coin together with the public key of
the next owner.  Anyone can check the signatures to verify the chain of
ownership.  It works well to secure ownership, but leaves one big
problem unsolved: double-spending.  Any owner could try to re-spend an
already spent coin by signing it again to another owner.  The usual
solution is for a trusted company with a central database to check for
double-spending, but that just gets back to the trust model.  In its
central position, the company can override the users, and the fees
needed to support the company make micropayments impractical.

Bitcoin's solution is to use a peer-to-peer network to check for
double-spending.  In a nutshell, the network works like a distributed
timestamp server, stamping the first transaction to spend a coin.  It
takes advantage of the nature of information being easy to spread but
hard to stifle.  For details on how it works, see the design paper at
http://www.bitcoin.org/bitcoin.pdf

The result is a distributed system with no single point of failure.
Users hold the crypto keys to their own money and transact directly with
each other, with the help of the P2P network to check for double-spending.

Satoshi Nakamoto
http://www.bitcoin.org





Martien van Steenbergen Martien at AardRock.COM
Thu Feb 12 08:40:53 CET 2009

Very interesting. Is this akin to David Chaum's anonymous digital
money? His concept makes sure money is anonymous unless it is
compromised, i.e. the same money spent more than once. As soon as it's
compromised, the ‘counterfeiter’ is immediately publicly exposed.

Also, in bitcoin, is there a limited supply of money (that must be
managed)? Or is money created exaclty at the moment of transaction?

Succes en plezier,

Martien.





Martien van Steenbergen wrote:
 > Very interesting. Is this akin to David Chaum's anonymous digital money?
 > His concept makes sure money is anonymous unless it is compromised, i.e.
 > the same money spent more than once. As soon as it's compromised, the
 > ‘counterfeiter’ is immediately publicly exposed.

It's similar in that it uses digital signatures for coins, but different
in the approach to privacy and preventing double-spending.  The
recipient of a Bitcoin payment is able to check whether it is the first
spend or not, and second-spends are not accepted.  There isn't an
off-line mode where double-spenders are caught and shamed after the
fact, because that would require participants to have identities.

To protect privacy, key pairs are used only once, with a new one for
every transaction.  The owner of a coin is just whoever has its private key.

Of course, the biggest difference is the lack of a central server.  That
was the Achilles heel of Chaumian systems; when the central company shut
down, so did the currency.

 > Also, in bitcoin, is there a limited supply of money (that must be
 > managed)? Or is money created exaclty at the moment of transaction?

There is a limited supply of money.  Circulation will be 21,000,000
coins.  Transactions only transfer ownership.

Thank you for your questions,

Satoshi





Martien van Steenbergen wrote:
 > Reminds me of:
 >
 >     * AardRock » Wizard Rabbit Treasurer
 >       <http://wiki.aardrock.com/Wizard_Rabbit_Treasurer>; and
 >     * AardRock » Pekunio <http://wiki.aardrock.com/Pekunio>

Indeed, it is much like Pekunio in the concept of spraying redundant
copies of every transaction to a number of peers on the network, but the
implementation is not a reputation network like Wizard Rabbit Treasurer.
   In fact, Bitcoin does not use reputation at all.  It sees the network
as just a big crowd and doesn't much care who it talks to or who tells
it something, as long as at least one of them relays the information
being broadcast around the network.  It doesn't care because there's no
way to lie to it.  Either you tell it crypto proof of something, or it
ignores you.

 > Are you familiar with Ripple?

As trust systems go, Ripple is unique in spreading trust around rather
than concentrating it.

[I've been asked at least 4 other times "have you heard of Ripple?"]




Michel Bauwens wrote:
 > how operational is your project? how soon do you think people will be
 > able to use it in real life?

It's fully operational and the network is growing.  If you try the
software, e-mail me your Bitcoin address and I'll send you a few coins.

We just need to spread the word and keep getting more people interested.





Here's a link to the original introduction of the paper on the 
Cryptography mailing list.  (Inflation issues were superseded by changes 
I made later to support transaction fees and the limited circulation 
plan.  This link is a moving target, this archive page is just a certain 
number of days back and the discussion will keep scrolling off to the 
next page.)
http://www.mail-archive.com/cryptography@metzdowd.com/mail3.html

A little follow up when the software was released.
http://www.mail-archive.com/cryptography@metzdowd.com/mail2.html

My description of how Bitcoin solves the Byzantine Generals' problem:
http://www.bitcoin.org/byzantine.html

# Email #5
Date: Mon, 04 May 2009 16:51:00 +0100
From: Satoshi Nakamoto <satoshin@gmx.com>
Subject: Re: Bitcoin
To: mmalmi@cc.hut.fi

Your FAQ looks good so far!

You can create whatever you want on bitcoin.sourceforge.net.  Something 
to get new users up to speed on what Bitcoin is and how to use it and 
why, and clean and professional looking would help make it look well 
established.  The site at bitcoin.org was designed in a more 
professorial style when I was presenting the design paper on the 
Cryptography list, but we're moving on from that phase.

You should probably change the part about "distribute them under several 
keys".  When the paper says that it means for the software to do it, and 
it does.  For privacy reasons, the software already uses a different key 
for every transaction, so every piece of money in your wallet is already 
on a different key.  The exception is when using a bitcoin address, 
everything sent to the same bitcoin address is on the same key, which is 
a privacy risk if you're trying to be anonymous.  The EC-DSA key size is 
very strong (sized for the future), we don't practically have to worry 
about a key getting broken, but if we did there's the advantage that 
someone expending the massive computing resources would only break one 
single transaction's worth of money, not someone's whole account.  The 
details about how to backup your wallet files is in the Q&A dump and 
also it's explained in readme.txt and definitely belongs in the FAQ.

Oh I see, you're trying to address byronm's concern on freedomainradio. 
  I see what you mean about the password feature being useful to address 
that argument.  Banks let anyone who has your name and account number 
drain your account, and you're not going to get it back from Nigeria. 
If someone installs a keylogger on your computer, they could just as 
easily get your bank password and transfer money out of your account. 
Once we password encrypt the wallet, we'll be able to make a clearer 
case that we're much more secure than banks.  We use strong encryption, 
while banks still let anyone who has your account info draw money from 
your account.

# Email #8
Date: Tue, 05 May 2009 18:39:44 +0100
From: Satoshi Nakamoto <satoshin@gmx.com>
Subject: Re: Bitcoin
To: mmalmi@cc.hut.fi

> ...the difference being, though, that not everyone can easily
> transfer their regular bank money into an uncontrollable location. In
> bitcoin anyone can do it.

That's true.

We shouldn't try to use security against identity theft as a selling 
point, since it leads into these counter arguments.  The current banking 
model is already tested and the actual loss percentage is known.  Even 
if ours is probably better, it's an unknown, so people can imagine 
anything.  The uncertainty about what the average loss percentage will 
be is greater than the likely loss percentage itself.

# Email #15
Date: Sun, 24 May 2009 23:03:38 +0100
From: Satoshi Nakamoto <satoshin@gmx.com>
Subject: Re: Bitcoin
To: mmalmi@cc.hut.fi
You're right, that was it.  I went in and granted us access using the 
alternate account.

I like your idea of at least moving the FAQ into the wiki.  I've seen 
other projects that use the wiki for the FAQ or even the whole site.  If 
you can figure out how to make it so regular users can edit things, then 
anyone who wants to can help.

# Email #19
Date: Thu, 11 Jun 2009 22:24:25 +0100
From: Satoshi Nakamoto <satoshin@gmx.com>
Subject: Re: Bitcoin
To: mmalmi@cc.hut.fi
The site layout is looking nicer.  More impressive looking.

There are a lot of things you can say on the sourceforge site that I 
can't say on my own site.  Even so, I'm uncomfortable with explicitly 
saying "consider it an investment".  That's a dangerous thing to say and 
you should delete that bullet point.  It's OK if they come to that 
conclusion on their own, but we can't pitch it as that.

A few details: the FAQ says "see section 2.3", but the sections aren't 
numbered.  Also, could you delete the last sentence on the FAQ "They are 
planned to be hidden in v0.1.6, since they're just confusing and 
annoying and there's no reason for users to have to see them." -- that's 
not really something I meant to say publicly.

The links to sites to help set up 8333 port forwarding is great. 
favicon is a nice touch.

Someone came up with the word "cryptocurrency"... maybe it's a word we 
should use when describing Bitcoin, do you like it?

Sourceforge is so slow right now I can't even get the login page to 
load.  Maybe due to the site reorg they just did.  I'll keep trying and 
try to get you that logo stats thing.

# Email #21
Date: Sun, 14 Jun 2009 21:30:58 +0100
From: Satoshi Nakamoto <satoshin@gmx.com>
Subject: Re: Bitcoin
To: mmalmi@cc.hut.fi

mmalmi@cc.hut.fi wrote:
> I made the changes. You could also register to the site or use the admin 
> account to make necessary changes yourself, since the pages are located 
> in the wiki.

Thanks, I've been really busy lately.

I registered username "satoshi".  Since there's no SSL login, I want to 
mainly use that account with sub-admin powers and use the admin account 
as little as possible.  I created a "Moderators" group to give my 
satoshi account as much editing control as possible without the ability 
to overthrow everything.

There's something weird with the download bar on the right covering 
things up, like on the new account registration it covers up the entry 
fields unless you make the browser really wide, and the homepage it 
covers up the screenshots.  (with Firefox)

# Email #24
Date: Tue, 21 Jul 2009 04:14:43 +0100
From: Satoshi Nakamoto <satoshin@gmx.com>
Subject: Re: Bitcoin
To: mmalmi@cc.hut.fi
I know this sounds really retarded, but I still haven't been able to get 
the sourceforge login page to load, so I haven't been able to read it 
either.  https://sourceforge.net/account/login.php

Hal isn't currently actively involved.  He helped me a lot defending the 
design on the Cryptography list, and with initial testing when it was 
first released.  He carried this torch years ago with his Reusable Proof 
Of Work (RPOW).

I'm not going to be much help right now either, pretty busy with work, 
and need a break from it after 18 months development.

It would help if there was something for people to use it for.  We need 
an application to bootstrap it.  Any ideas?

There are donors I can tap if we come up with something that needs 
funding, but they want to be anonymous, which makes it hard to actually 
do anything with it.

# Email #28
Date: Mon, 24 Aug 2009 23:00:35 +0100
From: Satoshi Nakamoto <satoshin@gmx.com>
Subject: Re: Bitcoin
To: mmalmi@cc.hut.fi
That's a good point that since you know how many coins exist and how 
fast new ones are created, you could set a support price based on the 
amount of legacy currency you have and be sure you'll have enough to 
meet all demands.  I had imagined an auction, but it would be far 
simpler and more confidence inspiring to back it at a specific exchange 
rate.

Offering currency to back bitcoins would attract freebie seekers, with 
the benefit of attracting a lot of publicity.  At first it would mostly 
be seen as a way to get free money for your computer's idle time.  Maybe 
pitched like help support the future of e-commerce and get a little 
money for your computer's spare cycles.  As people cash in and actually 
get paid, word would spread exponentially.

It might help to keep the minimum transaction size above an amount which 
a typical user would be able to accumulate with one computer, so that 
users have to trade with each other for someone to collect enough to 
cash in.  Aggregators would set up shop to buy bitcoins in smaller 
increments, which would add confidence in users ability to sell bitcoins 
if there are more available buyers than just you.

People would obviously be sceptical at first that the backing will hold 
up against an onslaught of people trying to get the free money, but as 
the competition raises the proof-of-work difficulty, it should become 
clear that bitcoins stay scarce.  People will see that they can't just 
get all the bitcoins they want.  It would establish a minimum value 
under bitcoins enabling them to be used for other purposes if, 
hopefully, other purposes are waiting for something to use.

# Email #29
Date: Mon, 24 Aug 2009 23:04:25 +0100
From: Satoshi Nakamoto <satoshin@gmx.com>
Subject: Re: Bitcoin
To: mmalmi@cc.hut.fi
Glad that worked, it's a pain that the dependencies are so big and hard 
to build.  Some of them give little attention to the Windows build. 
Next time I update to the latest versions, maybe I'll lay everything out 
in one directory tree and bundle the whole thing up into a giant archive.

I'm not sure they had wxPack before.  I'm glad they got that so everyone 
doesn't have to build wxWidgets themselves.  OpenSSL is the harder one 
to build.

I reduced the EXE size by running strip.exe on it to take out the debug 
symbols.  That's with mingw.  That's the better compiler, I only used VC 
  for debugging.

# several emails later

# Email #249
Date: Mon, 13 Dec 2010 16:11:53 +0000
From: Satoshi Nakamoto <satoshin@gmx.com>
Subject: [bitcoin-list] Bitcoin 0.3.19 is released
To: bitcoin-list@lists.sourceforge.net
This is a minor release to add some DoS protection.

Changes:
- Added some DoS limits, though it's still far from DoS resistant.
- Removed "safe mode" alerts.

http://www.bitcoin.org/smf/index.php?topic=2228.0

Download:
http://sourceforge.net/projects/bitcoin/files/Bitcoin/bitcoin-0.3.19/

# Email #251
Date: Mon, 20 Dec 2010 18:10:06 +0000
From: Satoshi Nakamoto <satoshin@gmx.com>
Subject: Re: Bitcoin.org backups
To: Gavin Andresen <gavinandresen@gmail.com>
Cc: mmalmi@cc.hut.fi
Gavin Andresen wrote:
> On Mon, Dec 20, 2010 at 10:55 AM,  <mmalmi@cc.hut.fi> wrote:
>> ShadowOfHarbringer described a way of mirroring the bitcoin.org website and
>> forum here:
>> http://www.bitcoin.org/smf/index.php?topic=2026.msg30043#msg30043
>>
>> Should we go by it and trust the database along with its password hashes to
>> some reliable community members who have servers?
> 
> That seems like asking for trouble, and I think it would violate the
> implicit trust of everybody who's registered for the forums.

I agree, don't let the database out of your hands.  There's private PM 
in there, e-mail addresses, passwords.

BTW, password hashes = passwords.  It's easy to break the hash of short 
passwords people use on forums.
6 chars = 3 difficulty
7 chars = 410 difficulty
8 chars = 25418 difficulty


>> Another option is to
>> > encrypt the backups with pgp and store them in multiple places.
> 
> That seems wiser.  Daily backups copied ... somewhere ... seems like
> the right thing to do.  If they're reasonably small (less than a
> gigabyte), I'd be happy to pay for Amazon S3 storage/bandwidth for
> them.

+1

Even with encryption, a trusted storage place is better.

# Email #254
Date: Thu, 06 Jan 2011 18:31:26 +0000
From: Satoshi Nakamoto <satoshin@gmx.com>
Subject: Re: Writing about BitCoin
To: Gavin Andresen <gavinandresen@gmail.com>
Cc: Martti Malmi <mmalmi@cc.hut.fi>
Gavin Andresen wrote:
> I'd be happy to talk to Rainey; 

Great

> Satoshi, I assume you don't want to
> deal with press/PR/interviews ?

True

> We could decline to talk to the press-- Satoshi, I know you've
> expressed concern about bitcoin growing too big too fast, and being
> unable to keep up with traffic/attacks/feature requests/etc.  But I
> don't think ignoring the press will make them go away; they'll just
> talk to somebody else.  I think it is better to give a realistic
> impression of bitcoin (it is cutting-edge, beta software that is still
> being developed, it is not poised to replace PayPal or the Euro
> anytime soon, etc) rather than let somebody over-enthusiastic become
> "the unofficial bitcoin spokesperson."

You're the best person to do it.

EFF is really important.  We want to have a good relationship with them. 
  We're the type of project they like; they've helped the TOR project 
and done a lot to protect P2P file sharing.

# Email #256
Date: Tue, 25 Jan 2011 18:34:03 +0000
From: Satoshi Nakamoto <satoshin@gmx.com>
Subject: Re: Fwd: Bitcoin question
To: mmalmi@cc.hut.fi
The paper was published in 2008.

Someone needs to correct Wikipedia; it incorrectly says the paper was 
published in 2009.  The paper was released earlier than the software.
