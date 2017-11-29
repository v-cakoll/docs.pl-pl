---
title: "Kolejność wyników klauzuli join"
description: "Jak kolejność wyników klauzuli join."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f948c18fb16a4f3ac02945b4a63583f1b01cad40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="aed8b-104">Kolejność wyników klauzuli join</span><span class="sxs-lookup"><span data-stu-id="aed8b-104">Order the results of a join clause</span></span>
<span data-ttu-id="aed8b-105">Ten przykład przedstawia sposób sortowania wyników operacji tworzenia sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="aed8b-105">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="aed8b-106">Należy pamiętać, że kolejność jest wykonywane po sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="aed8b-106">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="aed8b-107">Chociaż można używać `orderby` klauzuli z co najmniej jednym źródle sekwencji przed sprzężenia, zazwyczaj nie zaleca się jej.</span><span class="sxs-lookup"><span data-stu-id="aed8b-107">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="aed8b-108">Niektórzy dostawcy LINQ nie może zachować kolejność po sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="aed8b-108">Some LINQ providers might not preserve that ordering after the join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aed8b-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="aed8b-109">Example</span></span>  
 <span data-ttu-id="aed8b-110">To zapytanie tworzy sprzężenie grupy, a następnie sortuje oparte na element kategorii, który jest nadal w zakresie grupy.</span><span class="sxs-lookup"><span data-stu-id="aed8b-110">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="aed8b-111">Wewnątrz inicjatora typu anonimowego podzapytania zamówień zgodnych elementów z sekwencji produktów.</span><span class="sxs-lookup"><span data-stu-id="aed8b-111">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="aed8b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aed8b-112">See also</span></span>  
 [<span data-ttu-id="aed8b-113">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="aed8b-113">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="aed8b-114">Klauzula OrderBy</span><span class="sxs-lookup"><span data-stu-id="aed8b-114">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)  
 [<span data-ttu-id="aed8b-115">JOIN — klauzula</span><span class="sxs-lookup"><span data-stu-id="aed8b-115">join clause</span></span>](../language-reference/keywords/join-clause.md) 
