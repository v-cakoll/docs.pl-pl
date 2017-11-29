---
title: "Join — Klauzula (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2bb25c9dac8994e7f975539c1d036f0f0d9d239e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="c3e13-102">Join — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3e13-102">Join Clause (Visual Basic)</span></span>
<span data-ttu-id="c3e13-103">Łączy dwie kolekcje do jednej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c3e13-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="c3e13-104">Operacja łączenia jest oparta na zgodności kluczy i używa `Equals` operatora.</span><span class="sxs-lookup"><span data-stu-id="c3e13-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3e13-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3e13-105">Syntax</span></span>  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a><span data-ttu-id="c3e13-106">Części</span><span class="sxs-lookup"><span data-stu-id="c3e13-106">Parts</span></span>  
 `element`  
 <span data-ttu-id="c3e13-107">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c3e13-107">Required.</span></span> <span data-ttu-id="c3e13-108">Zmienna sterująca dla kolekcji jest dołączony.</span><span class="sxs-lookup"><span data-stu-id="c3e13-108">The control variable for the collection being joined.</span></span>  
  
 `collection`  
 <span data-ttu-id="c3e13-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c3e13-109">Required.</span></span> <span data-ttu-id="c3e13-110">Kolekcja do łączenia z tą kolekcją zidentyfikowane po lewej stronie `Join` operatora.</span><span class="sxs-lookup"><span data-stu-id="c3e13-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="c3e13-111">A `Join` klauzuli mogą być zagnieżdżone w innym `Join` klauzuli lub `Group Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c3e13-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>  
  
 `joinClause`  
 <span data-ttu-id="c3e13-112">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c3e13-112">Optional.</span></span> <span data-ttu-id="c3e13-113">Jeden lub więcej dodatkowych `Join` klauzule dalsze uściślenie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="c3e13-113">One or more additional `Join` clauses to further refine the query.</span></span>  
  
 `groupJoinClause`  
 <span data-ttu-id="c3e13-114">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c3e13-114">Optional.</span></span> <span data-ttu-id="c3e13-115">Jeden lub więcej dodatkowych `Group Join` klauzule dalsze uściślenie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="c3e13-115">One or more additional `Group Join` clauses to further refine the query.</span></span>  
  
 <span data-ttu-id="c3e13-116">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="c3e13-116">`key1` `Equals` `key2`</span></span>  
 <span data-ttu-id="c3e13-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c3e13-117">Required.</span></span> <span data-ttu-id="c3e13-118">Określa klucze w kolekcji jest dołączony.</span><span class="sxs-lookup"><span data-stu-id="c3e13-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="c3e13-119">Należy użyć `Equals` operatora, aby porównać klucze z kolekcji jest dołączony.</span><span class="sxs-lookup"><span data-stu-id="c3e13-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="c3e13-120">Warunki sprzężenia można połączyć za pomocą `And` operatora, aby zidentyfikować wielu kluczy.</span><span class="sxs-lookup"><span data-stu-id="c3e13-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="c3e13-121">`key1`musi pochodzić z kolekcji po lewej stronie `Join` operatora.</span><span class="sxs-lookup"><span data-stu-id="c3e13-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="c3e13-122">`key2`musi pochodzić z kolekcji w prawej części `Join` operatora.</span><span class="sxs-lookup"><span data-stu-id="c3e13-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>  
  
 <span data-ttu-id="c3e13-123">Klucze używane w warunek sprzężenia można wyrażeń, które zawierają więcej niż jeden element z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c3e13-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="c3e13-124">Każde wyrażenie klucza może jednak zawierać tylko elementy z jego odpowiednich kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c3e13-124">However, each key expression can contain only items from its respective collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3e13-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3e13-125">Remarks</span></span>  
 <span data-ttu-id="c3e13-126">`Join` Klauzuli łączy dwie kolekcje oparte na zgodności kluczy wartości z kolekcji jest dołączony.</span><span class="sxs-lookup"><span data-stu-id="c3e13-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="c3e13-127">Wynikowa Kolekcja może zawierać dowolną kombinację wartości z kolekcji zidentyfikowane po lewej stronie `Join` operatora i kolekcji objęci `Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c3e13-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="c3e13-128">Zwraca tylko wyniki, dla których warunek określony przez `Equals` operator jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="c3e13-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="c3e13-129">Jest to równoważne `INNER JOIN` w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="c3e13-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>  
  
 <span data-ttu-id="c3e13-130">Można użyć wielu `Join` klauzule zapytanie w celu dołączenia dwóch lub więcej kolekcji do jednej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c3e13-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>  
  
 <span data-ttu-id="c3e13-131">Można wykonywać niejawne sprzężenia połączyć kolekcji bez `Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c3e13-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="c3e13-132">Aby to zrobić, zawierają wiele `In` klauzul w Twojej `From` klauzuli i określ `Where` klauzulę identyfikującą kluczy, które ma być używany w celu utworzenia sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="c3e13-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>  
  
 <span data-ttu-id="c3e13-133">Można użyć `Group Join` klauzuli połączyć kolekcji do jednej kolekcji hierarchicznej.</span><span class="sxs-lookup"><span data-stu-id="c3e13-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="c3e13-134">Przypomina to `LEFT OUTER JOIN` w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="c3e13-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3e13-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="c3e13-135">Example</span></span>  
 <span data-ttu-id="c3e13-136">Poniższy przykład kodu wykonuje sprzężenie niejawne połączyć listę klientów z ich zleceń.</span><span class="sxs-lookup"><span data-stu-id="c3e13-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="c3e13-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="c3e13-137">Example</span></span>  
 <span data-ttu-id="c3e13-138">Poniższy przykład kodu łączy dwie kolekcje przy użyciu `Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c3e13-138">The following code example joins two collections by using the `Join` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]  
  
 <span data-ttu-id="c3e13-139">W tym przykładzie utworzy dane wyjściowe podobne do następującego:</span><span class="sxs-lookup"><span data-stu-id="c3e13-139">This example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a><span data-ttu-id="c3e13-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="c3e13-140">Example</span></span>  
 <span data-ttu-id="c3e13-141">Poniższy przykład kodu łączy dwie kolekcje przy użyciu `Join` klauzuli z dwiema kolumnami klucza.</span><span class="sxs-lookup"><span data-stu-id="c3e13-141">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]  
  
 <span data-ttu-id="c3e13-142">Przykład utworzy dane wyjściowe podobne do następującego:</span><span class="sxs-lookup"><span data-stu-id="c3e13-142">The example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a><span data-ttu-id="c3e13-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3e13-143">See Also</span></span>  
 [<span data-ttu-id="c3e13-144">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3e13-144">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="c3e13-145">Zapytania</span><span class="sxs-lookup"><span data-stu-id="c3e13-145">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="c3e13-146">SELECT — klauzula</span><span class="sxs-lookup"><span data-stu-id="c3e13-146">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="c3e13-147">Klauzula FROM</span><span class="sxs-lookup"><span data-stu-id="c3e13-147">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="c3e13-148">Group Join — klauzula</span><span class="sxs-lookup"><span data-stu-id="c3e13-148">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="c3e13-149">Gdy klauzula</span><span class="sxs-lookup"><span data-stu-id="c3e13-149">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
