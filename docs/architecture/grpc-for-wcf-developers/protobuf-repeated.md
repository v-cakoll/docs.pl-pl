---
title: Powtarzające się pola dla list i tablic - gRPC dla deweloperów WCF
description: Dowiedz się, jak Protobuf obsługuje kolekcje i jak odnoszą się one do kolekcji .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 63d99532d14deea7800673dd5a6350dd9362ad54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147974"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>Powtarzające się pola list i tablic

Listy można określić w buforze protokołu (Protobuf) za pomocą słowa kluczowego `repeated` prefiksu. W poniższym przykładzie pokazano, jak utworzyć listę:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

W wygenerowanym kodzie pola są `Google.Protobuf.Collections.RepeatedField<T>` reprezentowane przez typ ogólny, `repeated` a nie przez którykolwiek z wbudowanych typów kolekcji .NET.

Typ `RepeatedField<T>` zawiera kod wymagany do serializacji i deserializacji listy do formatu przewodu binarnego. Implementuje wszystkie standardowe interfejsy kolekcji .NET, takie jak <xref:System.Collections.Generic.IList%601> i <xref:System.Collections.Generic.IEnumerable%601>. Możesz więc łatwo używać zapytań LINQ lub konwertować je na tablicę lub listę.

>[!div class="step-by-step"]
>[Poprzedni](protobuf-nested-types.md)
>[następny](protobuf-reserved.md)
