### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Wywołania System.Windows.Input.PenContext.Disable w systemach z obsługą dotykową może zgłaszać ArgumentException

|   |   |
|---|---|
|Szczegóły|W niektórych okolicznościach wywołania wewnętrznego <strong>System.Windows.Intput.PenContext.Disable</strong> metody w systemach z obsługą dotykową może zgłaszać nieobsługiwany <code>T:System.ArgumentException</code> ze względu na współużytkowania wątkowości.|
|Sugestia|Ten problem został rozwiązany w programie .NET Framework 4.7. Aby zapobiec wyjątek, uaktualnienie do wersji programu .NET Framework, począwszy od programu .NET Framework 4.7.|
|Zakres|Krawędź|
|Wersja|4.6.1|
|Typ|Trwa przekierowywanie|

