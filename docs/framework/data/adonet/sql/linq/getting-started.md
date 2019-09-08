---
title: Wprowadzenie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: bd82b7e83149aaa53cf1b240cb79f8747bccba47
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793916"
---
# <a name="getting-started"></a><span data-ttu-id="5674e-102">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="5674e-102">Getting Started</span></span>
<span data-ttu-id="5674e-103">Korzystając [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]z programu, można [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] uzyskać dostęp do baz danych SQL w taki sam sposób jak w przypadku uzyskania dostępu do kolekcji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="5674e-103">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="5674e-104">Na przykład `nw` obiekt w poniższym kodzie jest tworzony, aby `Northwind` reprezentować bazę danych, `Customers` tabela `Customers` jest docelowa, wiersze są filtrowane z `London`, a ciąg dla `CompanyName` jest zaznaczony do pobrania.</span><span class="sxs-lookup"><span data-stu-id="5674e-104">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="5674e-105">Po wykonaniu pętli jest pobierana kolekcja `CompanyName` wartości.</span><span class="sxs-lookup"><span data-stu-id="5674e-105">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="5674e-106">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5674e-106">Next Steps</span></span>  
 <span data-ttu-id="5674e-107">Aby zapoznać się z dodatkowymi przykładami, w tym wstawianiem i aktualizowaniem, zobacz [co możesz zrobić z LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5674e-107">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="5674e-108">Następnie Wypróbuj niektóre instruktaże i samouczki, aby korzystać z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programu.</span><span class="sxs-lookup"><span data-stu-id="5674e-108">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="5674e-109">Zobacz [uczenie się według przewodników](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="5674e-109">See [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="5674e-110">Na koniec dowiesz się, jak rozpocząć pracę nad [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] własnym projektem, odczytując [typowe kroki dotyczące korzystania z LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5674e-110">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5674e-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5674e-111">See also</span></span>

- [<span data-ttu-id="5674e-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5674e-112">LINQ to SQL</span></span>](index.md)
- [<span data-ttu-id="5674e-113">Wprowadzenie do LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="5674e-113">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="5674e-114">Wprowadzenie do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5674e-114">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="5674e-115">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5674e-115">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
