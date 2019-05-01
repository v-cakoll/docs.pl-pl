---
title: Operatory porównania (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basic
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: 9014cac5e2f3933b27411dfe5681fc16f4cdde30
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013585"
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="e3a9b-102">Operatory porównania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3a9b-102">Comparison Operators (Visual Basic)</span></span>
<span data-ttu-id="e3a9b-103">Dostępne są następujące operatory porównania zdefiniowany w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-103">The following are the comparison operators defined in Visual Basic.</span></span>  
  
 <span data-ttu-id="e3a9b-104">`<` Operator</span><span class="sxs-lookup"><span data-stu-id="e3a9b-104">`<` operator</span></span>  
  
 <span data-ttu-id="e3a9b-105">`<=` Operator</span><span class="sxs-lookup"><span data-stu-id="e3a9b-105">`<=` operator</span></span>  
  
 <span data-ttu-id="e3a9b-106">`>` Operator</span><span class="sxs-lookup"><span data-stu-id="e3a9b-106">`>` operator</span></span>  
  
 <span data-ttu-id="e3a9b-107">`>=` Operator</span><span class="sxs-lookup"><span data-stu-id="e3a9b-107">`>=` operator</span></span>  
  
 <span data-ttu-id="e3a9b-108">`=` Operator</span><span class="sxs-lookup"><span data-stu-id="e3a9b-108">`=` operator</span></span>  
  
 <span data-ttu-id="e3a9b-109">`<>` Operator</span><span class="sxs-lookup"><span data-stu-id="e3a9b-109">`<>` operator</span></span>  
  
 [<span data-ttu-id="e3a9b-110">Is, operator</span><span class="sxs-lookup"><span data-stu-id="e3a9b-110">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [<span data-ttu-id="e3a9b-111">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="e3a9b-111">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [<span data-ttu-id="e3a9b-112">Like, operator</span><span class="sxs-lookup"><span data-stu-id="e3a9b-112">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 <span data-ttu-id="e3a9b-113">Te operatory porównania dwóch wyrażeń, aby określić, czy są równe, a jeśli nie, jak się różnią.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-113">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="e3a9b-114">`Is`, `IsNot`, i `Like` opisano szczegółowo w osobnych stron pomocy.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-114">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="e3a9b-115">Operatory relacyjne porównania są szczegółowo omówione w na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-115">The relational comparison operators are discussed in detail on this page.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3a9b-116">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3a9b-116">Syntax</span></span>  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="e3a9b-117">Części</span><span class="sxs-lookup"><span data-stu-id="e3a9b-117">Parts</span></span>  
 `result`  
 <span data-ttu-id="e3a9b-118">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-118">Required.</span></span> <span data-ttu-id="e3a9b-119">A `Boolean` wartość reprezentująca wynik porównania.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-119">A `Boolean` value representing the result of the comparison.</span></span>  
  
 `expression`  
 <span data-ttu-id="e3a9b-120">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-120">Required.</span></span> <span data-ttu-id="e3a9b-121">Dowolne wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-121">Any expression.</span></span>  
  
 `comparisonoperator`  
 <span data-ttu-id="e3a9b-122">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-122">Required.</span></span> <span data-ttu-id="e3a9b-123">Dowolny relacyjny operator porównania.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-123">Any relational comparison operator.</span></span>  
  
 <span data-ttu-id="e3a9b-124">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="e3a9b-124">`object1`, `object2`</span></span>  
 <span data-ttu-id="e3a9b-125">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-125">Required.</span></span> <span data-ttu-id="e3a9b-126">Wszystkie nazwy obiektów odwołania.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-126">Any reference object names.</span></span>  
  
 `string`  
 <span data-ttu-id="e3a9b-127">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-127">Required.</span></span> <span data-ttu-id="e3a9b-128">Wszelkie `String` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-128">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="e3a9b-129">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-129">Required.</span></span> <span data-ttu-id="e3a9b-130">Wszelkie `String` wyrażenie lub zakres znaków.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-130">Any `String` expression or range of characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3a9b-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3a9b-131">Remarks</span></span>  
 <span data-ttu-id="e3a9b-132">Poniższa tabela zawiera listę operatorów relacyjnych porównania i warunki, które określają, czy `result` jest `True` lub `False`.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-132">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>  
  
|<span data-ttu-id="e3a9b-133">Operator</span><span class="sxs-lookup"><span data-stu-id="e3a9b-133">Operator</span></span>|<span data-ttu-id="e3a9b-134">`True` Jeśli</span><span class="sxs-lookup"><span data-stu-id="e3a9b-134">`True` if</span></span>|<span data-ttu-id="e3a9b-135">`False` Jeśli</span><span class="sxs-lookup"><span data-stu-id="e3a9b-135">`False` if</span></span>|  
|--------------|---------------|----------------|  
|<span data-ttu-id="e3a9b-136">`<` (Mniejsze niż)</span><span class="sxs-lookup"><span data-stu-id="e3a9b-136">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|  
|<span data-ttu-id="e3a9b-137">`<=` (Mniejsze niż lub równe)</span><span class="sxs-lookup"><span data-stu-id="e3a9b-137">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|  
|<span data-ttu-id="e3a9b-138">`>` (Większe niż)</span><span class="sxs-lookup"><span data-stu-id="e3a9b-138">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|  
|<span data-ttu-id="e3a9b-139">`>=` (Większe niż lub równe)</span><span class="sxs-lookup"><span data-stu-id="e3a9b-139">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|  
|<span data-ttu-id="e3a9b-140">`=` (Równe)</span><span class="sxs-lookup"><span data-stu-id="e3a9b-140">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|  
|<span data-ttu-id="e3a9b-141">`<>` (Nie równa się)</span><span class="sxs-lookup"><span data-stu-id="e3a9b-141">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  <span data-ttu-id="e3a9b-142">[= — Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) jest również używany jako operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-142">The [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) is also used as an assignment operator.</span></span>  
  
 <span data-ttu-id="e3a9b-143">`Is` Operatora `IsNot` operatora i `Like` operator ma porównania określone funkcje, które różnią się od operatorów w powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-143">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>  
  
## <a name="comparing-numbers"></a><span data-ttu-id="e3a9b-144">Porównanie liczb</span><span class="sxs-lookup"><span data-stu-id="e3a9b-144">Comparing Numbers</span></span>  
 <span data-ttu-id="e3a9b-145">Przy porównaniu wyrażenie typu `Single` do jednego typu `Double`, `Single` wyrażenie jest konwertowany na `Double`.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-145">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="e3a9b-146">To zachowanie jest przeciwnej zachowanie w języku Visual Basic 6.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-146">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>  
  
 <span data-ttu-id="e3a9b-147">Podobnie, jeśli do porównania wyrażenie typu `Decimal` do wyrażenia typu `Single` lub `Double`, `Decimal` wyrażenie jest konwertowany na `Single` lub `Double`.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-147">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="e3a9b-148">Aby uzyskać `Decimal` wyrażeń, dowolnej ułamkowe wartości mniejszej niż 1E-28 mogą zostać utracone.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-148">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="e3a9b-149">Takie utraty wartość ułamkowa może spowodować dwie wartości do porównania jako równe, jeśli nie są one.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-149">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="e3a9b-150">Z tego powodu należy zajmie się przy użyciu równości (`=`) do porównywania dwóch zmienne zmiennoprzecinkowe.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-150">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="e3a9b-151">Jest to bezpieczniejsze sprawdzić, czy wartość bezwzględną liczby różnicę między dwoma liczbami jest mniejsza niż małych akceptowane na uszkodzenia.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-151">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>  
  
### <a name="floating-point-imprecision"></a><span data-ttu-id="e3a9b-152">Zmiennoprzecinkowe niedokładności</span><span class="sxs-lookup"><span data-stu-id="e3a9b-152">Floating-point Imprecision</span></span>  
 <span data-ttu-id="e3a9b-153">Podczas pracy z liczb zmiennoprzecinkowych, należy pamiętać o tym, że nie zawsze mają dokładne reprezentacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-153">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="e3a9b-154">Może to spowodować nieoczekiwane wyniki z niektórych operacji, takich jak porównania wartości i [Mod — Operator](../../../visual-basic/language-reference/operators/mod-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e3a9b-154">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](../../../visual-basic/language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="e3a9b-155">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="e3a9b-155">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="comparing-strings"></a><span data-ttu-id="e3a9b-156">Porównywanie ciągów</span><span class="sxs-lookup"><span data-stu-id="e3a9b-156">Comparing Strings</span></span>  
 <span data-ttu-id="e3a9b-157">Podczas porównywania ciągów wyrażenia ciągu są oceniane w oparciu o ich kolejność sortowania alfabetycznego, która zależy od `Option Compare` ustawienie.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-157">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>  
  
 <span data-ttu-id="e3a9b-158">`Option Compare Binary` podstawy ciąg porównania w porządku sortowania pochodną wewnętrzne binarne reprezentacje znaków.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-158">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="e3a9b-159">Kolejność sortowania jest określana przez stronę kodową.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-159">The sort order is determined by the code page.</span></span> <span data-ttu-id="e3a9b-160">Poniższy przykład przedstawia typowy binarny porządek sortowania.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-160">The following example shows a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="e3a9b-161">`Option Compare Text` podstawy ciąg porównania w kolejności sortowania bez uwzględniania wielkości liter, tekstowe, określane przez ustawienia regionalne aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-161">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="e3a9b-162">Po ustawieniu `Option Compare Text` i sortowania znaków w poprzednim przykładzie, mają zastosowanie następujące tekstowy porządek sortowania:</span><span class="sxs-lookup"><span data-stu-id="e3a9b-162">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a><span data-ttu-id="e3a9b-163">Zależność od ustawień regionalnych</span><span class="sxs-lookup"><span data-stu-id="e3a9b-163">Locale Dependence</span></span>  
 <span data-ttu-id="e3a9b-164">Po ustawieniu `Option Compare Text`, wynikiem porównania ciągów może zależeć od ustawień regionalnych, w którym aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-164">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="e3a9b-165">Dwa znaki może być porównywany jako równe w jeden ustawień regionalnych, ale nie w innym.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-165">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="e3a9b-166">Jeśli używasz porównania ciągów podjęcie istotnych decyzji, np. Czy chcesz zaakceptować próba logowania, należy alertu wrażliwość na ustawienia regionalne.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-166">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="e3a9b-167">Rozważ ustawienie albo `Option Compare Binary` lub wywoływania <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, która uwzględnia ustawienia regionalne.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-167">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="e3a9b-168">Programowanie nietypowane z operatorów porównania relacyjnych</span><span class="sxs-lookup"><span data-stu-id="e3a9b-168">Typeless Programming with Relational Comparison Operators</span></span>  
 <span data-ttu-id="e3a9b-169">Korzystanie z operatorów porównania relacyjnych z `Object` wyrażenia nie jest dozwolone w ramach `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-169">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="e3a9b-170">Gdy `Option Strict` jest `Off`oraz `expression1` lub `expression2` jest `Object` wyrażenia, typy środowiska wykonawczego określają, jak są porównywane.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-170">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="e3a9b-171">W poniższej tabeli przedstawiono, jak są porównywane wyrażeń i wynikiem porównania, w zależności od typu środowiska uruchomieniowego operandu.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-171">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>  
  
|<span data-ttu-id="e3a9b-172">W przypadku argumentów operacji</span><span class="sxs-lookup"><span data-stu-id="e3a9b-172">If operands are</span></span>|<span data-ttu-id="e3a9b-173">Porównanie jest</span><span class="sxs-lookup"><span data-stu-id="e3a9b-173">Comparison is</span></span>|  
|---------------------|-------------------|  
|<span data-ttu-id="e3a9b-174">Oba `String`</span><span class="sxs-lookup"><span data-stu-id="e3a9b-174">Both `String`</span></span>|<span data-ttu-id="e3a9b-175">Posortuj porównań opartych na właściwości sortowania ciągów.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-175">Sort comparison based on string sorting characteristics.</span></span>|  
|<span data-ttu-id="e3a9b-176">Zarówno liczbowe</span><span class="sxs-lookup"><span data-stu-id="e3a9b-176">Both numeric</span></span>|<span data-ttu-id="e3a9b-177">Obiekty konwertowane `Double`, porównanie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-177">Objects converted to `Double`, numeric comparison.</span></span>|  
|<span data-ttu-id="e3a9b-178">Jeden liczbowych i jeden `String`</span><span class="sxs-lookup"><span data-stu-id="e3a9b-178">One numeric and one `String`</span></span>|<span data-ttu-id="e3a9b-179">`String` Jest konwertowana na `Double` i wykonywane jest porównanie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-179">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="e3a9b-180">Jeśli `String` nie można przekonwertować na `Double`, <xref:System.InvalidCastException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-180">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|  
|<span data-ttu-id="e3a9b-181">Jeden lub oba są typami odwołań, innym niż `String`</span><span class="sxs-lookup"><span data-stu-id="e3a9b-181">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="e3a9b-182"><xref:System.InvalidCastException> Zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-182">An <xref:System.InvalidCastException> is thrown.</span></span>|  
  
 <span data-ttu-id="e3a9b-183">Traktuj liczbowego porównania `Nothing` jako 0.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-183">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="e3a9b-184">Traktuj porównań ciągów `Nothing` jako `""` (ciąg pusty).</span><span class="sxs-lookup"><span data-stu-id="e3a9b-184">String comparisons treat `Nothing` as `""` (an empty string).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="e3a9b-185">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="e3a9b-185">Overloading</span></span>  
 <span data-ttu-id="e3a9b-186">Operatory relacyjne (`<`.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-186">The relational comparison operators (`<`.</span></span> <span data-ttu-id="e3a9b-187">`<=``>`, `>=`, `=`, `<>`) może być *przeciążone*, co oznacza, że klasa lub Struktura można ponownie zdefiniować ich zachowania, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-187">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e3a9b-188">Jeśli Twój kod wykorzystuje dowolne z tych operatorów dla klasy lub struktury, upewnij się, że należy zrozumieć zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-188">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="e3a9b-189">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e3a9b-189">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
 <span data-ttu-id="e3a9b-190">Należy zauważyć, że [= — Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) mogą być przeciążone, tylko jako operator porównania relacyjnych, a nie jako operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-190">Notice that the [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3a9b-191">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3a9b-191">Example</span></span>  
 <span data-ttu-id="e3a9b-192">Poniższy przykład pokazuje różne przypadki użycia operatorów porównania relacyjnych, które umożliwia porównywanie wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-192">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="e3a9b-193">Operatory relacyjne porównania zwracają `Boolean` wynik, który reprezentuje informację określającą, czy podane wyrażenie daje w wyniku `True`.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-193">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="e3a9b-194">Po zastosowaniu `>` i `<` dokonywane jest porównanie operatorów na ciągi, przy użyciu normalnych alfabetycznej sortowania ciągów.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-194">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="e3a9b-195">To zamówienie mogą być zależne od ustawienia regionalne.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-195">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="e3a9b-196">Sortowanie jest rozróżniana wielkość liter lub nie jest zależny od [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) ustawienie.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-196">Whether the sort is case-sensitive or not depends on the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) setting.</span></span>  
  
 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]  
  
 <span data-ttu-id="e3a9b-197">W powyższym przykładzie zwraca pierwszy porównania `False` i zwracają pozostałych porównań `True`.</span><span class="sxs-lookup"><span data-stu-id="e3a9b-197">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3a9b-198">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3a9b-198">See also</span></span>

- <xref:System.InvalidCastException>
- [<span data-ttu-id="e3a9b-199">=, operator</span><span class="sxs-lookup"><span data-stu-id="e3a9b-199">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [<span data-ttu-id="e3a9b-200">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3a9b-200">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="e3a9b-201">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="e3a9b-201">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="e3a9b-202">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="e3a9b-202">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="e3a9b-203">Operatory porównania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3a9b-203">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
