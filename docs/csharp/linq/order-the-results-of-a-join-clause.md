---
title: Kolejność wyników klauzuli join (LINQ w C#)
description: Dowiedz się, jak kolejność wyników klauzuli join LINQ w C#.
ms.date: 12/1/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: 13cd6cb202cf67def17310db6d98e368ce837646
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516989"
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="7e9c2-103">Kolejność wyników klauzuli join</span><span class="sxs-lookup"><span data-stu-id="7e9c2-103">Order the results of a join clause</span></span>

<span data-ttu-id="7e9c2-104">W tym przykładzie przedstawiono sposób uporządkowania wyników operacji tworzenia sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="7e9c2-104">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="7e9c2-105">Należy pamiętać, że kolejność jest wykonywana po sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="7e9c2-105">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="7e9c2-106">Chociaż można używać `orderby` klauzuli z co najmniej źródła sekwencji przed sprzężenia, ogólnie nie zalecamy tego.</span><span class="sxs-lookup"><span data-stu-id="7e9c2-106">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="7e9c2-107">Niektórzy dostawcy LINQ może zachować kolejności po sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="7e9c2-107">Some LINQ providers might not preserve that ordering after the join.</span></span>

## <a name="example"></a><span data-ttu-id="7e9c2-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="7e9c2-108">Example</span></span>

<span data-ttu-id="7e9c2-109">To zapytanie tworzy sprzężenie grupy, a następnie sortuje grup oparty na element kategorii, który jest nadal w zakresie.</span><span class="sxs-lookup"><span data-stu-id="7e9c2-109">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="7e9c2-110">Wewnątrz inicjatora typu anonimowego podzapytaniu zamówień zgodnych elementów z sekwencji produktów.</span><span class="sxs-lookup"><span data-stu-id="7e9c2-110">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a><span data-ttu-id="7e9c2-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e9c2-111">See also</span></span>

- [<span data-ttu-id="7e9c2-112">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="7e9c2-112">Language Integrated Query (LINQ)</span></span>](index.md)  
- [<span data-ttu-id="7e9c2-113">orderby, klauzula</span><span class="sxs-lookup"><span data-stu-id="7e9c2-113">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)  
- [<span data-ttu-id="7e9c2-114">join, klauzula</span><span class="sxs-lookup"><span data-stu-id="7e9c2-114">join clause</span></span>](../language-reference/keywords/join-clause.md)  