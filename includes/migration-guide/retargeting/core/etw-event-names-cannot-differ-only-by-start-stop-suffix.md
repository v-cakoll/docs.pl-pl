### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>Nazwy zdarzeń funkcji ETW nie może się różnić tylko sufiksem "Start" lub "Stop"

|   |   |
|---|---|
|Szczegóły|.NET Framework 4.6 i 4.6.1 zgłasza wyjątek środowiska uruchomieniowego <xref:System.ArgumentException> gdy dwie nazwy zdarzenia funkcji Śledzenie zdarzeń systemu Windows () różnią się tylko w programie &quot;Start&quot; lub &quot;zatrzymać&quot; sufiks (jako po nazwie jedno zdarzenie <code>LogUser</code>i o innej nazwie <code>LogUserStart</code>). W takim przypadku środowisko uruchomieniowe nie można utworzyć źródła zdarzeń, którego nie można wyemitować żadnych rejestrowania.|
|Sugestia|Aby zapobiec wyjątek, upewnij się, że żadne nazwy dwóch zdarzeń różnią się tylko w programie &quot;Start&quot; lub &quot;zatrzymać&quot; sufiks. To wymaganie nie obowiązuje w programie .NET Framework 4.6.2; środowisko uruchomieniowe można odróżniania nazw zdarzeń, które różnią się tylko przez &quot;Start&quot; i &quot;zatrzymać&quot; sufiks.|
|Zakres|Krawędź|
|Wersja|4.6|
|Typ|Przekierowania|

