### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a>Lista&lt;T&gt;. ForEach może zgłosić wyjątek podczas modyfikowania elementu listy

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> zgłosi modułu wyliczającego <xref:System.InvalidOperationException?displayProperty=name> wyjątek, jeśli element wywołujący kolekcji zostanie zmodyfikowany. Wcześniej to czy nie zgłasza wyjątku, ale może prowadzić do wyścigu.|
|Sugestia|Najlepiej aby nie modyfikować listy podczas wyliczania ich elementów, ponieważ nigdy nie jest bezpieczne operacji należy ustalić kodu. Aby przywrócić poprzednie zachowanie, jednak aplikacji mogą odnosić się do programu .NET Framework 4.0.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Trwa przekierowywanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|

