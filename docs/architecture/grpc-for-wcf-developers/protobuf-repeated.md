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
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="13a23-103">Powtarzające się pola list i tablic</span><span class="sxs-lookup"><span data-stu-id="13a23-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="13a23-104">Należy określić listy w buforze protokołu (protobuf) za pomocą słowa kluczowego prefiksu `repeated`.</span><span class="sxs-lookup"><span data-stu-id="13a23-104">You specify lists in Protocol Buffer (Protobuf) by using the `repeated` prefix keyword.</span></span> <span data-ttu-id="13a23-105">Poniższy przykład pokazuje, jak utworzyć listę:</span><span class="sxs-lookup"><span data-stu-id="13a23-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="13a23-106">W wygenerowanym kodzie pola `repeated` są reprezentowane przez `Google.Protobuf.Collections.RepeatedField<T>` typ ogólny, a nie żadne wbudowane typy kolekcji programu .NET.</span><span class="sxs-lookup"><span data-stu-id="13a23-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> 

<span data-ttu-id="13a23-107">Typ `RepeatedField<T>` zawiera kod wymagany do serializacji i deserializacji listy do formatu sieci binarnej.</span><span class="sxs-lookup"><span data-stu-id="13a23-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="13a23-108">Implementuje wszystkie standardowe interfejsy kolekcji .NET, takie jak <xref:System.Collections.Generic.IList%601> i <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="13a23-108">It implements all the standard .NET collection interfaces, such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="13a23-109">Dzięki temu można używać zapytań LINQ lub łatwo konwertować je na tablicę lub listę.</span><span class="sxs-lookup"><span data-stu-id="13a23-109">So you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="13a23-110">[Poprzednie](protobuf-nested-types.md)
>[dalej](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="13a23-110">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
