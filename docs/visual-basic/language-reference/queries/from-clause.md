---
title: From — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: 71573de48cc51c48291fc4b82a0628d2d0f96caa
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43801784"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="e776e-102">From — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e776e-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="e776e-103">Określa co najmniej jednej zmiennej zakresu i kolekcji do wykonywania zapytań.</span><span class="sxs-lookup"><span data-stu-id="e776e-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e776e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e776e-104">Syntax</span></span>  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="e776e-105">Części</span><span class="sxs-lookup"><span data-stu-id="e776e-105">Parts</span></span>  
  
|<span data-ttu-id="e776e-106">Termin</span><span class="sxs-lookup"><span data-stu-id="e776e-106">Term</span></span>|<span data-ttu-id="e776e-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="e776e-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="e776e-108">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="e776e-108">Required.</span></span> <span data-ttu-id="e776e-109">A *zmiennej zakresu* używany do iterowania po elementach kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e776e-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="e776e-110">Zmienna zakresu jest używana do odwoływania się do każdego elementu członkowskiego `collection` jako zapytanie wykonuje iterację przez `collection`.</span><span class="sxs-lookup"><span data-stu-id="e776e-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="e776e-111">Musi być typem wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e776e-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="e776e-112">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="e776e-112">Optional.</span></span> <span data-ttu-id="e776e-113">Typ `element`.</span><span class="sxs-lookup"><span data-stu-id="e776e-113">The type of `element`.</span></span> <span data-ttu-id="e776e-114">Jeśli nie `type` jest określona, typ `element` wynika z `collection`.</span><span class="sxs-lookup"><span data-stu-id="e776e-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="e776e-115">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="e776e-115">Required.</span></span> <span data-ttu-id="e776e-116">Odnosi się do kolekcji być badana.</span><span class="sxs-lookup"><span data-stu-id="e776e-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="e776e-117">Musi być typem wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e776e-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e776e-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e776e-118">Remarks</span></span>  
 <span data-ttu-id="e776e-119">`From` Klauzuli służy do identyfikowania źródło danych pod kątem zapytania i zmienne, które służą do odwoływania się do elementu z kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="e776e-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="e776e-120">Te zmienne są nazywane *należeć do zakresu zmiennych*.</span><span class="sxs-lookup"><span data-stu-id="e776e-120">These variables are called *range variables*.</span></span> <span data-ttu-id="e776e-121">`From` Klauzula jest wymagana dla zapytania, chyba że `Aggregate` klauzuli służy do identyfikowania, zwraca tylko zagregowane wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="e776e-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="e776e-122">Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e776e-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="e776e-123">Można określić wiele `From` klauzule w zapytaniu, aby zidentyfikować wielu kolekcji, które mają zostać połączone.</span><span class="sxs-lookup"><span data-stu-id="e776e-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="e776e-124">Jeśli określono wiele kolekcji one jest powtarzana niezależnie lub można je dołączyć, jeśli są ze sobą powiązane.</span><span class="sxs-lookup"><span data-stu-id="e776e-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="e776e-125">Dołącz kolekcje niejawnie przy użyciu `Select` klauzuli lub jawnie przy użyciu `Join` lub `Group Join` klauzul.</span><span class="sxs-lookup"><span data-stu-id="e776e-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="e776e-126">Alternatywnie, można określić wiele zmiennych zakresu i kolekcji w jednym `From` klauzuli z każdej zmiennej zakresu powiązanych i kolekcji od siebie oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="e776e-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="e776e-127">Poniższy przykład kodu pokazuje obie opcje składni `From` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e776e-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 <span data-ttu-id="e776e-128">`From` Klauzuli definiuje zakres kwerendy, co jest podobne do zakresu `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="e776e-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="e776e-129">W związku z tym, każdy `element` zmiennej zakresu w zakresie zapytania musi mieć unikatową nazwę.</span><span class="sxs-lookup"><span data-stu-id="e776e-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="e776e-130">Ponieważ można określić wiele `From` klauzul zapytania, kolejne `From` klauzule mogą odwoływać się do zakresu zmiennych w `From` klauzuli lub może dotyczyć zmiennych zakresu w ramach poprzedniego `From` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e776e-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="e776e-131">Na przykład, poniższy kod przedstawia zagnieżdżoną `From` klauzuli gdzie kolekcji w drugiej klauzuli opiera się na właściwość zmiennej zakresu w pierwszej klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e776e-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 <span data-ttu-id="e776e-132">Każdy `From` klauzula może występować w dowolnej kombinacji klauzule dodatkowe kwerendy w celu doprecyzowania zapytania.</span><span class="sxs-lookup"><span data-stu-id="e776e-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="e776e-133">Zapytania można dostosować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e776e-133">You can refine the query in the following ways:</span></span>  
  
-   <span data-ttu-id="e776e-134">Łączenie wielu kolekcji niejawnie za pomocą `From` i `Select` zdań, lub jawnie przy użyciu `Join` lub `Group Join` klauzul.</span><span class="sxs-lookup"><span data-stu-id="e776e-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
-   <span data-ttu-id="e776e-135">Użyj `Where` klauzulę filtrującą dane wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="e776e-135">Use the `Where` clause to filter the query result.</span></span>  
  
-   <span data-ttu-id="e776e-136">Sortowanie wyników za pomocą `Order By` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e776e-136">Sort the result by using the `Order By` clause.</span></span>  
  
-   <span data-ttu-id="e776e-137">Zgrupować podobne wyniki za pomocą `Group By` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e776e-137">Group similar results together by using the `Group By` clause.</span></span>  
  
-   <span data-ttu-id="e776e-138">Użyj `Aggregate` klauzuli w celu identyfikacji funkcji agregujących do oceny, czy wynik całego zapytania.</span><span class="sxs-lookup"><span data-stu-id="e776e-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
-   <span data-ttu-id="e776e-139">Użyj `Let` klauzulę, aby wprowadzić zmienną iteracji, którego wartość jest określona przez wyrażenie zamiast kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e776e-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
-   <span data-ttu-id="e776e-140">Użyj `Distinct` klauzuli ignorowanie wyników zapytania duplikatów.</span><span class="sxs-lookup"><span data-stu-id="e776e-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
-   <span data-ttu-id="e776e-141">Identyfikowanie części wyników do zwrócenia przy użyciu `Skip`, `Take`, `Skip While`, i `Take While` klauzul.</span><span class="sxs-lookup"><span data-stu-id="e776e-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e776e-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="e776e-142">Example</span></span>  
 <span data-ttu-id="e776e-143">Następujące zapytanie używa wyrażenia `From` klauzulę, aby zadeklarować zmienną zakresu `cust` dla każdego `Customer` obiektu `customers` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e776e-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="e776e-144">`Where` Klauzuli używa zmiennej zakresu, aby uniemożliwić klientom określonego regionu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="e776e-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="e776e-145">`For Each` Pętli Wyświetla nazwę firmy, dla każdego klienta, w wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="e776e-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e776e-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e776e-146">See Also</span></span>  
 [<span data-ttu-id="e776e-147">Zapytania</span><span class="sxs-lookup"><span data-stu-id="e776e-147">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="e776e-148">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e776e-148">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="e776e-149">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e776e-149">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="e776e-150">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e776e-150">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="e776e-151">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="e776e-151">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="e776e-152">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="e776e-152">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="e776e-153">Klauzula Aggregate</span><span class="sxs-lookup"><span data-stu-id="e776e-153">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="e776e-154">Distinct, klauzula</span><span class="sxs-lookup"><span data-stu-id="e776e-154">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [<span data-ttu-id="e776e-155">Join, klauzula</span><span class="sxs-lookup"><span data-stu-id="e776e-155">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)  
 [<span data-ttu-id="e776e-156">Klauzula Group Join</span><span class="sxs-lookup"><span data-stu-id="e776e-156">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="e776e-157">Order By, klauzula</span><span class="sxs-lookup"><span data-stu-id="e776e-157">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="e776e-158">Let, klauzula</span><span class="sxs-lookup"><span data-stu-id="e776e-158">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 [<span data-ttu-id="e776e-159">Skip, klauzula</span><span class="sxs-lookup"><span data-stu-id="e776e-159">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="e776e-160">Take, klauzula</span><span class="sxs-lookup"><span data-stu-id="e776e-160">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="e776e-161">Skip While, klauzula</span><span class="sxs-lookup"><span data-stu-id="e776e-161">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="e776e-162">Take While, klauzula</span><span class="sxs-lookup"><span data-stu-id="e776e-162">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
