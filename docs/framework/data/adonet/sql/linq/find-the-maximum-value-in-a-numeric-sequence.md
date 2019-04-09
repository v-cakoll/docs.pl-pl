---
title: Odnajdywanie wartości maksymalnej w sekwencji numerycznej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
ms.openlocfilehash: b7a2588b9e5082915dff4d371adff2ad3d232d74
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122762"
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a><span data-ttu-id="7100e-102">Odnajdywanie wartości maksymalnej w sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="7100e-102">Find the Maximum Value in a Numeric Sequence</span></span>
<span data-ttu-id="7100e-103">Użyj <xref:System.Linq.Enumerable.Max%2A> operator, aby znaleźć największą wartość w sekwencji wartości liczbowych.</span><span class="sxs-lookup"><span data-stu-id="7100e-103">Use the <xref:System.Linq.Enumerable.Max%2A> operator to find the highest value in a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7100e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7100e-104">Example</span></span>  
 <span data-ttu-id="7100e-105">Poniższy przykład umożliwia znalezienie Najpóźniejsza data zatrudnienia dla każdego pracownika.</span><span class="sxs-lookup"><span data-stu-id="7100e-105">The following example finds the latest date of hire for any employee.</span></span>  
  
 <span data-ttu-id="7100e-106">Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, dane wyjściowe to: `11/15/1994 12:00:00 AM`.</span><span class="sxs-lookup"><span data-stu-id="7100e-106">If you run this query against the sample Northwind database, the output is: `11/15/1994 12:00:00 AM`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="7100e-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="7100e-107">Example</span></span>  
 <span data-ttu-id="7100e-108">Poniższy przykład umożliwia znalezienie większość jednostek w magazynie dla każdego produktu.</span><span class="sxs-lookup"><span data-stu-id="7100e-108">The following example finds the most units in stock for any product.</span></span>  
  
 <span data-ttu-id="7100e-109">Po uruchomieniu tego przykładu w bazie danych Northwind przykładowe dane wyjściowe to: `125`.</span><span class="sxs-lookup"><span data-stu-id="7100e-109">If you run this example against the sample Northwind database, the output is: `125`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a><span data-ttu-id="7100e-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="7100e-110">Example</span></span>  
 <span data-ttu-id="7100e-111">W poniższym przykładzie użyto Max można znaleźć `Products` mają najwyższą cena jednostkowa w każdej kategorii.</span><span class="sxs-lookup"><span data-stu-id="7100e-111">The following example uses Max to find the `Products` that have the highest unit price in each category.</span></span> <span data-ttu-id="7100e-112">Dane wyjściowe następnie wyświetla wyniki według kategorii.</span><span class="sxs-lookup"><span data-stu-id="7100e-112">The output then lists the results by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 <span data-ttu-id="7100e-113">Jeśli uruchamiasz poprzednie zapytanie względem przykładowej bazy danych Northwind, wyniki będą wyglądać w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7100e-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a><span data-ttu-id="7100e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7100e-114">See also</span></span>

- [<span data-ttu-id="7100e-115">Zapytania zagregowane</span><span class="sxs-lookup"><span data-stu-id="7100e-115">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [<span data-ttu-id="7100e-116">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="7100e-116">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
