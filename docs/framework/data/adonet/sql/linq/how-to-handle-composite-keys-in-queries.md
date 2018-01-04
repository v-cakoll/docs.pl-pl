---
title: "Porady: Obsługa klucze złożone w zapytaniach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2b0954d4659d1cc39cead0658fbd21dcd6dd12e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="8144c-102">Porady: Obsługa klucze złożone w zapytaniach</span><span class="sxs-lookup"><span data-stu-id="8144c-102">How to: Handle Composite Keys in Queries</span></span>
<span data-ttu-id="8144c-103">Operatory niektóre możliwe jest tylko jeden argument.</span><span class="sxs-lookup"><span data-stu-id="8144c-103">Some operators can take only one argument.</span></span> <span data-ttu-id="8144c-104">Argument musi zawierać więcej niż jedną kolumnę z bazy danych, należy utworzyć typu anonimowego do reprezentowania połączenie.</span><span class="sxs-lookup"><span data-stu-id="8144c-104">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8144c-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="8144c-105">Example</span></span>  
 <span data-ttu-id="8144c-106">W poniższym przykładzie przedstawiono kwerendę, która wywołuje `GroupBy` operatora, który można wykonać tylko jedną `key` argumentu.</span><span class="sxs-lookup"><span data-stu-id="8144c-106">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="8144c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="8144c-107">Example</span></span>  
 <span data-ttu-id="8144c-108">Ta sama sytuacja dotyczy sprzężenia, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8144c-108">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8144c-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8144c-109">See Also</span></span>  
 [<span data-ttu-id="8144c-110">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="8144c-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
