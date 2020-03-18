---
title: Zamów wyniki klauzuli sprzężenia (LINQ w języku C#)
description: Dowiedz się, jak uporządkować wyniki linq join klauzuli w języku C#.
ms.date: 12/01/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f60000b83bf378dd8740b7255d421dd4335614c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659868"
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="d6942-103">Kolejność wyników klauzuli join</span><span class="sxs-lookup"><span data-stu-id="d6942-103">Order the results of a join clause</span></span>

<span data-ttu-id="d6942-104">W tym przykładzie pokazano, jak uporządkować wyniki operacji sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="d6942-104">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="d6942-105">Należy zauważyć, że kolejność jest wykonywana po sprzężeniu.</span><span class="sxs-lookup"><span data-stu-id="d6942-105">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="d6942-106">Mimo że można `orderby` użyć klauzuli z co najmniej jedną sekwencją źródłową przed sprzężeniem, zazwyczaj nie zaleca się jej.</span><span class="sxs-lookup"><span data-stu-id="d6942-106">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="d6942-107">Niektórzy dostawcy LINQ może nie zachować, że kolejność po sprzężeniu.</span><span class="sxs-lookup"><span data-stu-id="d6942-107">Some LINQ providers might not preserve that ordering after the join.</span></span>

## <a name="example"></a><span data-ttu-id="d6942-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6942-108">Example</span></span>

<span data-ttu-id="d6942-109">Ta kwerenda tworzy sprzężenie grupy, a następnie sortuje grupy na podstawie elementu kategorii, który nadal znajduje się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="d6942-109">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="d6942-110">Wewnątrz inicjatora typu anonimowego kwerenda podrzędna porządkuje wszystkie pasujące elementy z sekwencji produktów.</span><span class="sxs-lookup"><span data-stu-id="d6942-110">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a><span data-ttu-id="d6942-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6942-111">See also</span></span>

- [<span data-ttu-id="d6942-112">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="d6942-112">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="d6942-113">Klauzula orderby</span><span class="sxs-lookup"><span data-stu-id="d6942-113">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="d6942-114">klauzula sprzężenia</span><span class="sxs-lookup"><span data-stu-id="d6942-114">join clause</span></span>](../language-reference/keywords/join-clause.md)
