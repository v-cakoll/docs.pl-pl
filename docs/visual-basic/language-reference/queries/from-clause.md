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
ms.openlocfilehash: 781902f1bf28bd029c8d9825aee155a6691cbae9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004781"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="3afad-102">From — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3afad-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="3afad-103">Określa co najmniej jedną zmienną zakresu i kolekcję do zapytania.</span><span class="sxs-lookup"><span data-stu-id="3afad-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3afad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3afad-104">Syntax</span></span>  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="3afad-105">Części</span><span class="sxs-lookup"><span data-stu-id="3afad-105">Parts</span></span>  
  
|<span data-ttu-id="3afad-106">Termin</span><span class="sxs-lookup"><span data-stu-id="3afad-106">Term</span></span>|<span data-ttu-id="3afad-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="3afad-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="3afad-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="3afad-108">Required.</span></span> <span data-ttu-id="3afad-109">*Zmienna zakresu* używana do iteracji elementów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3afad-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="3afad-110">Zmienna zakresu służy do odwoływania się do każdego elementu członkowskiego `collection`, ponieważ zapytanie wykonuje iterację przez `collection`.</span><span class="sxs-lookup"><span data-stu-id="3afad-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="3afad-111">Musi być typem wyliczalnym.</span><span class="sxs-lookup"><span data-stu-id="3afad-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="3afad-112">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3afad-112">Optional.</span></span> <span data-ttu-id="3afad-113">Typ `element`.</span><span class="sxs-lookup"><span data-stu-id="3afad-113">The type of `element`.</span></span> <span data-ttu-id="3afad-114">Jeśli nie określono `type`, typ `element` jest wnioskowany z `collection`.</span><span class="sxs-lookup"><span data-stu-id="3afad-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="3afad-115">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="3afad-115">Required.</span></span> <span data-ttu-id="3afad-116">Odwołuje się do kolekcji, do której mają być wysyłane zapytania.</span><span class="sxs-lookup"><span data-stu-id="3afad-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="3afad-117">Musi być typem wyliczalnym.</span><span class="sxs-lookup"><span data-stu-id="3afad-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3afad-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3afad-118">Remarks</span></span>  
 <span data-ttu-id="3afad-119">Klauzula `From` służy do identyfikowania danych źródłowych zapytania i zmiennych, które są używane do odwoływania się do elementu z kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="3afad-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="3afad-120">Te zmienne są nazywane *zmiennymi zakresu*.</span><span class="sxs-lookup"><span data-stu-id="3afad-120">These variables are called *range variables*.</span></span> <span data-ttu-id="3afad-121">Klauzula `From` jest wymagana dla zapytania, z wyjątkiem sytuacji, gdy klauzula `Aggregate` służy do identyfikowania zapytania, które zwraca tylko zagregowane wyniki.</span><span class="sxs-lookup"><span data-stu-id="3afad-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="3afad-122">Aby uzyskać więcej informacji, zobacz [klauzula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="3afad-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="3afad-123">Można określić wiele klauzul `From` w zapytaniu, aby zidentyfikować wiele kolekcji do przyłączenia.</span><span class="sxs-lookup"><span data-stu-id="3afad-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="3afad-124">Jeśli określono wiele kolekcji, są one powtarzane niezależnie lub można je przyłączać, jeśli są powiązane.</span><span class="sxs-lookup"><span data-stu-id="3afad-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="3afad-125">Kolekcje można sprzęgać niejawnie za pomocą klauzuli `Select` lub jawnie za pomocą klauzul `Join` lub `Group Join`.</span><span class="sxs-lookup"><span data-stu-id="3afad-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="3afad-126">Alternatywnie można określić wiele zmiennych zakresów i kolekcji w pojedynczej klauzuli `From`, z każdą pokrewną zmienną zakresu i kolekcją oddzieloną od innych, przecinkiem.</span><span class="sxs-lookup"><span data-stu-id="3afad-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="3afad-127">Poniższy przykład kodu pokazuje obie opcje składni dla klauzuli `From`.</span><span class="sxs-lookup"><span data-stu-id="3afad-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="3afad-128">Klauzula `From` definiuje zakres zapytania, który jest podobny do zakresu pętli `For`.</span><span class="sxs-lookup"><span data-stu-id="3afad-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="3afad-129">W związku z tym Każda zmienna zakresu `element` w zakresie zapytania musi mieć unikatową nazwę.</span><span class="sxs-lookup"><span data-stu-id="3afad-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="3afad-130">Ponieważ można określić wiele klauzul `From` dla zapytania, kolejne klauzule `From` mogą odwoływać się do zmiennych zakresu w klauzuli `From` lub mogą odwoływać się do zmiennych zakresu w poprzedniej klauzuli `From`.</span><span class="sxs-lookup"><span data-stu-id="3afad-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="3afad-131">Na przykład poniższy przykład pokazuje zagnieżdżoną klauzulę `From`, gdzie kolekcja w drugiej klauzuli jest oparta na właściwości zmiennej zakresu w pierwszej klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3afad-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="3afad-132">Każda klauzula `From` może następować dowolną kombinacją dodatkowych klauzul zapytania, aby uściślić zapytanie.</span><span class="sxs-lookup"><span data-stu-id="3afad-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="3afad-133">Zapytanie można uściślić w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3afad-133">You can refine the query in the following ways:</span></span>  
  
- <span data-ttu-id="3afad-134">Połącz wiele kolekcji niejawnie za pomocą klauzul `From` i `Select` lub jawnie za pomocą klauzul `Join` lub `Group Join`.</span><span class="sxs-lookup"><span data-stu-id="3afad-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
- <span data-ttu-id="3afad-135">Użyj klauzuli `Where`, aby odfiltrować wynik zapytania.</span><span class="sxs-lookup"><span data-stu-id="3afad-135">Use the `Where` clause to filter the query result.</span></span>  
  
- <span data-ttu-id="3afad-136">Posortuj wynik przy użyciu klauzuli `Order By`.</span><span class="sxs-lookup"><span data-stu-id="3afad-136">Sort the result by using the `Order By` clause.</span></span>  
  
- <span data-ttu-id="3afad-137">Grupuj podobne wyniki przy użyciu klauzuli `Group By`.</span><span class="sxs-lookup"><span data-stu-id="3afad-137">Group similar results together by using the `Group By` clause.</span></span>  
  
- <span data-ttu-id="3afad-138">Użyj klauzuli `Aggregate`, aby zidentyfikować funkcje agregujące do obliczenia dla całego wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="3afad-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
- <span data-ttu-id="3afad-139">Użyj klauzuli `Let`, aby wprowadzić zmienną iteracji, której wartość jest określana przez wyrażenie zamiast kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3afad-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
- <span data-ttu-id="3afad-140">Użyj klauzuli `Distinct` do ignorowania zduplikowanych wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="3afad-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
- <span data-ttu-id="3afad-141">Zidentyfikuj części wyniku do zwrócenia przy użyciu klauzul `Skip`, `Take`, `Skip While` i `Take While`.</span><span class="sxs-lookup"><span data-stu-id="3afad-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3afad-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="3afad-142">Example</span></span>  
 <span data-ttu-id="3afad-143">Następujące wyrażenie zapytania używa klauzuli `From`, aby zadeklarować zmienną zakresu `cust` dla każdego obiektu `Customer` w kolekcji `customers`.</span><span class="sxs-lookup"><span data-stu-id="3afad-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="3afad-144">Klauzula `Where` używa zmiennej zakresu w celu ograniczenia danych wyjściowych do klientów z określonego regionu.</span><span class="sxs-lookup"><span data-stu-id="3afad-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="3afad-145">Pętla `For Each` Wyświetla nazwę firmy dla każdego klienta w wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="3afad-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="3afad-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3afad-146">See also</span></span>

- [<span data-ttu-id="3afad-147">Zapytania</span><span class="sxs-lookup"><span data-stu-id="3afad-147">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="3afad-148">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3afad-148">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="3afad-149">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3afad-149">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="3afad-150">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3afad-150">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="3afad-151">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="3afad-151">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="3afad-152">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="3afad-152">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="3afad-153">Aggregate, klauzula</span><span class="sxs-lookup"><span data-stu-id="3afad-153">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="3afad-154">Distinct, klauzula</span><span class="sxs-lookup"><span data-stu-id="3afad-154">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="3afad-155">Join, klauzula</span><span class="sxs-lookup"><span data-stu-id="3afad-155">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)
- [<span data-ttu-id="3afad-156">Group Join, klauzula</span><span class="sxs-lookup"><span data-stu-id="3afad-156">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="3afad-157">Order By, klauzula</span><span class="sxs-lookup"><span data-stu-id="3afad-157">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="3afad-158">Let, klauzula</span><span class="sxs-lookup"><span data-stu-id="3afad-158">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)
- [<span data-ttu-id="3afad-159">Skip, klauzula</span><span class="sxs-lookup"><span data-stu-id="3afad-159">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="3afad-160">Take, klauzula</span><span class="sxs-lookup"><span data-stu-id="3afad-160">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="3afad-161">Skip While, klauzula</span><span class="sxs-lookup"><span data-stu-id="3afad-161">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="3afad-162">Take While, klauzula</span><span class="sxs-lookup"><span data-stu-id="3afad-162">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
