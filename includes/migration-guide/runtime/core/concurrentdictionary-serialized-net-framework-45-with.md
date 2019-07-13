---
ms.openlocfilehash: b7953aab434de3b081f22acc43cf6c4a00ac0742
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858563"
---
### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a>Nie można zdeserializować ConcurrentDictionary zserializowane w .NET Framework 4.5, za pomocą NetDataContractSerializer przez program .NET Framework 4.5.1 i 4.5.2

|   |   |
|---|---|
|Szczegóły|Z powodu wewnętrznych zmian na typ <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obiekty, które są serializowane za pomocą programu .NET Framework 4.5 przy użyciu <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> nie można zdeserializować w .NET Framework 4.5.1 lub 4.5.2.Note .NET Framework to przenoszenie w innych (kierunek Serializowanie przy użyciu programu .NET Framework 4.5.x i deserializacji za pomocą programu .NET Framework 4.5) działa. Podobnie całą serializację między wersjami 4.x współpracuje z 4.6.Serializing .NET Framework i nie występuje podczas deserializacji z jednej wersji programu .NET Framework.|
|Sugestia|Jeśli to konieczne do serializacji i deserializacji <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> między .NET Framework 4.5 i 4.5.1/4.5.2 .NET Framework, takich jak alternatywny serializator <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> lub <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> serializator powinny być używane zamiast <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name>. Alternatywnie ponieważ ten problem został rozwiązany w programie .NET Framework 4.6, może można rozwiązać przez uaktualnienie do wersji programu .NET Framework.|
|Scope|Mały|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|

