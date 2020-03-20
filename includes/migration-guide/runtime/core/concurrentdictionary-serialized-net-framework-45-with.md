---
ms.openlocfilehash: f9d7b8d22818245b96cafffe3732bdfe82ff69d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858563"
---
### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a>Nie można deserializować programu .NET Framework 4.5 z programu NetDataContractSerializer przez platformę .NET Framework 4.5.1 lub 4.5.2

|   |   |
|---|---|
|Szczegóły|Ze względu na wewnętrzne <xref:System.Collections.Concurrent.ConcurrentDictionary%602> zmiany typu, obiekty, które są serializowane z <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> .NET Framework 4.5 przy użyciu programu .NET Framework 4.5.1 lub w .NET Framework 4.5.2.Note, że poruszanie się w innym kierunku (serializacji z .NET Framework 4.5.x i deserializacji z .NET Framework 4.5) działa. Podobnie wszystkie serializacji w wersji krzyżowej 4.x działa z .NET Framework 4.6.Serializing i deserializing z pojedynczą wersją programu .NET Framework nie ma wpływu.|
|Sugestia|Jeśli konieczne jest serializować i <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> deserialize między .NET Framework 4.5 i .NET Framework 4.5.1/4.5.2, alternatywny serializator jak <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> lub <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> serializatora powinny być używane zamiast <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name>. Alternatywnie, ponieważ ten problem został rozwiązany w .NET Framework 4.6, można go rozwiązać przez uaktualnienie do tej wersji programu .NET Framework.|
|Zakres|Mały|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
