---
title: "Liczba liczba elementów w sekwencji"
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
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f6d1403384b8725720abbe9a81f98cbbfdb9c6e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="bdd1d-102">Liczba liczba elementów w sekwencji</span><span class="sxs-lookup"><span data-stu-id="bdd1d-102">Count the Number of Elements in a Sequence</span></span>
<span data-ttu-id="bdd1d-103">Użyj <xref:System.Linq.Enumerable.Count%2A> operatora, aby określić liczbę elementów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="bdd1d-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="bdd1d-104">Wykonywanie tej kwerendy względem przykładowej bazy danych Northwind generuje dane wyjściowe z `91`.</span><span class="sxs-lookup"><span data-stu-id="bdd1d-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdd1d-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="bdd1d-105">Example</span></span>  
 <span data-ttu-id="bdd1d-106">Poniższy przykład zlicza `Customers` w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="bdd1d-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="bdd1d-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="bdd1d-107">Example</span></span>  
 <span data-ttu-id="bdd1d-108">Poniższy przykład zlicza produkty w bazie danych, które nie zostały anulowane.</span><span class="sxs-lookup"><span data-stu-id="bdd1d-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="bdd1d-109">Uruchomione w tym przykładzie przed przykładowej bazy danych Northwind generuje dane wyjściowe z `69`.</span><span class="sxs-lookup"><span data-stu-id="bdd1d-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="bdd1d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bdd1d-110">See Also</span></span>  
 [<span data-ttu-id="bdd1d-111">Zapytania zagregowane</span><span class="sxs-lookup"><span data-stu-id="bdd1d-111">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [<span data-ttu-id="bdd1d-112">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="bdd1d-112">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
