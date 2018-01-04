---
title: Wprowadzenie
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
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e05ede0981a066abd72aafa81478d6c84342d18f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started"></a><span data-ttu-id="e296d-102">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="e296d-102">Getting Started</span></span>
<span data-ttu-id="e296d-103">Za pomocą [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], można użyć [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologii SQL dostępu do bazy danych, tak jak będzie można uzyskać dostępu do kolekcji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e296d-103">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="e296d-104">Na przykład `nw` utworzeniu obiektu w poniższym kodzie do reprezentowania `Northwind` bazy danych, `Customers` podlega tabeli, wiersze są filtrowane pod kątem `Customers` z `London`i ciąg `CompanyName` jest zaznaczone do pobrania.</span><span class="sxs-lookup"><span data-stu-id="e296d-104">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="e296d-105">Jeśli pętla jest wykonywana, Kolekcja `CompanyName` są pobierane wartości.</span><span class="sxs-lookup"><span data-stu-id="e296d-105">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="e296d-106">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e296d-106">Next Steps</span></span>  
 <span data-ttu-id="e296d-107">Niektóre dodatkowe przykłady w tym wstawiania i aktualizowania, można znaleźć [co użytkownik może zrobić z LINQ do SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e296d-107">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="e296d-108">Następnie spróbuj niektóre wskazówki i samouczki, aby mieć praktyczne doświadczenie z przy użyciu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e296d-108">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="e296d-109">Zobacz [uczenia przez wskazówki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="e296d-109">See [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="e296d-110">Na koniec, Dowiedz się, jak rozpocząć pracę na własną [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu, odczytując [typowe etapy za pomocą LINQ do SQL](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e296d-110">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e296d-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e296d-111">See Also</span></span>  
 [<span data-ttu-id="e296d-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e296d-112">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="e296d-113">Wprowadzenie do LINQ</span><span class="sxs-lookup"><span data-stu-id="e296d-113">Introduction to LINQ</span></span>](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)  
 [<span data-ttu-id="e296d-114">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e296d-114">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
