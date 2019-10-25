---
title: Powtarzające się pola dla list i tablic — gRPC dla deweloperów WCF
description: Dowiedz się, w jaki sposób kolekcje są obsługiwane przez protobuf oraz jak są one powiązane z kolekcjami platformy .NET.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 740af8af39af9bf31be17ad831f481176e30d81f
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846317"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>Powtarzające się pola list i tablic

Listy są określone w protobuf za pomocą słowa kluczowego prefiks `repeated`. Poniższy przykład pokazuje, jak utworzyć listę:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

W wygenerowanym kodzie pola `repeated` są reprezentowane przez `Google.Protobuf.Collections.RepeatedField<T>` typ ogólny, a nie żadne wbudowane typy kolekcji programu .NET. Typ `RepeatedField<T>` zawiera kod wymagany do serializacji i deserializacji listy do formatu sieci binarnej. Implementuje wszystkie standardowe interfejsy kolekcji .NET, takie jak <xref:System.Collections.Generic.IList%601> i <xref:System.Collections.Generic.IEnumerable%601>, dzięki czemu można używać zapytań LINQ lub łatwo konwertować je na tablicę lub listę.

>[!div class="step-by-step"]
>[Poprzedni](protobuf-nested-types.md)
>[Następny](protobuf-reserved.md)
