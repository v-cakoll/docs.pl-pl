---
title: Wykonanie podzapytania w operacji grupowania
description: Jak wykonanie podzapytania w operacji grupowania.
ms.date: 12/1/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: 209d05c2fe8719fa9116061d199272366146f465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277332"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="c319b-103">Wykonanie podzapytania w operacji grupowania</span><span class="sxs-lookup"><span data-stu-id="c319b-103">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="c319b-104">W tym temacie przedstawiono dwa różne sposoby, aby utworzyć kwerendę, porządkuje źródło danych w grupach, a następnie wykonuje podzapytania w każdej grupie pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="c319b-104">This topic shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="c319b-105">Podstawowa metoda w każdym przykładzie jest grupować elementy źródłowe przy użyciu *kontynuacji* o nazwie `newGroup`i generować nowy podzapytania przed `newGroup`.</span><span class="sxs-lookup"><span data-stu-id="c319b-105">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="c319b-106">Tym podzapytaniu jest wykonywane na każdej grupy utworzony w wyniku zapytania zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="c319b-106">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="c319b-107">Należy pamiętać, że w tym przykładzie ostateczne dane wyjściowe nie jest grupą, ale prostych sekwencji typy anonimowe.</span><span class="sxs-lookup"><span data-stu-id="c319b-107">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
 <span data-ttu-id="c319b-108">Aby uzyskać więcej informacji na temat grupy, zobacz [klauzuli group](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c319b-108">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
 <span data-ttu-id="c319b-109">Aby uzyskać więcej informacji o kontynuacje, zobacz [do](../language-reference/keywords/into.md).</span><span class="sxs-lookup"><span data-stu-id="c319b-109">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="c319b-110">W poniższym przykładzie użyto struktury danych w pamięci jako źródło danych, ale same zasady mają zastosowanie dla dowolnego rodzaju źródła danych LINQ.</span><span class="sxs-lookup"><span data-stu-id="c319b-110">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c319b-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c319b-111">Example</span></span> 

 > [!NOTE]
 > <span data-ttu-id="c319b-112">Ten przykład zawiera odwołania do obiektów, które są zdefiniowane w przykładowym kodzie w [kwerenda dotycząca kolekcji obiektów](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="c319b-112">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

 [!code-csharp[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
   
## <a name="see-also"></a><span data-ttu-id="c319b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c319b-113">See also</span></span>  
 [<span data-ttu-id="c319b-114">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="c319b-114">LINQ Query Expressions</span></span>](index.md)
