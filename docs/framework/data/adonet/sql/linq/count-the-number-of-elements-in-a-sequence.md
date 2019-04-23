---
title: Licznik liczby elementów w sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: b39b0a1487c9f250e32b13330f2f70b7e3c7c877
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209531"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="ace2a-102">Licznik liczby elementów w sekwencji</span><span class="sxs-lookup"><span data-stu-id="ace2a-102">Count the Number of Elements in a Sequence</span></span>
<span data-ttu-id="ace2a-103">Użyj <xref:System.Linq.Enumerable.Count%2A> operator, aby określić liczbę elementów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="ace2a-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="ace2a-104">Uruchomienie tego zapytania względem przykładowej bazy danych Northwind generuje dane wyjściowe `91`.</span><span class="sxs-lookup"><span data-stu-id="ace2a-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ace2a-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="ace2a-105">Example</span></span>  
 <span data-ttu-id="ace2a-106">Poniższy przykład zlicza `Customers` w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="ace2a-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="ace2a-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="ace2a-107">Example</span></span>  
 <span data-ttu-id="ace2a-108">Poniższy przykład zlicza produkty w bazie danych, które nie zostały wycofane.</span><span class="sxs-lookup"><span data-stu-id="ace2a-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="ace2a-109">Działających w tym przykładzie w odniesieniu do przykładowej bazy danych Northwind generuje dane wyjściowe `69`.</span><span class="sxs-lookup"><span data-stu-id="ace2a-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ace2a-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ace2a-110">See also</span></span>

- [<span data-ttu-id="ace2a-111">Zapytania zagregowane</span><span class="sxs-lookup"><span data-stu-id="ace2a-111">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [<span data-ttu-id="ace2a-112">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="ace2a-112">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
