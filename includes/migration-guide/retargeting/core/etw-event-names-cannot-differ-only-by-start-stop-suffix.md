### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>Nazwy zdarzeń funkcji ETW nie różnią się jedynie sufiks "Start" lub "Zatrzymaj"

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.6 i 4.6.1, środowisko wykonawcze zgłasza <xref:System.ArgumentException> gdy dwie nazwy zdarzeń śledzenie zdarzeń dla Windows (ETW) różniących się tylko &quot;Start&quot; lub &quot;zatrzymać&quot; sufiks (jako po nazwie jedno zdarzenie <code>LogUser</code>i nosi nazwę innego <code>LogUserStart</code>). W tym przypadku środowisko uruchomieniowe nie można utworzyć źródła zdarzeń, którego nie można wyemitować wszelkie rejestrowania.|
|Sugestia|Aby zapobiec wyjątek, upewnij się, że żadne nazwy dwóch zdarzeń różniących się tylko &quot;Start&quot; lub &quot;zatrzymać&quot; sufiks. To wymaganie jest usuwany, począwszy od programu .NET Framework 4.6.2; środowisko uruchomieniowe można odróżnić nazwy zdarzeń, które różnią się tylko przez &quot;Start&quot; i &quot;zatrzymać&quot; sufiks.|
|Zakres|Krawędź|
|Wersja|4.6|
|Typ|Przekierowanie|

