---
title: Zapytania zagregowane
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: ed8624c47ca8e68646f176ff91b63577d64b6d1f
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56094129"
---
# <a name="aggregate-queries"></a><span data-ttu-id="95832-102">Zapytania zagregowane</span><span class="sxs-lookup"><span data-stu-id="95832-102">Aggregate Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="95832-103">obsługuje `Average`, `Count`, `Max`, `Min`, i `Sum` operatorów agregacji.</span><span class="sxs-lookup"><span data-stu-id="95832-103">supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="95832-104">Należy zwrócić uwagę na następujące cechy operatory agregacji w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="95832-104">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
-   <span data-ttu-id="95832-105">Zapytania zagregowane są wykonywane natychmiast.</span><span class="sxs-lookup"><span data-stu-id="95832-105">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="95832-106">Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="95832-106">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
-   <span data-ttu-id="95832-107">Zapytania zagregowane zwykle zwracają liczbę zamiast kolekcji.</span><span class="sxs-lookup"><span data-stu-id="95832-107">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="95832-108">Aby uzyskać więcej informacji, zobacz [operacje agregacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="95832-108">For more information, see [Aggregation Operations](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span></span>  
  
-   <span data-ttu-id="95832-109">Nie można wywołać wartości zagregowanych dla typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="95832-109">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="95832-110">W przykładach w następujących tematach pochodzi z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="95832-110">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="95832-111">Aby uzyskać więcej informacji, zobacz [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="95832-111">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="95832-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="95832-112">In This Section</span></span>  
 [<span data-ttu-id="95832-113">Zwracanie średniej wartości z sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="95832-113">Return the Average Value From a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="95832-114">Pokazuje sposób użycia <xref:System.Linq.Enumerable.Average%2A> operatora.</span><span class="sxs-lookup"><span data-stu-id="95832-114">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="95832-115">Licznik liczby elementów w sekwencji</span><span class="sxs-lookup"><span data-stu-id="95832-115">Count the Number of Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="95832-116">Pokazuje sposób użycia <xref:System.Linq.Enumerable.Count%2A> operatora.</span><span class="sxs-lookup"><span data-stu-id="95832-116">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="95832-117">Odnajdywanie wartości maksymalnej w sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="95832-117">Find the Maximum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="95832-118">Pokazuje sposób użycia <xref:System.Linq.Enumerable.Max%2A> operatora.</span><span class="sxs-lookup"><span data-stu-id="95832-118">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="95832-119">Odnajdywanie wartości minimalnej w sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="95832-119">Find the Minimum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="95832-120">Pokazuje sposób użycia <xref:System.Linq.Enumerable.Min%2A> operatora.</span><span class="sxs-lookup"><span data-stu-id="95832-120">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="95832-121">Obliczanie sumy wartości w sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="95832-121">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="95832-122">Pokazuje sposób użycia <xref:System.Linq.Enumerable.Sum%2A> operatora.</span><span class="sxs-lookup"><span data-stu-id="95832-122">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="95832-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="95832-123">Related Sections</span></span>  
 [<span data-ttu-id="95832-124">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="95832-124">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="95832-125">Zawiera łącza do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania w języku Visual Basic i C#.</span><span class="sxs-lookup"><span data-stu-id="95832-125">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="95832-126">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="95832-126">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="95832-127">Zawiera łącza do tematów, które opisują pojęć dotyczących projektowania [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytania w programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="95832-127">Provides links to topics that explain concepts for designing [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="95832-128">Wprowadzenie do zapytań LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="95832-128">Introduction to LINQ Queries (C#)</span></span>](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="95832-129">Wyjaśnia, jak działa zapytania w [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="95832-129">Explains how queries work in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>
