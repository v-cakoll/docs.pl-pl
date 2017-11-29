---
title: Wykonanie podzapytania w operacji grupowania
description: Jak wykonanie podzapytania w operacji grupowania.
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: f638b8a679a15891d04e02f1597d6bf7934a9e74
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="f35ff-104">Wykonanie podzapytania w operacji grupowania</span><span class="sxs-lookup"><span data-stu-id="f35ff-104">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="f35ff-105">W tym temacie przedstawiono dwa różne sposoby, aby utworzyć kwerendę, porządkuje źródło danych w grupach, a następnie wykonuje podzapytania w każdej grupie pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="f35ff-105">This topic shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="f35ff-106">Podstawowa metoda w każdym przykładzie jest grupować elementy źródłowe przy użyciu *kontynuacji* o nazwie `newGroup`i generować nowy podzapytania przed `newGroup`.</span><span class="sxs-lookup"><span data-stu-id="f35ff-106">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="f35ff-107">Tym podzapytaniu jest wykonywane na każdej grupy utworzony w wyniku zapytania zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="f35ff-107">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="f35ff-108">Należy pamiętać, że w tym przykładzie ostateczne dane wyjściowe nie jest grupą, ale prostych sekwencji typy anonimowe.</span><span class="sxs-lookup"><span data-stu-id="f35ff-108">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
 <span data-ttu-id="f35ff-109">Aby uzyskać więcej informacji na temat grupy, zobacz [klauzuli group](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f35ff-109">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
 <span data-ttu-id="f35ff-110">Aby uzyskać więcej informacji o kontynuacje, zobacz [do](../language-reference/keywords/into.md).</span><span class="sxs-lookup"><span data-stu-id="f35ff-110">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="f35ff-111">W poniższym przykładzie użyto struktury danych w pamięci jako źródło danych, ale same zasady mają zastosowanie dla dowolnego rodzaju źródła danych LINQ.</span><span class="sxs-lookup"><span data-stu-id="f35ff-111">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f35ff-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="f35ff-112">Example</span></span> 

 > [!NOTE]
 > <span data-ttu-id="f35ff-113">Ten przykład zawiera odwołania do obiektów, które są zdefiniowane w przykładowym kodzie w [kwerenda dotycząca kolekcji obiektów](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="f35ff-113">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

 [!code-csharp[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
   
## <a name="see-also"></a><span data-ttu-id="f35ff-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f35ff-114">See also</span></span>  
 [<span data-ttu-id="f35ff-115">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="f35ff-115">LINQ Query Expressions</span></span>](index.md)
