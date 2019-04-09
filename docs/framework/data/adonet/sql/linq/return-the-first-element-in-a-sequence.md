---
title: Zwracanie pierwszego elementu w sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: dca917b3c12b0f9923cc9ea34a2568c412a09831
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081841"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="5fa65-102">Zwracanie pierwszego elementu w sekwencji</span><span class="sxs-lookup"><span data-stu-id="5fa65-102">Return the First Element in a Sequence</span></span>
<span data-ttu-id="5fa65-103">Użyj <xref:System.Linq.Enumerable.First%2A> operatora, aby powrócić do pierwszego elementu w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5fa65-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="5fa65-104">Wysyła zapytanie, które używają <xref:System.Linq.Enumerable.First%2A> są wykonywane natychmiast.</span><span class="sxs-lookup"><span data-stu-id="5fa65-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="5fa65-105">nie obsługuje <xref:System.Linq.Enumerable.Last%2A> operatora.</span><span class="sxs-lookup"><span data-stu-id="5fa65-105">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fa65-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fa65-106">Example</span></span>  
 <span data-ttu-id="5fa65-107">Poniższy kod wyszukuje pierwszy `Shipper` w tabeli:</span><span class="sxs-lookup"><span data-stu-id="5fa65-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="5fa65-108">Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, wyniki są</span><span class="sxs-lookup"><span data-stu-id="5fa65-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 `ID = 1, Company = Speedy Express`<span data-ttu-id="5fa65-109">.</span><span class="sxs-lookup"><span data-stu-id="5fa65-109">.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="5fa65-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fa65-110">Example</span></span>  
 <span data-ttu-id="5fa65-111">Poniższy kod umożliwia znalezienie jednej `Customer` zawierający `CustomerID` BONAP.</span><span class="sxs-lookup"><span data-stu-id="5fa65-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="5fa65-112">Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, wyniki są `ID = BONAP, Contact = Laurence Lebihan`.</span><span class="sxs-lookup"><span data-stu-id="5fa65-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="5fa65-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fa65-113">See also</span></span>

- [<span data-ttu-id="5fa65-114">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="5fa65-114">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="5fa65-115">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="5fa65-115">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
