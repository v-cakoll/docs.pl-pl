---
title: "TryCast — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords: TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6be11b49eb3b9d98e3bf147e9b1026d4ffc860c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="e20d9-102">TryCast — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e20d9-102">TryCast Operator (Visual Basic)</span></span>
<span data-ttu-id="e20d9-103">Wprowadza operację konwersji typu, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e20d9-103">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e20d9-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e20d9-104">Remarks</span></span>  
 <span data-ttu-id="e20d9-105">Jeśli próba konwersji nie powiedzie się, `CType` i `DirectCast` zarówno throw <xref:System.InvalidCastException> błędu.</span><span class="sxs-lookup"><span data-stu-id="e20d9-105">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="e20d9-106">Może to negatywnie wpłynąć na wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e20d9-106">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="e20d9-107">`TryCast`Zwraca [nic](../../../visual-basic/language-reference/nothing.md), dzięki czemu zamiast do obsługi wyjątku możliwe, należy tylko testowe zwrócony wynik przed `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="e20d9-107">`TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="e20d9-108">Możesz użyć `TryCast` — słowo kluczowe tak samo jak [CType — funkcja](../../../visual-basic/language-reference/functions/ctype-function.md) i [operatora DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="e20d9-108">You use the `TryCast` keyword the same way you use the [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) and the [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) keyword.</span></span> <span data-ttu-id="e20d9-109">Należy podać wyrażenie jako pierwszego argumentu oraz typ konwertować jako drugi argument.</span><span class="sxs-lookup"><span data-stu-id="e20d9-109">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="e20d9-110">`TryCast`działa tylko w typach referencyjnych, takich jak klasy i interfejsy.</span><span class="sxs-lookup"><span data-stu-id="e20d9-110">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="e20d9-111">Wymaga to dziedziczenia lub implementacji relacji między tymi dwoma typami.</span><span class="sxs-lookup"><span data-stu-id="e20d9-111">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="e20d9-112">Oznacza to, że jeden typ musi dziedziczyć lub implementować innych.</span><span class="sxs-lookup"><span data-stu-id="e20d9-112">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="e20d9-113">Błędów i niepowodzeń</span><span class="sxs-lookup"><span data-stu-id="e20d9-113">Errors and Failures</span></span>  
 <span data-ttu-id="e20d9-114">`TryCast`generuje błąd kompilatora, jeśli wykryje, że żadna dziedziczenia lub implementacji relacja nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="e20d9-114">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="e20d9-115">Jednak brak wystąpi błąd kompilatora nie gwarantuje pomyślne konwersji.</span><span class="sxs-lookup"><span data-stu-id="e20d9-115">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="e20d9-116">Jeśli żądany konwersja jest zawężenie, może nie działać w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e20d9-116">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="e20d9-117">W takim przypadku `TryCast` zwraca [nic](../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="e20d9-117">If this happens, `TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="e20d9-118">Słowa kluczowe konwersji</span><span class="sxs-lookup"><span data-stu-id="e20d9-118">Conversion Keywords</span></span>  
 <span data-ttu-id="e20d9-119">Poniżej przedstawiono porównanie słowa kluczowe konwersji typu.</span><span class="sxs-lookup"><span data-stu-id="e20d9-119">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="e20d9-120">Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="e20d9-120">Keyword</span></span>|<span data-ttu-id="e20d9-121">Typy danych</span><span class="sxs-lookup"><span data-stu-id="e20d9-121">Data types</span></span>|<span data-ttu-id="e20d9-122">Argument relacji</span><span class="sxs-lookup"><span data-stu-id="e20d9-122">Argument relationship</span></span>|<span data-ttu-id="e20d9-123">Błąd czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="e20d9-123">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="e20d9-124">CType — funkcja</span><span class="sxs-lookup"><span data-stu-id="e20d9-124">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)|<span data-ttu-id="e20d9-125">Wszystkie typy danych</span><span class="sxs-lookup"><span data-stu-id="e20d9-125">Any data types</span></span>|<span data-ttu-id="e20d9-126">Rozszerzanie i zwężanie konwersji muszą być zdefiniowane między dwoma typami</span><span class="sxs-lookup"><span data-stu-id="e20d9-126">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="e20d9-127">Zgłasza wyjątek<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="e20d9-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="e20d9-128">DirectCast — Operator</span><span class="sxs-lookup"><span data-stu-id="e20d9-128">DirectCast Operator</span></span>](../../../visual-basic/language-reference/operators/directcast-operator.md)|<span data-ttu-id="e20d9-129">Wszystkie typy danych</span><span class="sxs-lookup"><span data-stu-id="e20d9-129">Any data types</span></span>|<span data-ttu-id="e20d9-130">Jeden typ musi dziedziczyć lub implementować typ innych</span><span class="sxs-lookup"><span data-stu-id="e20d9-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="e20d9-131">Zgłasza wyjątek<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="e20d9-131">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="e20d9-132">Tylko typy odwołań</span><span class="sxs-lookup"><span data-stu-id="e20d9-132">Reference types only</span></span>|<span data-ttu-id="e20d9-133">Jeden typ musi dziedziczyć lub implementować typ innych</span><span class="sxs-lookup"><span data-stu-id="e20d9-133">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="e20d9-134">Zwraca [nic](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="e20d9-134">Returns [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e20d9-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="e20d9-135">Example</span></span>  
 <span data-ttu-id="e20d9-136">Poniższy przykład przedstawia użycie `TryCast`.</span><span class="sxs-lookup"><span data-stu-id="e20d9-136">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](../../../visual-basic/language-reference/codesnippet/VisualBasic/trycast-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e20d9-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e20d9-137">See Also</span></span>  
 [<span data-ttu-id="e20d9-138">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="e20d9-138">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="e20d9-139">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="e20d9-139">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
