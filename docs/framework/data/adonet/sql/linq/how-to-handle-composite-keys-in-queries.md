---
title: 'Instrukcje: Obsługa kluczy złożonych w zapytaniach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: 2621ab4db207d1b868fbe3778c30c744201b0506
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033816"
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="43c33-102">Instrukcje: Obsługa kluczy złożonych w zapytaniach</span><span class="sxs-lookup"><span data-stu-id="43c33-102">How to: Handle Composite Keys in Queries</span></span>
<span data-ttu-id="43c33-103">Niektóre operatory może zająć tylko jeden argument.</span><span class="sxs-lookup"><span data-stu-id="43c33-103">Some operators can take only one argument.</span></span> <span data-ttu-id="43c33-104">Jeśli argument musi zawierać więcej niż jedną kolumnę z bazy danych, należy utworzyć typ anonimowy do reprezentowania połączenie.</span><span class="sxs-lookup"><span data-stu-id="43c33-104">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43c33-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="43c33-105">Example</span></span>  
 <span data-ttu-id="43c33-106">Poniższy kod przedstawia zapytanie, które wywołuje `GroupBy` operatora, który może mieć tylko jedną `key` argumentu.</span><span class="sxs-lookup"><span data-stu-id="43c33-106">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="43c33-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="43c33-107">Example</span></span>  
 <span data-ttu-id="43c33-108">Taka sama sytuacja dotyczy sprzężenia, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="43c33-108">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="43c33-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43c33-109">See also</span></span>

- [<span data-ttu-id="43c33-110">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="43c33-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
