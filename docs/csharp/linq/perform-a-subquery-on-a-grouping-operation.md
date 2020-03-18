---
title: Wykonywanie podkwerendy w operacji grupowania (LINQ w języku C#)
description: Jak wykonać podkwerendę w operacji grupowania przy użyciu LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: fd26f87ad7d5b4892f086bf8c7a34cf19a7f9e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173370"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="3db61-103">Wykonywanie podzapytania w operacji grupowania</span><span class="sxs-lookup"><span data-stu-id="3db61-103">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="3db61-104">W tym artykule przedstawiono dwa różne sposoby tworzenia kwerendy, która porządkuje dane źródłowe w grupy, a następnie wykonuje podkwerendę nad każdą grupą indywidualnie.</span><span class="sxs-lookup"><span data-stu-id="3db61-104">This article shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="3db61-105">Podstawową techniką w każdym przykładzie jest grupowanie `newGroup`elementów źródłowych przy użyciu `newGroup` *kontynuacji* o nazwie , a następnie generowanie nowej podkwerendy przeciwko .</span><span class="sxs-lookup"><span data-stu-id="3db61-105">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="3db61-106">To podkwerenda jest uruchamiana dla każdej nowej grupy utworzonej przez kwerendę zewnętrzną.</span><span class="sxs-lookup"><span data-stu-id="3db61-106">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="3db61-107">Należy zauważyć, że w tym konkretnym przykładzie ostateczne dane wyjściowe nie jest grupa, ale płaska sekwencja typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="3db61-107">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
<span data-ttu-id="3db61-108">Aby uzyskać więcej informacji na temat grupowania, zobacz [klauzulę grupy](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="3db61-108">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
<span data-ttu-id="3db61-109">Aby uzyskać więcej informacji na temat kontynuacji, zobacz [w](../language-reference/keywords/into.md).</span><span class="sxs-lookup"><span data-stu-id="3db61-109">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="3db61-110">W poniższym przykładzie używa struktury danych w pamięci jako źródła danych, ale te same zasady mają zastosowanie do dowolnego rodzaju źródła danych LINQ.</span><span class="sxs-lookup"><span data-stu-id="3db61-110">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3db61-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="3db61-111">Example</span></span>

> [!NOTE]
> <span data-ttu-id="3db61-112">W tym przykładzie znajdują się odwołania do obiektów zdefiniowanych w przykładowym kodzie w [query kolekcji obiektów](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="3db61-112">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#23](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]

<span data-ttu-id="3db61-113">Kwerenda w powyższym fragmencie kodu może być również zapisywana przy użyciu składni metody.</span><span class="sxs-lookup"><span data-stu-id="3db61-113">The query in the snippet above can also be written using method syntax.</span></span> <span data-ttu-id="3db61-114">Poniższy fragment kodu zawiera semantycznie równoważną kwerendę napisaną przy użyciu składni metody.</span><span class="sxs-lookup"><span data-stu-id="3db61-114">The following code snippet has a semantically equivalent query written using method syntax.</span></span>

[!code-csharp[csProgGuideLINQ#86](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_2.cs)]

## <a name="see-also"></a><span data-ttu-id="3db61-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3db61-115">See also</span></span>

- [<span data-ttu-id="3db61-116">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="3db61-116">Language Integrated Query (LINQ)</span></span>](index.md)
