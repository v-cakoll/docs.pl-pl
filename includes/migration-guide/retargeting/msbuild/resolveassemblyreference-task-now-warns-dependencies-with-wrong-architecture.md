### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a>Wyświetli ostrzeżenie zależności o nieodpowiedniej architekturze resolveassemblyreference — zadanie

|   |   |
|---|---|
|Szczegóły|Zadanie emituje ostrzeżenie MSB3270, co oznacza, że odwołanie lub dowolny z jego zależności jest niezgodna Architektura aplikacji. Na przykład występuje to, jeśli aplikacja, która została skompilowana z <code>AnyCPU</code> opcja powoduje dołączenie x86 odwołania. Taki scenariusz może spowodować awarię aplikacji w czasie wykonywania (w tym przypadku, jeśli aplikacja jest wdrożona jako x64 proces).|
|Sugestia|Istnieją dwa obszary wpływu:<ul><li>Ponowna kompilacja generuje ostrzeżenia, które nie pojawił się po aplikacji został skompilowany w poprzedniej wersji programu MSBuild. Jednak ponieważ ostrzeżenia identyfikuje możliwe źródło błąd czasu wykonywania, powinien być zbadana i skierowana.</li><li>Ostrzeżenia są traktowane jako błędy, aplikacja zakończy się niepowodzeniem do skompilowania.</li></ul>|
|Zakres|Pomocnicza|
|Wersja|4.5.1|
|Typ|Przekierowania|

