---
title: From, klauzula
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
ms.openlocfilehash: 33680f49247b3b2a6082b3a6b27ca64f8401e42d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396184"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="58c23-102">From — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58c23-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="58c23-103">Określa co najmniej jedną zmienną zakresu i kolekcję do zapytania.</span><span class="sxs-lookup"><span data-stu-id="58c23-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58c23-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="58c23-104">Syntax</span></span>  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="58c23-105">Części</span><span class="sxs-lookup"><span data-stu-id="58c23-105">Parts</span></span>  
  
|<span data-ttu-id="58c23-106">Termin</span><span class="sxs-lookup"><span data-stu-id="58c23-106">Term</span></span>|<span data-ttu-id="58c23-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="58c23-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="58c23-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="58c23-108">Required.</span></span> <span data-ttu-id="58c23-109">*Zmienna zakresu* używana do iteracji elementów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="58c23-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="58c23-110">Zmienna zakresu jest używana do odwoływania się do każdego elementu członkowskiego, `collection` ponieważ zapytanie wykonuje iterację przez `collection` .</span><span class="sxs-lookup"><span data-stu-id="58c23-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="58c23-111">Musi być typem wyliczalnym.</span><span class="sxs-lookup"><span data-stu-id="58c23-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="58c23-112">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="58c23-112">Optional.</span></span> <span data-ttu-id="58c23-113">Typ `element` .</span><span class="sxs-lookup"><span data-stu-id="58c23-113">The type of `element`.</span></span> <span data-ttu-id="58c23-114">Jeśli nie `type` jest określony, typ `element` jest wnioskowany z `collection` .</span><span class="sxs-lookup"><span data-stu-id="58c23-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="58c23-115">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="58c23-115">Required.</span></span> <span data-ttu-id="58c23-116">Odwołuje się do kolekcji, do której mają być wysyłane zapytania.</span><span class="sxs-lookup"><span data-stu-id="58c23-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="58c23-117">Musi być typem wyliczalnym.</span><span class="sxs-lookup"><span data-stu-id="58c23-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58c23-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58c23-118">Remarks</span></span>  
 <span data-ttu-id="58c23-119">`From`Klauzula służy do identyfikowania danych źródłowych zapytania i zmiennych, które są używane do odwoływania się do elementu z kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="58c23-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="58c23-120">Te zmienne są nazywane *zmiennymi zakresu*.</span><span class="sxs-lookup"><span data-stu-id="58c23-120">These variables are called *range variables*.</span></span> <span data-ttu-id="58c23-121">`From`Klauzula jest wymagana dla zapytania, z wyjątkiem sytuacji, gdy `Aggregate` klauzula służy do identyfikowania zapytania, które zwraca tylko zagregowane wyniki.</span><span class="sxs-lookup"><span data-stu-id="58c23-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="58c23-122">Aby uzyskać więcej informacji, zobacz [klauzula Aggregate](aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="58c23-122">For more information, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="58c23-123">Można określić wiele `From` klauzul w zapytaniu, aby zidentyfikować wiele kolekcji do przyłączenia.</span><span class="sxs-lookup"><span data-stu-id="58c23-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="58c23-124">Jeśli określono wiele kolekcji, są one powtarzane niezależnie lub można je przyłączać, jeśli są powiązane.</span><span class="sxs-lookup"><span data-stu-id="58c23-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="58c23-125">Kolekcje można sprzęgać niejawnie przy użyciu `Select` klauzuli lub jawnie za pomocą `Join` `Group Join` klauzul or.</span><span class="sxs-lookup"><span data-stu-id="58c23-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="58c23-126">Alternatywnie można określić wiele zmiennych zakresów i kolekcji w pojedynczej `From` klauzuli, z każdą pokrewną zmienną zakresu i kolekcją oddzieloną od innych, przecinkiem.</span><span class="sxs-lookup"><span data-stu-id="58c23-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="58c23-127">Poniższy przykład kodu pokazuje obie opcje składni dla tej `From` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="58c23-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="58c23-128">`From`Klauzula definiuje zakres zapytania, który jest podobny do zakresu `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="58c23-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="58c23-129">W związku z tym każda `element` zmienna zakresu w zakresie zapytania musi mieć unikatową nazwę.</span><span class="sxs-lookup"><span data-stu-id="58c23-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="58c23-130">Ponieważ można określić wiele `From` klauzul dla zapytania, kolejne `From` klauzule mogą odwoływać się do zmiennych zakresu w `From` klauzuli lub mogą odwoływać się do zmiennych zakresu w poprzedniej `From` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="58c23-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="58c23-131">Na przykład poniższy przykład pokazuje klauzulę zagnieżdżoną `From` , gdzie kolekcja w drugiej klauzuli opiera się na właściwości zmiennej zakresu w pierwszej klauzuli.</span><span class="sxs-lookup"><span data-stu-id="58c23-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="58c23-132">`From`Po każdej klauzuli można wykonać dowolną kombinację dodatkowych klauzul zapytania, aby uściślić zapytanie.</span><span class="sxs-lookup"><span data-stu-id="58c23-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="58c23-133">Zapytanie można uściślić w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="58c23-133">You can refine the query in the following ways:</span></span>  
  
- <span data-ttu-id="58c23-134">Połącz wiele kolekcji niejawnie za pomocą `From` `Select` klauzul i lub jawnie za pomocą `Join` `Group Join` klauzul or.</span><span class="sxs-lookup"><span data-stu-id="58c23-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
- <span data-ttu-id="58c23-135">Użyj `Where` klauzuli, aby odfiltrować wynik zapytania.</span><span class="sxs-lookup"><span data-stu-id="58c23-135">Use the `Where` clause to filter the query result.</span></span>  
  
- <span data-ttu-id="58c23-136">Posortuj wynik przy użyciu `Order By` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="58c23-136">Sort the result by using the `Order By` clause.</span></span>  
  
- <span data-ttu-id="58c23-137">Grupuj podobne wyniki przy użyciu `Group By` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="58c23-137">Group similar results together by using the `Group By` clause.</span></span>  
  
- <span data-ttu-id="58c23-138">Użyj `Aggregate` klauzuli, aby zidentyfikować funkcje agregujące do obliczenia dla całego wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="58c23-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
- <span data-ttu-id="58c23-139">Użyj `Let` klauzuli, aby wprowadzić zmienną iteracji, której wartość jest określana przez wyrażenie zamiast kolekcji.</span><span class="sxs-lookup"><span data-stu-id="58c23-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
- <span data-ttu-id="58c23-140">Użyj `Distinct` klauzuli do ignorowania zduplikowanych wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="58c23-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
- <span data-ttu-id="58c23-141">Zidentyfikuj części wyniku do zwrócenia przy użyciu `Skip` `Take` klauzul,, `Skip While` , i `Take While` .</span><span class="sxs-lookup"><span data-stu-id="58c23-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58c23-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="58c23-142">Example</span></span>  
 <span data-ttu-id="58c23-143">Następujące wyrażenie zapytania używa klauzuli, `From` Aby zadeklarować zmienną zakresu `cust` dla każdego `Customer` obiektu w `customers` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="58c23-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="58c23-144">`Where`Klauzula używa zmiennej zakresu w celu ograniczenia danych wyjściowych do klientów z określonego regionu.</span><span class="sxs-lookup"><span data-stu-id="58c23-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="58c23-145">`For Each`Pętla wyświetla nazwę firmy dla każdego klienta w wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="58c23-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="58c23-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58c23-146">See also</span></span>

- [<span data-ttu-id="58c23-147">Zapytania</span><span class="sxs-lookup"><span data-stu-id="58c23-147">Queries</span></span>](index.md)
- [<span data-ttu-id="58c23-148">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="58c23-148">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="58c23-149">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="58c23-149">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="58c23-150">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="58c23-150">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="58c23-151">SELECT — klauzula</span><span class="sxs-lookup"><span data-stu-id="58c23-151">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="58c23-152">Klauzula WHERE</span><span class="sxs-lookup"><span data-stu-id="58c23-152">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="58c23-153">Aggregate, klauzula</span><span class="sxs-lookup"><span data-stu-id="58c23-153">Aggregate Clause</span></span>](aggregate-clause.md)
- [<span data-ttu-id="58c23-154">Distinct, klauzula</span><span class="sxs-lookup"><span data-stu-id="58c23-154">Distinct Clause</span></span>](distinct-clause.md)
- [<span data-ttu-id="58c23-155">Klauzula join</span><span class="sxs-lookup"><span data-stu-id="58c23-155">Join Clause</span></span>](join-clause.md)
- [<span data-ttu-id="58c23-156">Group Join. klauzula</span><span class="sxs-lookup"><span data-stu-id="58c23-156">Group Join Clause</span></span>](group-join-clause.md)
- [<span data-ttu-id="58c23-157">Order By, klauzula</span><span class="sxs-lookup"><span data-stu-id="58c23-157">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="58c23-158">Klauzula Let</span><span class="sxs-lookup"><span data-stu-id="58c23-158">Let Clause</span></span>](let-clause.md)
- [<span data-ttu-id="58c23-159">Skip, klauzula</span><span class="sxs-lookup"><span data-stu-id="58c23-159">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="58c23-160">Take, klauzula</span><span class="sxs-lookup"><span data-stu-id="58c23-160">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="58c23-161">Skip While, klauzula</span><span class="sxs-lookup"><span data-stu-id="58c23-161">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="58c23-162">Take While, klauzula</span><span class="sxs-lookup"><span data-stu-id="58c23-162">Take While Clause</span></span>](take-while-clause.md)
