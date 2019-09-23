---
title: Powtarzające się pola dla list i tablic — gRPC dla deweloperów WCF
description: Dowiedz się, w jaki sposób kolekcje są obsługiwane przez protobuf oraz jak są one powiązane z kolekcjami platformy .NET.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: ad06551bf3eaec795865af227815b78c9601d0db
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184184"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>Powtarzające się pola dla list i tablic

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Listy są określone w protobuf za pomocą `repeated` słowa kluczowego prefix. Poniższy przykład pokazuje, jak utworzyć listę:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

W wygenerowanym kodzie `repeated` pola są reprezentowane `Google.Protobuf.Collections.RepeatedField<T>` przez typ ogólny, a nie żadne wbudowane typy kolekcji programu .NET. `RepeatedField<T>` Typ zawiera kod wymagany do serializacji i deserializacji listy do formatu sieci binarnej. Implementuje ona wszystkie standardowe interfejsy kolekcji .NET, takie jak <xref:System.Collections.Generic.IList%601> i <xref:System.Collections.Generic.IEnumerable%601>, aby można było używać zapytań LINQ lub łatwo konwertować je na tablicę lub listę.

>[!div class="step-by-step"]
>[Poprzedni](protobuf-nested-types.md)
>[Następny](protobuf-reserved.md)
