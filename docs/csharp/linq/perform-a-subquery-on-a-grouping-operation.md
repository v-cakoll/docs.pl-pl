---
title: Wykonanie podzapytania w operacji grupowania (LINQ w C#)
description: Jak wykonanie podzapytania w operacji grupowania, za pomocą LINQ w C#.
ms.date: 12/1/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: 514db81b80557a3026589f00177910cc9446c0f4
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45625855"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="18b65-103">Wykonanie podzapytania w operacji grupowania</span><span class="sxs-lookup"><span data-stu-id="18b65-103">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="18b65-104">W tym artykule przedstawiono dwa różne sposoby, aby utworzyć zapytanie, porządkuje źródła danych w grupach, a następnie indywidualnie wykonuje podzapytania w każdej grupie.</span><span class="sxs-lookup"><span data-stu-id="18b65-104">This article shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="18b65-105">Podstawowa technika w każdym przykładzie jest do grupowania elementów źródła przy użyciu *kontynuacji* o nazwie `newGroup`i generować nowy podzapytania względem `newGroup`.</span><span class="sxs-lookup"><span data-stu-id="18b65-105">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="18b65-106">Podzapytania ten jest wykonywany dla każdej nowej grupy, który jest tworzony przez zapytanie zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="18b65-106">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="18b65-107">Należy pamiętać, że w tym konkretnym przykładzie końcowych danych wyjściowych nie jest grupą, ale prosty sekwencję typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="18b65-107">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
<span data-ttu-id="18b65-108">Aby uzyskać więcej informacji na temat grupy, zobacz [group — klauzula](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="18b65-108">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
<span data-ttu-id="18b65-109">Aby uzyskać więcej informacji dotyczących kontynuacji, zobacz [do](../language-reference/keywords/into.md).</span><span class="sxs-lookup"><span data-stu-id="18b65-109">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="18b65-110">W poniższym przykładzie użyto struktury danych w pamięci jako źródło danych, ale te same zasady mają zastosowanie dla każdego rodzaju źródła danych LINQ.</span><span class="sxs-lookup"><span data-stu-id="18b65-110">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18b65-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="18b65-111">Example</span></span>

> [!NOTE]
> <span data-ttu-id="18b65-112">Ten przykład zawiera odwołania do obiektów, które są zdefiniowane w przykładowym kodzie w [kwerenda dotycząca kolekcji obiektów](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="18b65-112">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#23](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="18b65-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18b65-113">See also</span></span>

- [<span data-ttu-id="18b65-114">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="18b65-114">Language Integrated Query (LINQ)</span></span>](index.md)
