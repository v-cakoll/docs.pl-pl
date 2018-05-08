### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a>Lista&lt;T&gt;. ForEach może zgłosić wyjątek podczas modyfikowania elementu listy

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.5, <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> zgłosi modułu wyliczającego <xref:System.InvalidOperationException?displayProperty=name> wyjątek, jeśli element wywołujący kolekcji jest modyfikowany. Wcześniej to nie spowoduje zgłoszenie wyjątku, ale może prowadzić do wyścigu.|
|Sugestia|Najlepiej, jeśli kod powinna zostać ustalona nie zmodyfikować listy podczas wyliczania ich elementów, ponieważ nie jest bezpieczne operacji. Aby powrócić do poprzedniej zachowanie, jednak aplikacji mogą odnosić się do programu .NET Framework 4.0.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|

