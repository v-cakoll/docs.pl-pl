### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a>NetDataContractSerializer nie powiedzie się do deserializacji obiekt ConcurrentDictionary serializacji przy użyciu różnych wersji platformy .NET

|   |   |
|---|---|
|Szczegóły|Zgodnie z projektem <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> mogą być używane tylko w przypadku, gdy zarówno serializację i deserializację kończy się udostępnianie tych samych typów CLR. W związku z tym nie ma żadnej gwarancji czy obiekt serializowany z jednej wersji programu .NET Framework może być zdeserializowany przy użyciu innej wersji.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> jest typem wiadomo, że nie można deserializować poprawnie, jeśli serializacji przy użyciu programu .NET Framework 4.5 lub starszego, a następnie deserializowany za pomocą programu .NET Framework 4.5.1 lub nowszej.|
|Sugestia|Istnieje kilka możliwych obejścia tego problemu:<ul><li>Uaktualnienie serializacji do użycia w programie .NET Framework 4.5.1, jak również.</li><li>Użyj <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> zamiast <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> jako nie oczekuje dokładnie takie same typy CLR zarówno serializacji i deserializacji kończy się.</li><li>Użyj <xref:System.Collections.Generic.Dictionary%602?displayProperty=name> zamiast <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> od czasu nie występuje tego konkretnego 4.5 -&gt;Podziel 4.5.1.</li></ul>|
|Zakres|Pomocnicza|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li></ul>|

