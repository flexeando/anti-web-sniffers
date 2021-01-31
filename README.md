<h2 align="center">[CODE] ANTI-WEB SNIFFERS :cyclone:</h2>

<h4 align="center">The last post was only to stop Fiddler</h4>
<h4 align="center">I put some time and created some better and for more application to stop sniffing</h4>

—————————————————————————————————————————————————————————————————————————————————————————————————————————————————————

```csharp
CODE:

namespace AntiSniffer
{
    using System.Collections.Generic;

    public class AntiSniffer
    {
        private static readonly List<string> AppFilter = new List<string>() //you can add more to this list
        {
            "http analyzer stand-alone",
            "fiddler",
            "effetech http sniffer",
            "firesheep",
            "IEWatch Professional",
            "dumpcap",
            "wireshark",
            "wireshark portable",
            "sysinternals tcpview",
			"http debugger",
			"https debugger"
        };

        private static readonly List<string> DumpFilter = new List<string>()  //you can add more to this list
        {
            "NetworkMiner",
            "NetworkTrafficView",
            "HTTPNetworkSniffer",
            "tcpdump",
            "intercepter",
            "Intercepter-NG",
        };

        public static void Inizialize() //Use this to function to kill all open sniffers
        {
            for (int i = 0; i < AppFilter.Count; i++)
            {
                int appIndex = i;
                for (int y = 0; y < DumpFilter.Count; y++)
                {
                    int dumpIndex = y;
                    Helpers.ProcessKiller.ClosingCycle(AppFilter[appIndex], DumpFilter[dumpIndex]);
                }
            }
        }
    }
}
