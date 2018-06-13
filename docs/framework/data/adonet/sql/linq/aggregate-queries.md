---
title: Zapytania zagregowane
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: e4d5e0a9dc1ffb0bf1857fee788d46947f3901d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358846"
---
# <a name="aggregate-queries"></a><span data-ttu-id="99d63-102">Zapytania zagregowane</span><span class="sxs-lookup"><span data-stu-id="99d63-102">Aggregate Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="99d63-103"> obsługuje `Average`, `Count`, `Max`, `Min`, i `Sum` operatorów agregacji.</span><span class="sxs-lookup"><span data-stu-id="99d63-103"> supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="99d63-104">Należy zauważyć następujące właściwości operatorów agregacji w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="99d63-104">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
-   <span data-ttu-id="99d63-105">Zapytania agregujące są wykonywane natychmiast.</span><span class="sxs-lookup"><span data-stu-id="99d63-105">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="99d63-106">Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="99d63-106">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
-   <span data-ttu-id="99d63-107">Zapytania agregujące zwracają zazwyczaj numer zamiast kolekcji.</span><span class="sxs-lookup"><span data-stu-id="99d63-107">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="99d63-108">Aby uzyskać więcej informacji, zobacz [operacje agregacji](http://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).</span><span class="sxs-lookup"><span data-stu-id="99d63-108">For more information, see [Aggregation Operations](http://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).</span></span>  
  
-   <span data-ttu-id="99d63-109">Nie można wywołać wartości zagregowanych dla typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="99d63-109">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="99d63-110">Przykłady w następujących tematach pochodzi z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="99d63-110">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="99d63-111">Aby uzyskać więcej informacji, zobacz [pobieranie przykładowe bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="99d63-111">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="99d63-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="99d63-112">In This Section</span></span>  
 [<span data-ttu-id="99d63-113">Zwracanie średniej wartości z sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="99d63-113">Return the Average Value From a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="99d63-114">Pokazuje, jak używać <xref:System.Linq.Enumerable.Average%2A> operatora.</span><span class="sxs-lookup"><span data-stu-id="99d63-114">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="99d63-115">Licznik liczby elementów w sekwencji</span><span class="sxs-lookup"><span data-stu-id="99d63-115">Count the Number of Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="99d63-116">Pokazuje, jak używać <xref:System.Linq.Enumerable.Count%2A> operatora.</span><span class="sxs-lookup"><span data-stu-id="99d63-116">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="99d63-117">Odnajdywanie wartości maksymalnej w sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="99d63-117">Find the Maximum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="99d63-118">Pokazuje, jak używać <xref:System.Linq.Enumerable.Max%2A> operatora.</span><span class="sxs-lookup"><span data-stu-id="99d63-118">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="99d63-119">Odnajdywanie wartości minimalnej w sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="99d63-119">Find the Minimum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="99d63-120">Pokazuje, jak używać <xref:System.Linq.Enumerable.Min%2A> operatora.</span><span class="sxs-lookup"><span data-stu-id="99d63-120">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="99d63-121">Obliczanie sumy wartości w sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="99d63-121">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="99d63-122">Pokazuje, jak używać <xref:System.Linq.Enumerable.Sum%2A> operatora.</span><span class="sxs-lookup"><span data-stu-id="99d63-122">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="99d63-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="99d63-123">Related Sections</span></span>  
 [<span data-ttu-id="99d63-124">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="99d63-124">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="99d63-125">Zawiera łącza do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania w Visual Basic i C#.</span><span class="sxs-lookup"><span data-stu-id="99d63-125">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="99d63-126">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="99d63-126">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="99d63-127">Zawiera łącza do tematów, które opisano pojęcia związane z projektowaniem [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytania w programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99d63-127">Provides links to topics that explain concepts for designing [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="99d63-128">Wprowadzenie do kwerend LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="99d63-128">Introduction to LINQ Queries (C#)</span></span>](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="99d63-129">Objaśniono, w jaki sposób zapytań [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99d63-129">Explains how queries work in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>
