---
ms.openlocfilehash: 380f662349a8dcd04e5bf445e1479d0a32d5861f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235608"
---
### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a>NetDataContractSerializer zakończy się niepowodzeniem do deserializacji ConcurrentDictionary serializowany z innej wersji platformy .NET

|   |   |
|---|---|
|Szczegóły|Zgodnie z projektem <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> mogą służyć tylko wtedy, gdy zarówno serializacji i deserializacji kończy się udostępniać te same typy CLR. W związku z tym nie ma żadnej gwarancji, obiekt, który serializowany z jednej wersji programu .NET Framework może być zdeserializowany przy użyciu innej wersji.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> to typ, który jest znany nie można deserializować poprawnie, jeśli serializacji przy użyciu programu .NET Framework 4.5 lub starszej, a następnie deserializowany za pomocą programu .NET Framework 4.5.1 lub nowszej.|
|Sugestia|Istnieje kilka możliwych obejścia tego problemu:<ul><li>Uaktualnienie serializacji do użycia programu .NET Framework 4.5.1, jak również.</li><li>Użyj <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> zamiast <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> jako nie oczekuje dokładnie te same typy CLR zarówno na poziomie serializacji i deserializacji kończy się.</li><li>Użyj <xref:System.Collections.Generic.Dictionary%602?displayProperty=name> zamiast <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> , ponieważ nie jest zauważalna podczas tego konkretnego 4.5 -&gt;Przerwij 4.5.1.</li></ul>|
|Zakres|Mały|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li></ul>|
