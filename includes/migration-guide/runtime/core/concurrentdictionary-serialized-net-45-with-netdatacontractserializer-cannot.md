### <a name="a-concurrentdictionary-serialized-in-net-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-451-or-452"></a>Obiekt ConcurrentDictionary zserializowane w .NET 4.5 z NetDataContractSerializer nie można przeprowadzić deserializacji przez .NET 4.5.1 lub 4.5.2

|   |   |
|---|---|
|Szczegóły|Z powodu zmian wewnętrzny typ <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obiektów, które są serializowane z programu .NET Framework 4.5 przy użyciu <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> nie można przeprowadzić deserializacji w programie .NET Framework 4.5.1 lub 4.5.2.Note .NET Framework to przenoszenie w innych (kierunek Serializacja z programu .NET Framework 4.5.x i deserializację z programu .NET Framework 4.5) działa. Podobnie wszystkie serializacji między wersjami 4.x współpracuje z 4.6.Serializing .NET Framework i nie występuje podczas deserializacji z jednej wersji programu .NET Framework.|
|Sugestia|Jeśli jest konieczne w celu serializacji i deserializacji <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> między .NET Framework 4.5 i 4.5.1/4.5.2 .NET Framework, takich jak alternatywny serializator <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> lub <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> serializator powinien być używany zamiast <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name>. Alternatywnie ponieważ ten problem został rozwiązany w .NET Framework 4.6, mogą zostać rozwiązane przez uaktualnienie do tej wersji programu .NET Framework.|
|Zakres|Pomocnicza|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|

