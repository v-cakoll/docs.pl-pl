---
title: Odnajdywanie wartości minimalnej w sekwencji numerycznej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
ms.openlocfilehash: d8aee43f13ec92f649b4df20505ac56c336fe07a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793834"
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a><span data-ttu-id="65add-102">Odnajdywanie wartości minimalnej w sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="65add-102">Find the Minimum Value in a Numeric Sequence</span></span>
<span data-ttu-id="65add-103"><xref:System.Linq.Enumerable.Min%2A> Użyj operatora, aby zwrócić minimalną wartość z sekwencji wartości liczbowych.</span><span class="sxs-lookup"><span data-stu-id="65add-103">Use the <xref:System.Linq.Enumerable.Min%2A> operator to return the minimum value from a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65add-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="65add-104">Example</span></span>  
 <span data-ttu-id="65add-105">W poniższym przykładzie znajduje się najniższa cena jednostkowa dowolnego produktu.</span><span class="sxs-lookup"><span data-stu-id="65add-105">The following example finds the lowest unit price of any product.</span></span>  
  
 <span data-ttu-id="65add-106">W przypadku uruchomienia tego zapytania względem przykładowej bazy danych Northwind dane wyjściowe to: `2.5000`.</span><span class="sxs-lookup"><span data-stu-id="65add-106">If you run this query against the Northwind sample database, the output is: `2.5000`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="65add-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="65add-107">Example</span></span>  
 <span data-ttu-id="65add-108">Poniższy przykład umożliwia znalezienie najmniejszej ilości frachtu dla dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="65add-108">The following example finds the lowest freight amount for any order.</span></span>  
  
 <span data-ttu-id="65add-109">W przypadku uruchomienia tego zapytania względem przykładowej bazy danych Northwind dane wyjściowe to: `0.0200`.</span><span class="sxs-lookup"><span data-stu-id="65add-109">If you run this query against the Northwind sample database, the output is: `0.0200`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="65add-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="65add-110">Example</span></span>  
 <span data-ttu-id="65add-111">W poniższym przykładzie jest używane minimum, aby `Products` znaleźć wartość, która ma najniższą cenę jednostkową w każdej kategorii.</span><span class="sxs-lookup"><span data-stu-id="65add-111">The following example uses Min to find the `Products` that have the lowest unit price in each category.</span></span> <span data-ttu-id="65add-112">Dane wyjściowe są uporządkowane według kategorii.</span><span class="sxs-lookup"><span data-stu-id="65add-112">The output is arranged by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 <span data-ttu-id="65add-113">W przypadku uruchomienia poprzedniego zapytania względem przykładowej bazy danych Northwind wyniki będą wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="65add-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="65add-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65add-114">See also</span></span>

- [<span data-ttu-id="65add-115">Zapytania zagregowane</span><span class="sxs-lookup"><span data-stu-id="65add-115">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="65add-116">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="65add-116">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
