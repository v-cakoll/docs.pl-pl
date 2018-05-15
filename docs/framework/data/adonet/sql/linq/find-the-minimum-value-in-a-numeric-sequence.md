---
title: Znajdź wartość minimalną sekwencją liczb
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
ms.openlocfilehash: 9b55c0a188f7e5857ddc5021c820be847ce63600
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a><span data-ttu-id="3b412-102">Znajdź wartość minimalną sekwencją liczb</span><span class="sxs-lookup"><span data-stu-id="3b412-102">Find the Minimum Value in a Numeric Sequence</span></span>
<span data-ttu-id="3b412-103">Użyj <xref:System.Linq.Enumerable.Min%2A> operatora, aby zwrócić wartość minimalna z sekwencję wartości liczbowych.</span><span class="sxs-lookup"><span data-stu-id="3b412-103">Use the <xref:System.Linq.Enumerable.Min%2A> operator to return the minimum value from a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b412-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b412-104">Example</span></span>  
 <span data-ttu-id="3b412-105">Poniższy przykład umożliwia znalezienie najniższej cenie jednostkowej jakiegokolwiek produktu.</span><span class="sxs-lookup"><span data-stu-id="3b412-105">The following example finds the lowest unit price of any product.</span></span>  
  
 <span data-ttu-id="3b412-106">Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, dane wyjściowe są: `2.5000`.</span><span class="sxs-lookup"><span data-stu-id="3b412-106">If you run this query against the Northwind sample database, the output is: `2.5000`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="3b412-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b412-107">Example</span></span>  
 <span data-ttu-id="3b412-108">Poniższy przykład umożliwia znalezienie najniższą kwotę transport dla dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="3b412-108">The following example finds the lowest freight amount for any order.</span></span>  
  
 <span data-ttu-id="3b412-109">Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, dane wyjściowe są: `0.0200`.</span><span class="sxs-lookup"><span data-stu-id="3b412-109">If you run this query against the Northwind sample database, the output is: `0.0200`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="3b412-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b412-110">Example</span></span>  
 <span data-ttu-id="3b412-111">W poniższym przykładzie użyto Min, aby znaleźć `Products` zawierających najniższej cenie jednostkowej w każdej kategorii.</span><span class="sxs-lookup"><span data-stu-id="3b412-111">The following example uses Min to find the `Products` that have the lowest unit price in each category.</span></span> <span data-ttu-id="3b412-112">Dane wyjściowe są rozmieszczone według kategorii.</span><span class="sxs-lookup"><span data-stu-id="3b412-112">The output is arranged by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 <span data-ttu-id="3b412-113">Jeśli poprzednie zapytanie wykonywane przykładowej bazy danych Northwind, wyniki będą wyglądać w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3b412-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Guaraná Fantástica`  
  
 `2`  
  
 `Aniseed Syrup`  
  
 `3`  
  
 `Teatime Chocolate Biscuits`  
  
 `4`  
  
 `Geitost`  
  
 `5`  
  
 `Filo Mix`  
  
 `6`  
  
 `Tourtière`  
  
 `7`  
  
 `Longlife Tofu`  
  
 `8`  
  
 `Konbu`  
  
## <a name="see-also"></a><span data-ttu-id="3b412-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b412-114">See Also</span></span>  
 [<span data-ttu-id="3b412-115">Zapytania zagregowane</span><span class="sxs-lookup"><span data-stu-id="3b412-115">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [<span data-ttu-id="3b412-116">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="3b412-116">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
