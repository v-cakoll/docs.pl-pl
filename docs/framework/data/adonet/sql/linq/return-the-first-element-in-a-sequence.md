---
title: Zwracanie pierwszego elementu w sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 39cf9270b08fce64590fef418bb428c5a781b0e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963814"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="8d793-102">Zwracanie pierwszego elementu w sekwencji</span><span class="sxs-lookup"><span data-stu-id="8d793-102">Return the First Element in a Sequence</span></span>
<span data-ttu-id="8d793-103"><xref:System.Linq.Enumerable.First%2A> Użyj operatora, aby zwrócić pierwszy element w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="8d793-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="8d793-104">Zapytania, które <xref:System.Linq.Enumerable.First%2A> używają są wykonywane od razu.</span><span class="sxs-lookup"><span data-stu-id="8d793-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8d793-105">nie obsługuje <xref:System.Linq.Enumerable.Last%2A> operatora.</span><span class="sxs-lookup"><span data-stu-id="8d793-105">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d793-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d793-106">Example</span></span>  
 <span data-ttu-id="8d793-107">Poniższy kod umożliwia znalezienie pierwszego `Shipper` w tabeli:</span><span class="sxs-lookup"><span data-stu-id="8d793-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="8d793-108">W przypadku uruchomienia tego zapytania względem przykładowej bazy danych Northwind wyniki są</span><span class="sxs-lookup"><span data-stu-id="8d793-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="8d793-109">`ID = 1, Company = Speedy Express`.</span><span class="sxs-lookup"><span data-stu-id="8d793-109">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="8d793-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d793-110">Example</span></span>  
 <span data-ttu-id="8d793-111">Poniższy kod umożliwia znalezienie pojedynczego `Customer` , który `CustomerID` ma BONAP.</span><span class="sxs-lookup"><span data-stu-id="8d793-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="8d793-112">W przypadku uruchomienia tego zapytania względem przykładowej bazy danych Northwind wyniki są `ID = BONAP, Contact = Laurence Lebihan`następujące.</span><span class="sxs-lookup"><span data-stu-id="8d793-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="8d793-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d793-113">See also</span></span>

- [<span data-ttu-id="8d793-114">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="8d793-114">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="8d793-115">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="8d793-115">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
