---
title: Wprowadzenie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: 7ddecf910b5f76fdb5e75300118fa0a063269116
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556405"
---
# <a name="getting-started"></a><span data-ttu-id="dd973-102">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="dd973-102">Getting Started</span></span>
<span data-ttu-id="dd973-103">Za pomocą [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], możesz użyć [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologii SQL dostęp do bazy danych tak, jak dostęp do kolekcji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="dd973-103">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="dd973-104">Na przykład `nw` obiekt w poniższym kodzie zostanie utworzony do reprezentowania `Northwind` bazy danych, `Customers` podlega tabeli, wiersze zostały przefiltrowane pod kątem `Customers` z `London`i ciąg `CompanyName` jest zaznaczone do pobrania.</span><span class="sxs-lookup"><span data-stu-id="dd973-104">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="dd973-105">Po wykonaniu pętli, pobieranie `CompanyName` wartości są pobierane.</span><span class="sxs-lookup"><span data-stu-id="dd973-105">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="dd973-106">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="dd973-106">Next Steps</span></span>  
 <span data-ttu-id="dd973-107">Niektóre dodatkowe przykłady, w tym wstawiania i aktualizowania, można znaleźć [co użytkownik może zrobić za pomocą LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="dd973-107">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="dd973-108">Następnie spróbuj wykonać niektóre wskazówki i samouczki ułatwiające praktyczne doświadczenie korzystania z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dd973-108">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="dd973-109">Zobacz [nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="dd973-109">See [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="dd973-110">Ponadto Dowiedz się, jak rozpocząć pracę na własną rękę [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu, czytając [typowe etapy za pomocą LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="dd973-110">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd973-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd973-111">See also</span></span>
- [<span data-ttu-id="dd973-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="dd973-112">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="dd973-113">Wprowadzenie do LINQ</span><span class="sxs-lookup"><span data-stu-id="dd973-113">Introduction to LINQ</span></span>](https://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)
- [<span data-ttu-id="dd973-114">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="dd973-114">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
