---
title: Liczbę elementów w sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 546417cc0b4aed7fa092ddb25fe37fa8d95d0e91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510485"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="2518f-102">Liczbę elementów w sekwencji</span><span class="sxs-lookup"><span data-stu-id="2518f-102">Count the Number of Elements in a Sequence</span></span>
<span data-ttu-id="2518f-103">Użyj <xref:System.Linq.Enumerable.Count%2A> operator, aby określić liczbę elementów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="2518f-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="2518f-104">Uruchomienie tego zapytania względem przykładowej bazy danych Northwind generuje dane wyjściowe `91`.</span><span class="sxs-lookup"><span data-stu-id="2518f-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2518f-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="2518f-105">Example</span></span>  
 <span data-ttu-id="2518f-106">Poniższy przykład zlicza `Customers` w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="2518f-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="2518f-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="2518f-107">Example</span></span>  
 <span data-ttu-id="2518f-108">Poniższy przykład zlicza produkty w bazie danych, które nie zostały wycofane.</span><span class="sxs-lookup"><span data-stu-id="2518f-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="2518f-109">Działających w tym przykładzie w odniesieniu do przykładowej bazy danych Northwind generuje dane wyjściowe `69`.</span><span class="sxs-lookup"><span data-stu-id="2518f-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="2518f-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2518f-110">See also</span></span>
- [<span data-ttu-id="2518f-111">Zapytania zagregowane</span><span class="sxs-lookup"><span data-stu-id="2518f-111">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [<span data-ttu-id="2518f-112">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="2518f-112">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
