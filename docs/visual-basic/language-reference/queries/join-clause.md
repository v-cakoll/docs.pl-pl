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
ms.openlocfilehash: b5211d0ed3f618013dc9fe764a6d7b2db8177c26
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582293"
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="b6236-102">Join — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6236-102">Join Clause (Visual Basic)</span></span>

<span data-ttu-id="b6236-103">Łączy dwie kolekcje w jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="b6236-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="b6236-104">Operacja join jest oparta na zgodnych kluczach i używa operatora `Equals`.</span><span class="sxs-lookup"><span data-stu-id="b6236-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>

## <a name="syntax"></a><span data-ttu-id="b6236-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6236-105">Syntax</span></span>

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a><span data-ttu-id="b6236-106">Części</span><span class="sxs-lookup"><span data-stu-id="b6236-106">Parts</span></span>

<span data-ttu-id="b6236-107">Wymagane `element`.</span><span class="sxs-lookup"><span data-stu-id="b6236-107">`element` Required.</span></span> <span data-ttu-id="b6236-108">Zmienna kontroli dla połączonej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b6236-108">The control variable for the collection being joined.</span></span>

`collection`  
<span data-ttu-id="b6236-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b6236-109">Required.</span></span> <span data-ttu-id="b6236-110">Kolekcja do połączenia z kolekcją zidentyfikowaną po lewej stronie operatora `Join`.</span><span class="sxs-lookup"><span data-stu-id="b6236-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="b6236-111">Klauzula `Join` może być zagnieżdżona w innej klauzuli `Join` lub w klauzuli `Group Join`.</span><span class="sxs-lookup"><span data-stu-id="b6236-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>

`joinClause`  
<span data-ttu-id="b6236-112">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b6236-112">Optional.</span></span> <span data-ttu-id="b6236-113">Co najmniej jednej z dodatkowych klauzul `Join` w celu dodatkowego uściślenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="b6236-113">One or more additional `Join` clauses to further refine the query.</span></span>

`groupJoinClause`  
<span data-ttu-id="b6236-114">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b6236-114">Optional.</span></span> <span data-ttu-id="b6236-115">Co najmniej jednej z dodatkowych klauzul `Group Join` w celu dodatkowego uściślenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="b6236-115">One or more additional `Group Join` clauses to further refine the query.</span></span>

<span data-ttu-id="b6236-116">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="b6236-116">`key1` `Equals` `key2`</span></span>  
<span data-ttu-id="b6236-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b6236-117">Required.</span></span> <span data-ttu-id="b6236-118">Identyfikuje klucze dla kolekcji, które są sprzężone.</span><span class="sxs-lookup"><span data-stu-id="b6236-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="b6236-119">Należy użyć operatora `Equals`, aby porównać klucze z kolekcji, które są sprzężone.</span><span class="sxs-lookup"><span data-stu-id="b6236-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="b6236-120">Możesz połączyć warunki sprzężenia przy użyciu operatora `And`, aby zidentyfikować wiele kluczy.</span><span class="sxs-lookup"><span data-stu-id="b6236-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="b6236-121">`key1` musi znajdować się w kolekcji po lewej stronie operatora `Join`.</span><span class="sxs-lookup"><span data-stu-id="b6236-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="b6236-122">`key2` musi pochodzić z kolekcji po prawej stronie operatora `Join`.</span><span class="sxs-lookup"><span data-stu-id="b6236-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>

<span data-ttu-id="b6236-123">Klucze używane w warunku sprzężenia mogą być wyrażeniami, które zawierają więcej niż jeden element z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b6236-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="b6236-124">Jednak każde wyrażenie klucza może zawierać tylko elementy z odpowiedniej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b6236-124">However, each key expression can contain only items from its respective collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6236-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6236-125">Remarks</span></span>

<span data-ttu-id="b6236-126">Klauzula `Join` łączy dwie kolekcje na podstawie pasujących wartości klucza z kolekcji, które są sprzężone.</span><span class="sxs-lookup"><span data-stu-id="b6236-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="b6236-127">Kolekcja wyników może zawierać dowolną kombinację wartości z kolekcji identyfikowanej po lewej stronie operatora `Join` i kolekcji identyfikowanej w klauzuli `Join`.</span><span class="sxs-lookup"><span data-stu-id="b6236-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="b6236-128">Zapytanie zwróci tylko wyniki, dla których spełniony jest warunek określony przez operator `Equals`.</span><span class="sxs-lookup"><span data-stu-id="b6236-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="b6236-129">Jest to odpowiednik `INNER JOIN` w SQL.</span><span class="sxs-lookup"><span data-stu-id="b6236-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>

<span data-ttu-id="b6236-130">W zapytaniu można użyć wielu klauzul `Join` w celu dołączenia dwóch lub większej liczby kolekcji do pojedynczej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b6236-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>

<span data-ttu-id="b6236-131">Można wykonać niejawne sprzężenie w celu łączenia kolekcji bez klauzuli `Join`.</span><span class="sxs-lookup"><span data-stu-id="b6236-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="b6236-132">W tym celu należy uwzględnić wiele klauzul `In` w klauzuli `From` i określić klauzulę `Where`, która identyfikuje klucze, które mają być używane dla sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="b6236-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>

<span data-ttu-id="b6236-133">Można użyć klauzuli `Group Join`, aby połączyć kolekcje w jedną hierarchiczną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="b6236-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="b6236-134">Jest to podobne do `LEFT OUTER JOIN` w SQL.</span><span class="sxs-lookup"><span data-stu-id="b6236-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>

## <a name="example"></a><span data-ttu-id="b6236-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6236-135">Example</span></span>

<span data-ttu-id="b6236-136">Poniższy przykład kodu wykonuje niejawne sprzężenie w celu połączenia listy klientów z ich zamówieniami.</span><span class="sxs-lookup"><span data-stu-id="b6236-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a><span data-ttu-id="b6236-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6236-137">Example</span></span>

<span data-ttu-id="b6236-138">Poniższy przykład kodu łączy dwie kolekcje przy użyciu klauzuli `Join`.</span><span class="sxs-lookup"><span data-stu-id="b6236-138">The following code example joins two collections by using the `Join` clause.</span></span>

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

<span data-ttu-id="b6236-139">Ten przykład generuje dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="b6236-139">This example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a><span data-ttu-id="b6236-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6236-140">Example</span></span>

<span data-ttu-id="b6236-141">Poniższy przykład kodu łączy dwie kolekcje przy użyciu klauzuli `Join` z dwiema kolumnami klucza.</span><span class="sxs-lookup"><span data-stu-id="b6236-141">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

<span data-ttu-id="b6236-142">Przykład generuje dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="b6236-142">The example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a><span data-ttu-id="b6236-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6236-143">See also</span></span>

- [<span data-ttu-id="b6236-144">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b6236-144">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="b6236-145">Zapytania</span><span class="sxs-lookup"><span data-stu-id="b6236-145">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="b6236-146">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="b6236-146">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="b6236-147">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="b6236-147">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="b6236-148">Group Join, klauzula</span><span class="sxs-lookup"><span data-stu-id="b6236-148">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="b6236-149">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="b6236-149">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
