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
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="03ee3-103">Powtarzające się pola list i tablic</span><span class="sxs-lookup"><span data-stu-id="03ee3-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="03ee3-104">Listy są określone w protobuf za pomocą słowa kluczowego prefiks `repeated`.</span><span class="sxs-lookup"><span data-stu-id="03ee3-104">Lists are specified in Protobuf using the `repeated` prefix keyword.</span></span> <span data-ttu-id="03ee3-105">Poniższy przykład pokazuje, jak utworzyć listę:</span><span class="sxs-lookup"><span data-stu-id="03ee3-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="03ee3-106">W wygenerowanym kodzie pola `repeated` są reprezentowane przez `Google.Protobuf.Collections.RepeatedField<T>` typ ogólny, a nie żadne wbudowane typy kolekcji programu .NET.</span><span class="sxs-lookup"><span data-stu-id="03ee3-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="03ee3-107">Typ `RepeatedField<T>` zawiera kod wymagany do serializacji i deserializacji listy do formatu sieci binarnej.</span><span class="sxs-lookup"><span data-stu-id="03ee3-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="03ee3-108">Implementuje wszystkie standardowe interfejsy kolekcji .NET, takie jak <xref:System.Collections.Generic.IList%601> i <xref:System.Collections.Generic.IEnumerable%601>, dzięki czemu można używać zapytań LINQ lub łatwo konwertować je na tablicę lub listę.</span><span class="sxs-lookup"><span data-stu-id="03ee3-108">It implements all the standard .NET collection interfaces such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>, so you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="03ee3-109">[Poprzedni](protobuf-nested-types.md)
>[Następny](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="03ee3-109">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
