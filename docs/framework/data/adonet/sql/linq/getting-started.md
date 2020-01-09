---
title: Wprowadzenie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: 3bff4e9f268e9eac84c244cb58eed8b4384e717d
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634696"
---
# <a name="getting-started"></a><span data-ttu-id="82847-102">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="82847-102">Getting Started</span></span>
<span data-ttu-id="82847-103">Za pomocą [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]można używać technologii LINQ do uzyskiwania dostępu do baz danych SQL tak samo jak w przypadku dostępu do kolekcji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="82847-103">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the LINQ technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="82847-104">Na przykład obiekt `nw` w poniższym kodzie jest tworzony w celu reprezentowania bazy danych `Northwind`, tabela `Customers` jest docelowa, wiersze są filtrowane pod kątem `Customers` z `London`, a do pobrania jest wybierany ciąg dla `CompanyName`.</span><span class="sxs-lookup"><span data-stu-id="82847-104">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="82847-105">Po wykonaniu pętli jest pobierana Kolekcja wartości `CompanyName`.</span><span class="sxs-lookup"><span data-stu-id="82847-105">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="82847-106">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="82847-106">Next Steps</span></span>  
 <span data-ttu-id="82847-107">Aby zapoznać się z dodatkowymi przykładami, w tym wstawianiem i aktualizowaniem, zobacz [co możesz zrobić z LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="82847-107">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="82847-108">Następnie Wypróbuj niektóre instruktaże i samouczki, aby korzystać z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="82847-108">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="82847-109">Zobacz [uczenie się według przewodników](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="82847-109">See [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="82847-110">Na koniec dowiesz się, jak rozpocząć pracę nad własnym [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektem, odczytując [typowe kroki dotyczące korzystania z LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="82847-110">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82847-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82847-111">See also</span></span>

- [<span data-ttu-id="82847-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="82847-112">LINQ to SQL</span></span>](index.md)
- [<span data-ttu-id="82847-113">Wprowadzenie do LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="82847-113">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="82847-114">Wprowadzenie do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82847-114">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="82847-115">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="82847-115">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
