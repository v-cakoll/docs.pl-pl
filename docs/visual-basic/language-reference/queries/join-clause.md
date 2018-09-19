---
title: Join — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: b1551583079c66d1bf5f6963a42d5d24e518fff3
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003324"
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="9aad1-102">Join — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9aad1-102">Join Clause (Visual Basic)</span></span>
<span data-ttu-id="9aad1-103">Łączy dwie kolekcje w jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="9aad1-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="9aad1-104">Operacja łączenia jest oparta na zgodności kluczy i używa `Equals` operatora.</span><span class="sxs-lookup"><span data-stu-id="9aad1-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aad1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9aad1-105">Syntax</span></span>  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a><span data-ttu-id="9aad1-106">Części</span><span class="sxs-lookup"><span data-stu-id="9aad1-106">Parts</span></span>  
 `element`  
 <span data-ttu-id="9aad1-107">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="9aad1-107">Required.</span></span> <span data-ttu-id="9aad1-108">Zmienna sterująca dla kolekcji jest dołączony.</span><span class="sxs-lookup"><span data-stu-id="9aad1-108">The control variable for the collection being joined.</span></span>  
  
 `collection`  
 <span data-ttu-id="9aad1-109">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="9aad1-109">Required.</span></span> <span data-ttu-id="9aad1-110">Kolekcja do łączenia z tą kolekcją identyfikowane w lewej części `Join` operatora.</span><span class="sxs-lookup"><span data-stu-id="9aad1-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="9aad1-111">A `Join` klauzuli może być zagnieżdżona w innej `Join` klauzuli lub `Group Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9aad1-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>  
  
 `joinClause`  
 <span data-ttu-id="9aad1-112">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="9aad1-112">Optional.</span></span> <span data-ttu-id="9aad1-113">Jeden lub więcej dodatkowych `Join` klauzul, aby jeszcze bardziej zawęzić zapytanie.</span><span class="sxs-lookup"><span data-stu-id="9aad1-113">One or more additional `Join` clauses to further refine the query.</span></span>  
  
 `groupJoinClause`  
 <span data-ttu-id="9aad1-114">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="9aad1-114">Optional.</span></span> <span data-ttu-id="9aad1-115">Jeden lub więcej dodatkowych `Group Join` klauzul, aby jeszcze bardziej zawęzić zapytanie.</span><span class="sxs-lookup"><span data-stu-id="9aad1-115">One or more additional `Group Join` clauses to further refine the query.</span></span>  
  
 <span data-ttu-id="9aad1-116">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="9aad1-116">`key1` `Equals` `key2`</span></span>  
 <span data-ttu-id="9aad1-117">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="9aad1-117">Required.</span></span> <span data-ttu-id="9aad1-118">Określa klucze dla kolekcji jest dołączony.</span><span class="sxs-lookup"><span data-stu-id="9aad1-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="9aad1-119">Należy użyć `Equals` operatora do porównywania kluczy z kolekcji jest dołączony.</span><span class="sxs-lookup"><span data-stu-id="9aad1-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="9aad1-120">Warunki sprzężenia można połączyć za pomocą `And` operatora, aby zidentyfikować wielu kluczy.</span><span class="sxs-lookup"><span data-stu-id="9aad1-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="9aad1-121">`key1` musi mieć długość od kolekcji w lewej części `Join` operatora.</span><span class="sxs-lookup"><span data-stu-id="9aad1-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="9aad1-122">`key2` musi mieć długość od kolekcji na prawej krawędzi `Join` operatora.</span><span class="sxs-lookup"><span data-stu-id="9aad1-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>  
  
 <span data-ttu-id="9aad1-123">Klucze używane w warunek sprzężenia, może być wyrażeń, które zawierają więcej niż jeden element z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9aad1-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="9aad1-124">Jednak każde wyrażenie kluczy może zawierać tylko elementy z jego odpowiednich kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9aad1-124">However, each key expression can contain only items from its respective collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9aad1-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9aad1-125">Remarks</span></span>  
 <span data-ttu-id="9aad1-126">`Join` Klauzuli łączy dwie kolekcje, w oparciu o dopasowanie wartości kluczy z kolekcji jest dołączony.</span><span class="sxs-lookup"><span data-stu-id="9aad1-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="9aad1-127">Wynikowy Kolekcja może zawierać dowolną kombinację wartości z kolekcji identyfikowane w lewej części `Join` operatora i kolekcji w `Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9aad1-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="9aad1-128">Kwerenda będzie zwracać tylko wyniki, dla których warunek określony przez `Equals` operator jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="9aad1-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="9aad1-129">Jest to równoważne `INNER JOIN` w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="9aad1-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>  
  
 <span data-ttu-id="9aad1-130">Możesz użyć wielu `Join` klauzul zapytania do dołączenia do co najmniej dwóch kolekcje w jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="9aad1-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>  
  
 <span data-ttu-id="9aad1-131">Można wykonać sprzężenie niejawne połączyć kolekcji bez `Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9aad1-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="9aad1-132">Aby to zrobić, należy dołączyć wiele `In` klauzul swoje `From` klauzuli i określ `Where` klauzulę identyfikującą klucze, które chcesz użyć w celu utworzenia sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="9aad1-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>  
  
 <span data-ttu-id="9aad1-133">Możesz użyć `Group Join` klauzuli połączyć kolekcje w jedną hierarchiczną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="9aad1-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="9aad1-134">Formuła ta przypomina `LEFT OUTER JOIN` w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="9aad1-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9aad1-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="9aad1-135">Example</span></span>  
 <span data-ttu-id="9aad1-136">Poniższy kod wykonuje sprzężenie niejawne połączyć listę klientów z jego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="9aad1-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="9aad1-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="9aad1-137">Example</span></span>  
 <span data-ttu-id="9aad1-138">Poniższy kod łączy dwie kolekcje przy użyciu `Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9aad1-138">The following code example joins two collections by using the `Join` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]  
  
 <span data-ttu-id="9aad1-139">Ten przykład generuje dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="9aad1-139">This example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a><span data-ttu-id="9aad1-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="9aad1-140">Example</span></span>  
 <span data-ttu-id="9aad1-141">Poniższy kod łączy dwie kolekcje przy użyciu `Join` klauzulę zawierającą dwie kolumny klucza.</span><span class="sxs-lookup"><span data-stu-id="9aad1-141">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]  
  
 <span data-ttu-id="9aad1-142">Przykład generuje dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="9aad1-142">The example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a><span data-ttu-id="9aad1-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9aad1-143">See Also</span></span>  
 [<span data-ttu-id="9aad1-144">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9aad1-144">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="9aad1-145">Zapytania</span><span class="sxs-lookup"><span data-stu-id="9aad1-145">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="9aad1-146">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="9aad1-146">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="9aad1-147">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="9aad1-147">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="9aad1-148">Klauzula Group Join</span><span class="sxs-lookup"><span data-stu-id="9aad1-148">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="9aad1-149">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="9aad1-149">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
