---
title: "Znajdź wartość maksymalna liczbowe sekwencji"
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
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 387fe8db55da337b970bbac0e6e046b43433b482
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a><span data-ttu-id="3e08a-102">Znajdź wartość maksymalna liczbowe sekwencji</span><span class="sxs-lookup"><span data-stu-id="3e08a-102">Find the Maximum Value in a Numeric Sequence</span></span>
<span data-ttu-id="3e08a-103">Użyj <xref:System.Linq.Enumerable.Max%2A> operatora, aby znaleźć największą wartość w sekwencji wartości liczbowych.</span><span class="sxs-lookup"><span data-stu-id="3e08a-103">Use the <xref:System.Linq.Enumerable.Max%2A> operator to find the highest value in a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e08a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e08a-104">Example</span></span>  
 <span data-ttu-id="3e08a-105">Poniższy przykład wyszukuje najnowsze Data zatrudnienia dowolnego pracownika.</span><span class="sxs-lookup"><span data-stu-id="3e08a-105">The following example finds the latest date of hire for any employee.</span></span>  
  
 <span data-ttu-id="3e08a-106">Po uruchomieniu tej kwerendy w bazie danych Northwind przykładowe dane wyjściowe są: `11/15/1994 12:00:00 AM`.</span><span class="sxs-lookup"><span data-stu-id="3e08a-106">If you run this query against the sample Northwind database, the output is: `11/15/1994 12:00:00 AM`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="3e08a-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e08a-107">Example</span></span>  
 <span data-ttu-id="3e08a-108">Poniższy przykład umożliwia znalezienie większości jednostki w magazynie dla każdego produktu.</span><span class="sxs-lookup"><span data-stu-id="3e08a-108">The following example finds the most units in stock for any product.</span></span>  
  
 <span data-ttu-id="3e08a-109">Jeśli wykonywane są w tym przykładzie przykładowej bazy danych Northwind, dane wyjściowe są: `125`.</span><span class="sxs-lookup"><span data-stu-id="3e08a-109">If you run this example against the sample Northwind database, the output is: `125`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a><span data-ttu-id="3e08a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e08a-110">Example</span></span>  
 <span data-ttu-id="3e08a-111">W poniższym przykładzie użyto Max można znaleźć `Products` zawierających najwyższej cenie jednostkowej w każdej kategorii.</span><span class="sxs-lookup"><span data-stu-id="3e08a-111">The following example uses Max to find the `Products` that have the highest unit price in each category.</span></span> <span data-ttu-id="3e08a-112">Dane wyjściowe następnie wyświetla wyniki według kategorii.</span><span class="sxs-lookup"><span data-stu-id="3e08a-112">The output then lists the results by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 <span data-ttu-id="3e08a-113">Jeśli poprzednie zapytanie wykonywane przykładowej bazy danych Northwind, wyniki będą wyglądać w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3e08a-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3e08a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e08a-114">See Also</span></span>  
 [<span data-ttu-id="3e08a-115">Zapytania zagregowane</span><span class="sxs-lookup"><span data-stu-id="3e08a-115">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [<span data-ttu-id="3e08a-116">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="3e08a-116">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
