---
ms.openlocfilehash: ae0f68a19d6eae53998d61e924cfef3aaaec1784
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620228"
---
### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a>Serializacja ConcurrentDictionary w .NET Framework 4,5 z NetDataContractSerializerem nie może zostać zdeserializować przez .NET Framework 4.5.1 lub 4.5.2

#### <a name="details"></a>Szczegóły

Ze względu na wewnętrzne zmiany typu <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obiekty, które są serializowane z .NET Framework 4,5 przy użyciu <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> nie można deserializować w .NET Framework 4.5.1 lub w .NET Framework 4.5.2. Zauważ, że poruszane w innym kierunku (Serializacja przy użyciu .NET Framework 4.5. x i deserializacji z .NET Framework 4,5). Podobnie, wszystkie 4. x serializacji między wersjami współdziałają z .NET Framework 4.6. Serializacja i deserializacja z jedną wersją .NET Framework nie ma żadnego oddziaływania.

#### <a name="suggestion"></a>Sugestia

Jeśli konieczne jest Serializacja i deserializacja <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> między .NET Framework 4,5 i .NET Framework 4.5.1/4.5.2, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> zamiast elementu należy użyć alternatywnego serializatora, takiego jak serializator lub <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> . Alternatywnie, ponieważ ten problem został rozwiązany w .NET Framework 4,6, może zostać rozwiązany przez uaktualnienie do tej wersji .NET Framework.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
