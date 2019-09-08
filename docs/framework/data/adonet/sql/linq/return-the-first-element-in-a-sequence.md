---
title: Zwracanie pierwszego elementu w sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 9faeed754942d7b176872484ac776c1df592bbd8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792720"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="ef296-102">Zwracanie pierwszego elementu w sekwencji</span><span class="sxs-lookup"><span data-stu-id="ef296-102">Return the First Element in a Sequence</span></span>
<span data-ttu-id="ef296-103"><xref:System.Linq.Enumerable.First%2A> Użyj operatora, aby zwrócić pierwszy element w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="ef296-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="ef296-104">Zapytania, które <xref:System.Linq.Enumerable.First%2A> używają są wykonywane od razu.</span><span class="sxs-lookup"><span data-stu-id="ef296-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="ef296-105">nie obsługuje <xref:System.Linq.Enumerable.Last%2A> operatora.</span><span class="sxs-lookup"><span data-stu-id="ef296-105">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef296-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef296-106">Example</span></span>  
 <span data-ttu-id="ef296-107">Poniższy kod umożliwia znalezienie pierwszego `Shipper` w tabeli:</span><span class="sxs-lookup"><span data-stu-id="ef296-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="ef296-108">W przypadku uruchomienia tego zapytania względem przykładowej bazy danych Northwind wyniki są</span><span class="sxs-lookup"><span data-stu-id="ef296-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="ef296-109">`ID = 1, Company = Speedy Express`.</span><span class="sxs-lookup"><span data-stu-id="ef296-109">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="ef296-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef296-110">Example</span></span>  
 <span data-ttu-id="ef296-111">Poniższy kod umożliwia znalezienie pojedynczego `Customer` , który `CustomerID` ma BONAP.</span><span class="sxs-lookup"><span data-stu-id="ef296-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="ef296-112">W przypadku uruchomienia tego zapytania względem przykładowej bazy danych Northwind wyniki są `ID = BONAP, Contact = Laurence Lebihan`następujące.</span><span class="sxs-lookup"><span data-stu-id="ef296-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="ef296-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef296-113">See also</span></span>

- [<span data-ttu-id="ef296-114">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="ef296-114">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="ef296-115">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="ef296-115">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
