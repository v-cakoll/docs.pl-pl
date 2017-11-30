---
title: "Określić, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek"
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
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0dda546c0d8cd073a5d11bdf22805310e3f4f40a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a><span data-ttu-id="79d9b-102">Określić, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek</span><span class="sxs-lookup"><span data-stu-id="79d9b-102">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>
<span data-ttu-id="79d9b-103"><xref:System.Linq.Enumerable.All%2A> Operator zwraca `true` , gdy wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="79d9b-103">The <xref:System.Linq.Enumerable.All%2A> operator returns `true` if all elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="79d9b-104"><xref:System.Linq.Queryable.Any%2A> Operator zwraca `true` Jeśli dowolny element w sekwencji spełnia warunek.</span><span class="sxs-lookup"><span data-stu-id="79d9b-104">The <xref:System.Linq.Queryable.Any%2A> operator returns `true` if any element in a sequence satisfies a condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79d9b-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="79d9b-105">Example</span></span>  
 <span data-ttu-id="79d9b-106">Poniższy przykład zwraca sekwencję klientów, którzy mają co najmniej jednego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="79d9b-106">The following example returns a sequence of customers that have at least one order.</span></span> <span data-ttu-id="79d9b-107">`Where` / `where` Daje w wyniku klauzuli `true` Jeśli dany `Customer` ma jakiekolwiek `Order`.</span><span class="sxs-lookup"><span data-stu-id="79d9b-107">The `Where`/`where` clause evaluates to `true` if the given `Customer` has any `Order`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="79d9b-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="79d9b-108">Example</span></span>  
 <span data-ttu-id="79d9b-109">Poniższy kod Visual Basic Określa listę klientów, którzy nie dokonali zamówienia i zapewnia, że dla każdego klienta na tej liście podano nazwę kontaktu.</span><span class="sxs-lookup"><span data-stu-id="79d9b-109">The following Visual Basic code determines the list of customers who have not placed orders, and ensures that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a><span data-ttu-id="79d9b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="79d9b-110">Example</span></span>  
 <span data-ttu-id="79d9b-111">W poniższym przykładzie C# zwraca sekwencję klientów, których zamówień `ShipCity` rozpoczynające się od "C".</span><span class="sxs-lookup"><span data-stu-id="79d9b-111">The following C# example returns a sequence of customers whose orders have a `ShipCity` beginning with "C".</span></span> <span data-ttu-id="79d9b-112">Również zwracany obejmuje klientów, którzy mają żadnych zleceń.</span><span class="sxs-lookup"><span data-stu-id="79d9b-112">Also included in the return are customers who have no orders.</span></span> <span data-ttu-id="79d9b-113">(Zgodnie z projektem <xref:System.Linq.Queryable.All%2A> operator zwraca `true` dla pustej sekwencji.) Klienci z żadnych zamówień są eliminowane w danych wyjściowych konsoli przy użyciu `Count` operatora.</span><span class="sxs-lookup"><span data-stu-id="79d9b-113">(By design, the <xref:System.Linq.Queryable.All%2A> operator returns `true` for an empty sequence.) Customers with no orders are eliminated in the console output by using the `Count` operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="79d9b-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79d9b-114">See Also</span></span>  
 [<span data-ttu-id="79d9b-115">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="79d9b-115">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
