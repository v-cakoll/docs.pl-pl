---
ms.openlocfilehash: 6ed7438a7f6e7710fcce03c8260a1360143f8d93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235492"
---
### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>SoapFormatter nie można deserializować obiektu Hashtable i podobne uporządkowane obiekty kolekcji

|   |   |
|---|---|
|Szczegóły|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> Ma nie gwarancji, że obiekty są serializowane w ramach jednej wersji programu .NET Framework pomyślnie przeprowadzić deserializacji w innej wersji. W szczególności niektóre uporządkowane kolekcji (np. <xref:System.Collections.Hashtable?displayProperty=name>) dodane elementy członkowskie między 4.0 i 4.5 w taki sposób, że obiekty tego typu nie można deserializować za pomocą programu .NET Framework 4.0, jeśli zostały one Zserializowany za pomocą programu .NET Framework 4.5. Należy pamiętać, że jeśli serializowane dane jest serializacji i deserializacji za pomocą tej samej wersji środowiska .NET Framework, problem nie wystąpi.|
|Sugestia|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> należy zastąpić serializacji <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> serializacji lub <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> być odporne na zmiany w .NET Framework.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|
