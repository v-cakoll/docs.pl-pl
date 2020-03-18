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
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="4df37-103">Powtarzające się pola list i tablic</span><span class="sxs-lookup"><span data-stu-id="4df37-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="4df37-104">Listy można określić w buforze protokołu (Protobuf) za pomocą słowa kluczowego `repeated` prefiksu.</span><span class="sxs-lookup"><span data-stu-id="4df37-104">You specify lists in Protocol Buffer (Protobuf) by using the `repeated` prefix keyword.</span></span> <span data-ttu-id="4df37-105">W poniższym przykładzie pokazano, jak utworzyć listę:</span><span class="sxs-lookup"><span data-stu-id="4df37-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="4df37-106">W wygenerowanym kodzie pola są `Google.Protobuf.Collections.RepeatedField<T>` reprezentowane przez typ ogólny, `repeated` a nie przez którykolwiek z wbudowanych typów kolekcji .NET.</span><span class="sxs-lookup"><span data-stu-id="4df37-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span>

<span data-ttu-id="4df37-107">Typ `RepeatedField<T>` zawiera kod wymagany do serializacji i deserializacji listy do formatu przewodu binarnego.</span><span class="sxs-lookup"><span data-stu-id="4df37-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="4df37-108">Implementuje wszystkie standardowe interfejsy kolekcji .NET, takie jak <xref:System.Collections.Generic.IList%601> i <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="4df37-108">It implements all the standard .NET collection interfaces, such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="4df37-109">Możesz więc łatwo używać zapytań LINQ lub konwertować je na tablicę lub listę.</span><span class="sxs-lookup"><span data-stu-id="4df37-109">So you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4df37-110">[Poprzedni](protobuf-nested-types.md)
>[następny](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="4df37-110">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
