---
title: Licznik liczby elementów w sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 74e24aeb64b0097cba3975e76475034e6bb9544d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247704"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="4b391-102">Licznik liczby elementów w sekwencji</span><span class="sxs-lookup"><span data-stu-id="4b391-102">Count the Number of Elements in a Sequence</span></span>
<span data-ttu-id="4b391-103">Użyj operatora <xref:System.Linq.Enumerable.Count%2A> , aby policzyć liczbę elementów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="4b391-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="4b391-104">Uruchomienie tego zapytania względem przykładowej bazy danych Northwind powoduje utworzenie danych `91`wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="4b391-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b391-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b391-105">Example</span></span>  
 <span data-ttu-id="4b391-106">Poniższy przykład zlicza liczbę `Customers` w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="4b391-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="4b391-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b391-107">Example</span></span>  
 <span data-ttu-id="4b391-108">Poniższy przykład zlicza produkty w bazie danych, które nie zostały wycofane.</span><span class="sxs-lookup"><span data-stu-id="4b391-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="4b391-109">Uruchomienie tego przykładu w przypadku przykładowej bazy danych Northwind powoduje `69`utworzenie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="4b391-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="4b391-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b391-110">See also</span></span>

- [<span data-ttu-id="4b391-111">Zapytania zagregowane</span><span class="sxs-lookup"><span data-stu-id="4b391-111">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="4b391-112">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="4b391-112">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
