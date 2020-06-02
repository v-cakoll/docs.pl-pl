---
title: Wprowadzenie
description: W tym przykładowym kodzie Rozpocznij korzystanie z LINQ to SQL, aby używać technologii LINQ do uzyskiwania dostępu do baz danych SQL tak samo jak w przypadku dostępu do kolekcji w pamięci.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: a46c42e917bdab0d32ee594bbcd604ee9e3d26bc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286420"
---
# <a name="getting-started"></a><span data-ttu-id="24fa7-103">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="24fa7-103">Getting Started</span></span>
<span data-ttu-id="24fa7-104">Korzystając z programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , można uzyskać dostęp do baz danych SQL przy użyciu technologii LINQ tak samo jak w przypadku dostępu do kolekcji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="24fa7-104">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the LINQ technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="24fa7-105">Na przykład `nw` obiekt w poniższym kodzie jest tworzony, aby reprezentować `Northwind` bazę danych, `Customers` tabela jest docelowa, wiersze są filtrowane dla `Customers` z `London` , a ciąg dla `CompanyName` jest wybierany do pobrania.</span><span class="sxs-lookup"><span data-stu-id="24fa7-105">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="24fa7-106">Po wykonaniu pętli `CompanyName` jest pobierana Kolekcja wartości.</span><span class="sxs-lookup"><span data-stu-id="24fa7-106">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="24fa7-107">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="24fa7-107">Next Steps</span></span>  
 <span data-ttu-id="24fa7-108">Aby zapoznać się z dodatkowymi przykładami, w tym wstawianiem i aktualizowaniem, zobacz [co możesz zrobić z LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="24fa7-108">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="24fa7-109">Następnie Wypróbuj niektóre instruktaże i samouczki, aby korzystać z programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="24fa7-109">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="24fa7-110">Zobacz [uczenie się według przewodników](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="24fa7-110">See [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="24fa7-111">Na koniec dowiesz się, jak rozpocząć pracę nad własnym [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektem, odczytując [typowe kroki dotyczące korzystania z LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="24fa7-111">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24fa7-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24fa7-112">See also</span></span>

- [<span data-ttu-id="24fa7-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="24fa7-113">LINQ to SQL</span></span>](index.md)
- [<span data-ttu-id="24fa7-114">Wprowadzenie do LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="24fa7-114">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="24fa7-115">Wprowadzenie do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24fa7-115">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="24fa7-116">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="24fa7-116">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
