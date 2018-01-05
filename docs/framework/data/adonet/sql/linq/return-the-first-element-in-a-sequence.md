---
title: Zwraca pierwszy Element w sekwencji
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
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 476b8863d05f0c2d77b1b90c8795b85449ed3160
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="cc2ec-102">Zwraca pierwszy Element w sekwencji</span><span class="sxs-lookup"><span data-stu-id="cc2ec-102">Return the First Element in a Sequence</span></span>
<span data-ttu-id="cc2ec-103">Użyj <xref:System.Linq.Enumerable.First%2A> operatora, aby zwrócić pierwszego elementu w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="cc2ec-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="cc2ec-104">Wysyła zapytanie używające <xref:System.Linq.Enumerable.First%2A> są wykonywane natychmiast.</span><span class="sxs-lookup"><span data-stu-id="cc2ec-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="cc2ec-105">nie obsługuje <xref:System.Linq.Enumerable.Last%2A> operatora.</span><span class="sxs-lookup"><span data-stu-id="cc2ec-105"> does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc2ec-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc2ec-106">Example</span></span>  
 <span data-ttu-id="cc2ec-107">Następujący kod znajduje pierwszy `Shipper` w tabeli:</span><span class="sxs-lookup"><span data-stu-id="cc2ec-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="cc2ec-108">Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, wyniki są</span><span class="sxs-lookup"><span data-stu-id="cc2ec-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="cc2ec-109">`ID = 1, Company = Speedy Express`.,</span><span class="sxs-lookup"><span data-stu-id="cc2ec-109">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="cc2ec-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc2ec-110">Example</span></span>  
 <span data-ttu-id="cc2ec-111">Poniższy kod umożliwia znalezienie pojedynczą `Customer` mający `CustomerID` BONAP.</span><span class="sxs-lookup"><span data-stu-id="cc2ec-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="cc2ec-112">Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, wyniki są `ID = BONAP, Contact = Laurence Lebihan`.</span><span class="sxs-lookup"><span data-stu-id="cc2ec-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="cc2ec-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc2ec-113">See Also</span></span>  
 [<span data-ttu-id="cc2ec-114">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="cc2ec-114">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="cc2ec-115">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="cc2ec-115">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
