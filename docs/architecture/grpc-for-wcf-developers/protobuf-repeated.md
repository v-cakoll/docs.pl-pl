---
title: Powtarzające się pola dla list i tablic — gRPC dla deweloperów WCF
description: Dowiedz się, jak protobuf obsługuje kolekcje i jak są one powiązane z kolekcjami programu .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 16f2b5a54b032f32c8fcb9d572d5284fe589cb01
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542962"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>Powtarzające się pola list i tablic

Należy określić listy w buforze protokołu (protobuf) za pomocą słowa kluczowego prefiksu `repeated`. Poniższy przykład pokazuje, jak utworzyć listę:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

W wygenerowanym kodzie pola `repeated` są reprezentowane przez `Google.Protobuf.Collections.RepeatedField<T>` typ ogólny, a nie żadne wbudowane typy kolekcji programu .NET. 

Typ `RepeatedField<T>` zawiera kod wymagany do serializacji i deserializacji listy do formatu sieci binarnej. Implementuje wszystkie standardowe interfejsy kolekcji .NET, takie jak <xref:System.Collections.Generic.IList%601> i <xref:System.Collections.Generic.IEnumerable%601>. Dzięki temu można używać zapytań LINQ lub łatwo konwertować je na tablicę lub listę.

>[!div class="step-by-step"]
>[Poprzednie](protobuf-nested-types.md)
>[dalej](protobuf-reserved.md)
