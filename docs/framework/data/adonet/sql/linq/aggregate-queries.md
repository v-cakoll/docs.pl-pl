---
title: Zapytania zagregowane
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: b7b38306903313825056c02fc3c3fb8c98e07e17
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964122"
---
# <a name="aggregate-queries"></a><span data-ttu-id="9facf-102">Zapytania zagregowane</span><span class="sxs-lookup"><span data-stu-id="9facf-102">Aggregate Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9facf-103">`Average`obsługuje operatory, `Count`, `Max`, `Min`i agregacji.`Sum`</span><span class="sxs-lookup"><span data-stu-id="9facf-103">supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="9facf-104">Zwróć uwagę na następujące cechy agregacji operatorów [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]w:</span><span class="sxs-lookup"><span data-stu-id="9facf-104">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="9facf-105">Zapytania agregujące są wykonywane natychmiastowo.</span><span class="sxs-lookup"><span data-stu-id="9facf-105">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="9facf-106">Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQC#()](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="9facf-106">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
- <span data-ttu-id="9facf-107">Zapytania agregujące zwykle zwracają liczbę zamiast kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9facf-107">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="9facf-108">Aby uzyskać więcej informacji, zobacz [operacje agregacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="9facf-108">For more information, see [Aggregation Operations](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span></span>  
  
- <span data-ttu-id="9facf-109">Nie można wywoływać agregacji dla typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="9facf-109">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="9facf-110">Przykłady w poniższych tematach pochodzą z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="9facf-110">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="9facf-111">Aby uzyskać więcej informacji, zobacz [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="9facf-111">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9facf-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9facf-112">In This Section</span></span>  
 [<span data-ttu-id="9facf-113">Zwracanie średniej wartości z sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="9facf-113">Return the Average Value From a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="9facf-114">Pokazuje, <xref:System.Linq.Enumerable.Average%2A> jak używać operatora.</span><span class="sxs-lookup"><span data-stu-id="9facf-114">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="9facf-115">Licznik liczby elementów w sekwencji</span><span class="sxs-lookup"><span data-stu-id="9facf-115">Count the Number of Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="9facf-116">Pokazuje, <xref:System.Linq.Enumerable.Count%2A> jak używać operatora.</span><span class="sxs-lookup"><span data-stu-id="9facf-116">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="9facf-117">Odnajdywanie wartości maksymalnej w sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="9facf-117">Find the Maximum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="9facf-118">Pokazuje, <xref:System.Linq.Enumerable.Max%2A> jak używać operatora.</span><span class="sxs-lookup"><span data-stu-id="9facf-118">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="9facf-119">Odnajdywanie wartości minimalnej w sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="9facf-119">Find the Minimum Value in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="9facf-120">Pokazuje, <xref:System.Linq.Enumerable.Min%2A> jak używać operatora.</span><span class="sxs-lookup"><span data-stu-id="9facf-120">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="9facf-121">Obliczanie sumy wartości w sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="9facf-121">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="9facf-122">Pokazuje, <xref:System.Linq.Enumerable.Sum%2A> jak używać operatora.</span><span class="sxs-lookup"><span data-stu-id="9facf-122">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9facf-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="9facf-123">Related Sections</span></span>  
 [<span data-ttu-id="9facf-124">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="9facf-124">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="9facf-125">Oferuje linki do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytań w Visual Basic i C#.</span><span class="sxs-lookup"><span data-stu-id="9facf-125">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="9facf-126">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="9facf-126">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="9facf-127">Zawiera łącza do tematów objaśniających koncepcje projektowania [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytań w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programie.</span><span class="sxs-lookup"><span data-stu-id="9facf-127">Provides links to topics that explain concepts for designing [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="9facf-128">Wprowadzenie do zapytań LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="9facf-128">Introduction to LINQ Queries (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="9facf-129">Wyjaśnia, w [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]jaki sposób zapytania działają.</span><span class="sxs-lookup"><span data-stu-id="9facf-129">Explains how queries work in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>
