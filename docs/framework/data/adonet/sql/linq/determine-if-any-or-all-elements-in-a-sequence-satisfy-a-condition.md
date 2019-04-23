---
title: Określanie, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: c1bc8e18f2e3b0c67b98713e67fc261649a6a0e2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128339"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a><span data-ttu-id="12bfa-102">Określanie, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek</span><span class="sxs-lookup"><span data-stu-id="12bfa-102">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>
<span data-ttu-id="12bfa-103"><xref:System.Linq.Enumerable.All%2A> Operator zwraca `true` Jeśli wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="12bfa-103">The <xref:System.Linq.Enumerable.All%2A> operator returns `true` if all elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="12bfa-104"><xref:System.Linq.Queryable.Any%2A> Operator zwraca `true` Jeśli dowolnego elementu w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="12bfa-104">The <xref:System.Linq.Queryable.Any%2A> operator returns `true` if any element in a sequence satisfies a condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12bfa-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="12bfa-105">Example</span></span>  
 <span data-ttu-id="12bfa-106">Poniższy przykład zwraca sekwencję klientów, którzy mają co najmniej jedno ustawienie kolejności.</span><span class="sxs-lookup"><span data-stu-id="12bfa-106">The following example returns a sequence of customers that have at least one order.</span></span> <span data-ttu-id="12bfa-107">`Where` / `where` Daje w wyniku klauzuli `true` Jeśli danego `Customer` ma jakiekolwiek `Order`.</span><span class="sxs-lookup"><span data-stu-id="12bfa-107">The `Where`/`where` clause evaluates to `true` if the given `Customer` has any `Order`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="12bfa-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="12bfa-108">Example</span></span>  
 <span data-ttu-id="12bfa-109">Poniższy kod w języku Visual Basic Określa listę klientów, którzy nie dokonali zamówień i gwarantuje, że dla każdego klienta na tej liście podano nazwę kontaktu.</span><span class="sxs-lookup"><span data-stu-id="12bfa-109">The following Visual Basic code determines the list of customers who have not placed orders, and ensures that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a><span data-ttu-id="12bfa-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="12bfa-110">Example</span></span>  
 <span data-ttu-id="12bfa-111">Następujące C# przykład zwraca sekwencję klientów, których zamówienia mają `ShipCity` rozpoczynające się od "C".</span><span class="sxs-lookup"><span data-stu-id="12bfa-111">The following C# example returns a sequence of customers whose orders have a `ShipCity` beginning with "C".</span></span> <span data-ttu-id="12bfa-112">Również powrót obejmuje klienci, którzy mają nie zamówienia.</span><span class="sxs-lookup"><span data-stu-id="12bfa-112">Also included in the return are customers who have no orders.</span></span> <span data-ttu-id="12bfa-113">(Zgodnie z projektem <xref:System.Linq.Queryable.All%2A> operator zwraca `true` dla pustej sekwencji.) Klienci z brak zamówień są eliminowane w danych wyjściowych konsoli przy użyciu `Count` operatora.</span><span class="sxs-lookup"><span data-stu-id="12bfa-113">(By design, the <xref:System.Linq.Queryable.All%2A> operator returns `true` for an empty sequence.) Customers with no orders are eliminated in the console output by using the `Count` operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="12bfa-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12bfa-114">See also</span></span>

- [<span data-ttu-id="12bfa-115">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="12bfa-115">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
