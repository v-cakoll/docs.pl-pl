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
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="7fa7a-103">Powtarzające się pola dla list i tablic</span><span class="sxs-lookup"><span data-stu-id="7fa7a-103">Repeated fields for lists and arrays</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="7fa7a-104">Listy są określone w protobuf za pomocą `repeated` słowa kluczowego prefix.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-104">Lists are specified in Protobuf using the `repeated` prefix keyword.</span></span> <span data-ttu-id="7fa7a-105">Poniższy przykład pokazuje, jak utworzyć listę:</span><span class="sxs-lookup"><span data-stu-id="7fa7a-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="7fa7a-106">W wygenerowanym kodzie `repeated` pola są reprezentowane `Google.Protobuf.Collections.RepeatedField<T>` przez typ ogólny, a nie żadne wbudowane typy kolekcji programu .NET.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="7fa7a-107">`RepeatedField<T>` Typ zawiera kod wymagany do serializacji i deserializacji listy do formatu sieci binarnej.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="7fa7a-108">Implementuje ona wszystkie standardowe interfejsy kolekcji .NET, takie jak <xref:System.Collections.Generic.IList%601> i <xref:System.Collections.Generic.IEnumerable%601>, aby można było używać zapytań LINQ lub łatwo konwertować je na tablicę lub listę.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-108">It implements all the standard .NET collection interfaces such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>, so you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7fa7a-109">[Poprzedni](protobuf-nested-types.md)
>[Następny](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="7fa7a-109">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
