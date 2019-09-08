---
title: Określanie, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: 7de65579cb41641aded0b9a320fac59804959ff5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782233"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a><span data-ttu-id="a8655-102">Określanie, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek</span><span class="sxs-lookup"><span data-stu-id="a8655-102">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>
<span data-ttu-id="a8655-103">Operator <xref:System.Linq.Enumerable.All%2A> zwraca`true` , jeśli wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="a8655-103">The <xref:System.Linq.Enumerable.All%2A> operator returns `true` if all elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="a8655-104">Operator <xref:System.Linq.Queryable.Any%2A> zwraca`true` , jeśli którykolwiek element w sekwencji spełnia warunek.</span><span class="sxs-lookup"><span data-stu-id="a8655-104">The <xref:System.Linq.Queryable.Any%2A> operator returns `true` if any element in a sequence satisfies a condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8655-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8655-105">Example</span></span>  
 <span data-ttu-id="a8655-106">Poniższy przykład zwraca sekwencję klientów, którzy mają co najmniej jedno zamówienie.</span><span class="sxs-lookup"><span data-stu-id="a8655-106">The following example returns a sequence of customers that have at least one order.</span></span> <span data-ttu-id="a8655-107">`Where` Klauzulama`true`wartość, Jeśli dana`Customer` wartość ma .`Order` / `where`</span><span class="sxs-lookup"><span data-stu-id="a8655-107">The `Where`/`where` clause evaluates to `true` if the given `Customer` has any `Order`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="a8655-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8655-108">Example</span></span>  
 <span data-ttu-id="a8655-109">Poniższy kod Visual Basic określa listę klientów, którzy nie przetworzyli zamówień, i gwarantuje, że dla każdego klienta na tej liście zostanie podana nazwa kontaktu.</span><span class="sxs-lookup"><span data-stu-id="a8655-109">The following Visual Basic code determines the list of customers who have not placed orders, and ensures that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a><span data-ttu-id="a8655-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8655-110">Example</span></span>  
 <span data-ttu-id="a8655-111">Poniższy C# przykład zwraca sekwencję klientów, których zamówienia zaczynają się `ShipCity` od znaku "C".</span><span class="sxs-lookup"><span data-stu-id="a8655-111">The following C# example returns a sequence of customers whose orders have a `ShipCity` beginning with "C".</span></span> <span data-ttu-id="a8655-112">Również uwzględniono w zwracaniu klientów, którzy nie mają zamówień.</span><span class="sxs-lookup"><span data-stu-id="a8655-112">Also included in the return are customers who have no orders.</span></span> <span data-ttu-id="a8655-113">(Według projektu, <xref:System.Linq.Queryable.All%2A> operator zwraca `true` dla pustej sekwencji). Klienci bez zamówień są eliminowani w danych wyjściowych konsoli za pomocą `Count` operatora.</span><span class="sxs-lookup"><span data-stu-id="a8655-113">(By design, the <xref:System.Linq.Queryable.All%2A> operator returns `true` for an empty sequence.) Customers with no orders are eliminated in the console output by using the `Count` operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="a8655-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8655-114">See also</span></span>

- [<span data-ttu-id="a8655-115">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="a8655-115">Query Examples</span></span>](query-examples.md)
