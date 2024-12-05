Each ad unit in the Original API is a subclass of the `AdUnit` class, which provides the following properties and methods for additional configuration.

### Auto Refresh

#### setAutoRefreshPeriodMillis
{:.no_toc}

If set on a given Prebid Mobile ad unit, the `fetchDemand` function will be called every `periodMillis` until `stopAutoRefresh` is called. Each call to `fetchDemand` will invoke the `onComplete` function. This refresh only pertains to Prebid Mobile and not to any ad server refresh processes. It is suggested that the adServers refresh be turned off.

**Parameters**

- `periodMillis`: Integer defining the refresh time in milliseconds.

#### startAutoRefresh
{:.no_toc}

Starts the auto-refresh behavior for a given Prebid Mobile ad unit.

#### stopAutoRefresh
{:.no_toc}

Halts the auto-refresh behavior for a given Prebid Mobile ad unit. If no auto-refresh behavior has been set, `stopAutoRefresh` will be ignored.

### GPID

(requires SDK v2.1.6)

The Global Placement ID (GPID) is a key that uniquely identifies a specific instance of an adunit. Some bidders require this value. An important scenario is "infinite scroll" -- if your app creates instances
of an adunit dynamically as the user scrolls through content, the the GPID must be different for each by appending some kind of sequence or ID. e.g. "/newsfeed#7"

Using the following method, you can set the impression-level [GPID](https://docs.prebid.org/features/pbAdSlot.html#the-gpid) value to the bid request:

``` kotlin
adUnit?.gpid = "/36117602/hnp-sfgate.com/Homepage/AP300"
```

### Ad Position

The `adPosition` property allows developers to specify the position of the ad within the publisher's content. This property maps to the `pos` field in the OpenRTB specification under the `imp[].banner` or `imp[].video` objects, depending on the ad format. The possible values for this field could be found in the [respective specification](https://github.com/InteractiveAdvertisingBureau/AdCOM/blob/main/AdCOM%20v1.0%20FINAL.md#list--placement-positions-).

You can set `adPosition` by using the following method: 

```kotlin
adUnit.setAdPosition(AdPosition.FOOTER);
```