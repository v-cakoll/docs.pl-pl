---
title: Powtarzające się pola dla list i tablic — gRPC dla deweloperów WCF
description: Dowiedz się, w jaki sposób kolekcje są obsługiwane przez protobuf oraz jak są one powiązane z kolekcjami platformy .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 17c579bc98ba62ea74b9452bdb28efd96fc51406
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967366"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="5d41d-103">Powtarzające się pola list i tablic</span><span class="sxs-lookup"><span data-stu-id="5d41d-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="5d41d-104">Listy są określone w protobuf za pomocą słowa kluczowego prefiks `repeated`.</span><span class="sxs-lookup"><span data-stu-id="5d41d-104">Lists are specified in Protobuf using the `repeated` prefix keyword.</span></span> <span data-ttu-id="5d41d-105">Poniższy przykład pokazuje, jak utworzyć listę:</span><span class="sxs-lookup"><span data-stu-id="5d41d-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="5d41d-106">W wygenerowanym kodzie pola `repeated` są reprezentowane przez `Google.Protobuf.Collections.RepeatedField<T>` typ ogólny, a nie żadne wbudowane typy kolekcji programu .NET.</span><span class="sxs-lookup"><span data-stu-id="5d41d-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="5d41d-107">Typ `RepeatedField<T>` zawiera kod wymagany do serializacji i deserializacji listy do formatu sieci binarnej.</span><span class="sxs-lookup"><span data-stu-id="5d41d-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="5d41d-108">Implementuje wszystkie standardowe interfejsy kolekcji .NET, takie jak <xref:System.Collections.Generic.IList%601> i <xref:System.Collections.Generic.IEnumerable%601>, dzięki czemu można używać zapytań LINQ lub łatwo konwertować je na tablicę lub listę.</span><span class="sxs-lookup"><span data-stu-id="5d41d-108">It implements all the standard .NET collection interfaces such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>, so you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5d41d-109">[Poprzedni](protobuf-nested-types.md)
>[Następny](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="5d41d-109">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
