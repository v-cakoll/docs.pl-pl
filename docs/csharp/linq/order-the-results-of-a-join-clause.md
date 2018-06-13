---
title: Kolejność wyników klauzuli join
description: Jak kolejność wyników klauzuli join.
ms.date: 12/1/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f426152e614ed9a9c4aa41d7ba7cb8ddf1cd3063
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269703"
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="736bb-103">Kolejność wyników klauzuli join</span><span class="sxs-lookup"><span data-stu-id="736bb-103">Order the results of a join clause</span></span>
<span data-ttu-id="736bb-104">Ten przykład przedstawia sposób sortowania wyników operacji tworzenia sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="736bb-104">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="736bb-105">Należy pamiętać, że kolejność jest wykonywane po sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="736bb-105">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="736bb-106">Chociaż można używać `orderby` klauzuli z co najmniej jednym źródle sekwencji przed sprzężenia, zazwyczaj nie zaleca się jej.</span><span class="sxs-lookup"><span data-stu-id="736bb-106">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="736bb-107">Niektórzy dostawcy LINQ nie może zachować kolejność po sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="736bb-107">Some LINQ providers might not preserve that ordering after the join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="736bb-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="736bb-108">Example</span></span>  
 <span data-ttu-id="736bb-109">To zapytanie tworzy sprzężenie grupy, a następnie sortuje oparte na element kategorii, który jest nadal w zakresie grupy.</span><span class="sxs-lookup"><span data-stu-id="736bb-109">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="736bb-110">Wewnątrz inicjatora typu anonimowego podzapytania zamówień zgodnych elementów z sekwencji produktów.</span><span class="sxs-lookup"><span data-stu-id="736bb-110">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="736bb-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="736bb-111">See also</span></span>  
 [<span data-ttu-id="736bb-112">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="736bb-112">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="736bb-113">orderby, klauzula</span><span class="sxs-lookup"><span data-stu-id="736bb-113">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)  
 [<span data-ttu-id="736bb-114">join, klauzula</span><span class="sxs-lookup"><span data-stu-id="736bb-114">join clause</span></span>](../language-reference/keywords/join-clause.md) 
