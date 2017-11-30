---
title: "Przykłady zapytań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e7d7a0a1f641603887675ed0c1faebd5c06b273
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="query-examples"></a><span data-ttu-id="13c9e-102">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="13c9e-102">Query Examples</span></span>
<span data-ttu-id="13c9e-103">Ta sekcja zawiera [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] i C# przykłady typowych [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="13c9e-103">This section provides [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# examples of typical [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries.</span></span> <span data-ttu-id="13c9e-104">Deweloperzy przy użyciu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] znajduje się dużo więcej przykładów w przykładowe rozwiązanie dostępne w sekcji przykładów.</span><span class="sxs-lookup"><span data-stu-id="13c9e-104">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can find many more examples in a sample solution available in the Samples section.</span></span> <span data-ttu-id="13c9e-105">Aby uzyskać więcej informacji, zobacz [przykłady](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).</span><span class="sxs-lookup"><span data-stu-id="13c9e-105">For more information, see [Samples](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="13c9e-106">*DB* jest często używana w przykładach kodu w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="13c9e-106">*db* is often used in code examples in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation.</span></span> <span data-ttu-id="13c9e-107">*DB* zakłada, że wystąpienie *Northwind* klasy, która dziedziczy <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="13c9e-107">*db* is assumed to be an instance of a *Northwind* class, which inherits from <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13c9e-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="13c9e-108">In This Section</span></span>  
 [<span data-ttu-id="13c9e-109">Zapytania zagregowane</span><span class="sxs-lookup"><span data-stu-id="13c9e-109">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 <span data-ttu-id="13c9e-110">Informacje dotyczące używania <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, itd.</span><span class="sxs-lookup"><span data-stu-id="13c9e-110">Describes how to use <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, and so forth.</span></span>  
  
 [<span data-ttu-id="13c9e-111">Zwraca pierwszy Element w sekwencji</span><span class="sxs-lookup"><span data-stu-id="13c9e-111">Return the First Element in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-first-element-in-a-sequence.md)  
 <span data-ttu-id="13c9e-112">Przykłady użycia <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="13c9e-112">Provides examples of using <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
 [<span data-ttu-id="13c9e-113">Zwracanym lub Pomiń elementy w sekwencji</span><span class="sxs-lookup"><span data-stu-id="13c9e-113">Return Or Skip Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 <span data-ttu-id="13c9e-114">Przykłady użycia <xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="13c9e-114">Provides examples of using <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span>  
  
 [<span data-ttu-id="13c9e-115">Sortowanie elementów w sekwencji</span><span class="sxs-lookup"><span data-stu-id="13c9e-115">Sort Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sort-elements-in-a-sequence.md)  
 <span data-ttu-id="13c9e-116">Przykłady użycia <xref:System.Linq.Enumerable.OrderBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="13c9e-116">Provides examples of using <xref:System.Linq.Enumerable.OrderBy%2A>.</span></span>  
  
 [<span data-ttu-id="13c9e-117">Grupowanie elementów w sekwencji</span><span class="sxs-lookup"><span data-stu-id="13c9e-117">Group Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/group-elements-in-a-sequence.md)  
 <span data-ttu-id="13c9e-118">Przykłady użycia <xref:System.Linq.Enumerable.GroupBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="13c9e-118">Provides examples of using <xref:System.Linq.Enumerable.GroupBy%2A>.</span></span>  
  
 [<span data-ttu-id="13c9e-119">Eliminowanie zduplikowane elementy z sekwencji</span><span class="sxs-lookup"><span data-stu-id="13c9e-119">Eliminate Duplicate Elements from a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/eliminate-duplicate-elements-from-a-sequence.md)  
 <span data-ttu-id="13c9e-120">Przykłady użycia <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="13c9e-120">Provides examples of using <xref:System.Linq.Enumerable.Distinct%2A>.</span></span>  
  
 [<span data-ttu-id="13c9e-121">Określić, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek</span><span class="sxs-lookup"><span data-stu-id="13c9e-121">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 <span data-ttu-id="13c9e-122">Przykłady użycia <xref:System.Linq.Enumerable.All%2A> i <xref:System.Linq.Enumerable.Any%2A>.</span><span class="sxs-lookup"><span data-stu-id="13c9e-122">Provides examples of using <xref:System.Linq.Enumerable.All%2A> and <xref:System.Linq.Enumerable.Any%2A>.</span></span>  
  
 [<span data-ttu-id="13c9e-123">Łączenie dwóch sekwencji</span><span class="sxs-lookup"><span data-stu-id="13c9e-123">Concatenate Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 <span data-ttu-id="13c9e-124">Przykłady użycia <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="13c9e-124">Provides examples of using <xref:System.Linq.Enumerable.Concat%2A>.</span></span>  
  
 [<span data-ttu-id="13c9e-125">Zwraca różnicy pomiędzy dwoma sekwencji</span><span class="sxs-lookup"><span data-stu-id="13c9e-125">Return the Set Difference Between Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 <span data-ttu-id="13c9e-126">Przykłady użycia <xref:System.Linq.Enumerable.Except%2A>.</span><span class="sxs-lookup"><span data-stu-id="13c9e-126">Provides examples of using <xref:System.Linq.Enumerable.Except%2A>.</span></span>  
  
 [<span data-ttu-id="13c9e-127">Zwraca część wspólną dwóch sekwencji zestawu</span><span class="sxs-lookup"><span data-stu-id="13c9e-127">Return the Set Intersection of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 <span data-ttu-id="13c9e-128">Przykłady użycia <xref:System.Linq.Enumerable.Intersect%2A>.</span><span class="sxs-lookup"><span data-stu-id="13c9e-128">Provides examples of using <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 [<span data-ttu-id="13c9e-129">Zwraca złożenie dwóch sekwencji zestawu</span><span class="sxs-lookup"><span data-stu-id="13c9e-129">Return the Set Union of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)  
 <span data-ttu-id="13c9e-130">Przykłady użycia <xref:System.Linq.Enumerable.Union%2A>.</span><span class="sxs-lookup"><span data-stu-id="13c9e-130">Provides examples of using <xref:System.Linq.Enumerable.Union%2A>.</span></span>  
  
 [<span data-ttu-id="13c9e-131">Konwertowanie sekwencji do tablicy</span><span class="sxs-lookup"><span data-stu-id="13c9e-131">Convert a Sequence to an Array</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-an-array.md)  
 <span data-ttu-id="13c9e-132">Przykłady użycia <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="13c9e-132">Provides examples of using <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
 [<span data-ttu-id="13c9e-133">Konwertuj sekwencji do listy ogólnej</span><span class="sxs-lookup"><span data-stu-id="13c9e-133">Convert a Sequence to a Generic List</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-a-generic-list.md)  
 <span data-ttu-id="13c9e-134">Przykłady użycia <xref:System.Linq.Enumerable.ToList%2A>.</span><span class="sxs-lookup"><span data-stu-id="13c9e-134">Provides examples of using <xref:System.Linq.Enumerable.ToList%2A>.</span></span>  
  
 [<span data-ttu-id="13c9e-135">Przekonwertować typem rodzajowym interfejsem IEnumerable</span><span class="sxs-lookup"><span data-stu-id="13c9e-135">Convert a Type to a Generic IEnumerable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md)  
 <span data-ttu-id="13c9e-136">Przykłady użycia <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="13c9e-136">Provides examples of using <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span></span>  
  
 [<span data-ttu-id="13c9e-137">Sformułować sprzężenia i iloczyn wektorowy zapytania</span><span class="sxs-lookup"><span data-stu-id="13c9e-137">Formulate Joins and Cross-Product Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
 <span data-ttu-id="13c9e-138">Przykłady użycia klucza obcego nawigacji w `from`, `where`, i `select` klauzul.</span><span class="sxs-lookup"><span data-stu-id="13c9e-138">Provides examples of using foreign-key navigation in the `from`, `where`, and `select` clauses.</span></span>  
  
 [<span data-ttu-id="13c9e-139">Sformułować projekcje</span><span class="sxs-lookup"><span data-stu-id="13c9e-139">Formulate Projections</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-projections.md)  
 <span data-ttu-id="13c9e-140">Przykłady łączenie `select` z innymi funkcjami (na przykład *typy anonimowe*) do formularza projekcje zapytania.</span><span class="sxs-lookup"><span data-stu-id="13c9e-140">Provides examples of combining `select` with other features (for example, *anonymous types*) to form query projections.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="13c9e-141">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="13c9e-141">Related Sections</span></span>  
 [<span data-ttu-id="13c9e-142">Operatory standardowe zapytań — omówienie</span><span class="sxs-lookup"><span data-stu-id="13c9e-142">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 <span data-ttu-id="13c9e-143">Wyjaśnia pojęcie standardowych operatorów zapytań.</span><span class="sxs-lookup"><span data-stu-id="13c9e-143">Explains the concept of standard query operators.</span></span>  
  
 [<span data-ttu-id="13c9e-144">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="13c9e-144">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="13c9e-145">Wyjaśniono, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] używa pojęcia, które są stosowane do zapytania.</span><span class="sxs-lookup"><span data-stu-id="13c9e-145">Explains how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uses concepts that apply to queries.</span></span>  
  
 [<span data-ttu-id="13c9e-146">Przewodnik programowania w języku</span><span class="sxs-lookup"><span data-stu-id="13c9e-146">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="13c9e-147">Udostępnia portal do tematów dotyczących programowania pojęć związanych z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="13c9e-147">Provides a portal to topics that explain programming concepts related to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
