### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Wywołania System.Windows.Input.PenContext.Disable w systemach z obsługą dotyku może zgłaszać ArgumentException

|   |   |
|---|---|
|Szczegóły|W pewnych okolicznościach wywołań wewnętrznej <strong>System.Windows.Intput.PenContext.Disable</strong> metody w systemach z obsługą dotyku może zgłaszać nieobsłużony <code>T:System.ArgumentException</code> z powodu ponownego rozpoczęcia.|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4.7. Aby zapobiec wyjątek, uaktualnienia do wersji programu .NET Framework, począwszy od .NET Framework 4.7.|
|Zakres|Krawędź|
|Wersja|4.6.1|
|Typ|Przekierowania|

