# IOT POC Upgrades

- Author(s): @Buckshot22
- Start Date: 2023-08-28
- Category: <!-- economic, technical, meta -->
- Original HIP PR: <!-- leave this empty; maintainer will fill in ID of this pull request -->
- Tracking Issue: <!-- leave this empty; maintainer will create a discussion issue -->
- Vote Requirements: VeIOT

## Summary

This HIP proposes to- 
1. Establish a scoring metric based on a number of criteria to provide a coverage score for IOT Hotspots.
2. Set a hard limit per Res8 Hex (or equivalent K-Ring), Hotspots within that Hex will be ranked based on the 'Coverage Score'. Those below the cut off will not be rewarded. **Needs explanation of K-Rings if we go that route
3. Increase witnesses per beacon to 25. 

<!-- Read the content requests in all sections before starting to write any section. -->

## Motivation

The Helium network has had an incredible growth in numbers of hotspots through it's early years, however one issue is that the bulk of these units are clustered in city centers, providing little utility, while large areas of the world remain with insufficient coverage.

For data usage to grow, we need to encourage better placement of Hotspots and discourage the clustering of large numbers in city centers. 
HIP 17 attempted to achieve this, however is overly complex and poorly understood by many and has failed to have any significant effect on this issue.

The metrics used to measure the 'Coverage Score' effectively create an 'SLA' which will help to provide a level of assurance to companies, organisations and individuals wanting to utilise the network for sensor usage.

## Stakeholders

- Hotspot hosts
- Investors
- Network users.

## Detailed Explanation

**Coverage Score**

The Coverage Score will be determined by the following metrics in weighted order ** Need to provide formula and weightings

- Number of unique witnesses within 20km over the past 14 days *500
- Measure of uptime over the previous 14 days (number of beacons over 14 days? or something better) *100
- Average response time over the previous 14 days (500 - average response time in ms) *50
- Length of time that the unit has remained in location (time since last assertion in days) *10
- HNT/IOT staking (HNT staked *2 + IOT staked *1)

**Res8 Limit**

Proposal is to set the initial Res8 limit at 2 and review on a regular schedule. 
If there are more than 2 Hotspots in any Res8, only the 2 with the highest Coverage Score will be rewarded for POC activities.
This number can be adjusted if required

**Witness limit per beacon**

Witnesses per beacon were reduced due to load on the Helium blockchain, with the move to Solana, this is no longer required. By reducing over density it becomes viable to increase this limit. This also helps to aleviate some of the concerns by hotspots which are 'bridging' areas of density and less dense areas which were negatively affected by HIP 83. By providing better incentives to those bridging units we expect network growth on the outskirts of city areas will be encouraged.

This HIP proposes to increase the witnesses per beacon to 25. This number can be further increased in the future after evaluation.


## Drawbacks

The primary arguments which have been made against these ideas to date are -
1. Pushback from those negatively impacted.
Our conention is that Proof Of Coverage rewards need to be aligned with useful coverage. Providing lower level coverage to an area as small as a Res8 that already has many better performing hotspots does not add any value to the network and therefore should not be rewarded.
Those hosts will have the option to move, sell their equipment or turn off. Any of those options will achieve the outcome sort in this HIP.
3. People will lie about their location.
This happens already, while this HIP may provide some added incentive to do so, the effects will be limited. Those who are in a saturated Res8 which happen to be very close to a vacant spot may move their location a short distance and evade the limit.
Our contention is that such a short move is not significant, the unit would be close enough to actually be providing coverage to that area so we do not see any issue with this.
In the cases that this HIP is targeting, where you have a city area filled with Res8's with double digit coverage throughout, a host would need to move miles away from their true location to achieve this effect. These units would be caught out by the denylist algorithms. 


## Rationale and Alternatives

The HIP authors believe that by introducing these changes, it will force improvements to the spread of coverage while maintaining sufficiant redundancy for the network. By improving coverage and providing an SLA score it will improve dependability in the eyes of potential data customers.

It is expected that there will be pushback from those who stand to be caught out by this HIP due to providing superfluous coverage which is not adding value to the network.
It is the authors belief that Proof Of Coverage rewards should only be provided to those providing valuable coverage. Providing lower level coverage to an area as small as a Res8 that already has better performing hotspots does not add any value to the network.
By not rewarding the superfluous hotspots the incentive is increased to deploy hotspots to underserved areas ** Needs current data, preferably the number of IOT per month currenly awarded to hotspots that are in Res8's that have more than 2 and are not in the top 2.

Hotspot Operators who are negatively affected by this change are likely to-
1. Move their hotspot - More likely to happen if it is a hosted unit, the preferred behaviour is that units are moved to a less saturated area.
2. Sell their hotspot - Users who have a hotspot at home and with no other hosting options would be likely to sell their unit. This has the same positive effect as moving.
3. Improve their Score - Some users may invest the time to improve their setup and thereby displace on of the top 4. This provides obvious benefits to the network.
4. Turn their hotspot off/repurpose it - While not as preferable to item 1 or 2, it does help to achieve the same result in that hosts who are not providing valuable coverage turning off will increase the incentives for those who choose to deploy in less saturated areas.
5. Just ignore it - Similar to 4. These users are not earning rewards, those rewards are now increasing the pool available and providing extra incentives for those deploying in less saturated areas.

## Unresolved Questions

- What parts of the design do you expect to resolve through the HIP process before this gets merged?
- What parts of the design do you expect to resolve through the implementation of this feature?
- What related issues do you consider out of scope for this HIP that could be addressed in the
  future independently of the solution that comes out of this HIP?
- Are there dependencies, milestones, or dates that need to be met for this HIP to succeed?

## Deployment Impact

Describe how this design will be deployed and any potential impact it may have on current users of
this project.

- How will current users be impacted?
- How will existing documentation/knowledge base need to be supported? Any content to change at
  <http://docs.helium.com>?
- Is this backwards compatible? Can this HIP be undone?
  - If not, what is the procedure to migrate?

## Success Metrics

What metrics can be used to measure the success of this design? Are any new ETL reports needed to
measure the success?

- What should we measure to prove a performance increase?
- What should we measure to prove an improvement in stability?
- What should we measure to prove a reduction in complexity?
- What should we measure to prove an acceptance of this by its users?
