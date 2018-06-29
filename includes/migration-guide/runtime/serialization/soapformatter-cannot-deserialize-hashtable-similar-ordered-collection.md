### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>SoapFormatter nie można deserializować obiektu Hashtable i podobnie uporządkowanych kolekcji obiektów

|   |   |
|---|---|
|Szczegóły|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> Ma nie gwarancji, że obiekty serializowane w jednym .NET Framework w wersji pomyślnie przeprowadzić deserializacji w innej wersji. W szczególności niektóre uporządkowane kolekcji (takie jak <xref:System.Collections.Hashtable?displayProperty=name>) dodane elementy członkowskie między 4.0 i 4.5 w taki sposób, że obiekty tego typu nie można deserializować z programu .NET Framework 4.0, jeśli zostały one serializowany z programu .NET Framework 4.5. Należy pamiętać, że jeśli dane serializowane jest serializacji i deserializacji o tej samej wersji .NET Framework, problem nie nastąpi.|
|Sugestia|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> serializacji powinna zostać zastąpiona <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> szeregowanie lub <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> pozwala uzyskać odporność na zmiany .NET Framework.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|

