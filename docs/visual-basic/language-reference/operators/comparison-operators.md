---
title: "Operatory porównania (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
- comparison operators [Visual Basic], Visual Basicl
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aa450f7978f46196663c7534b31597b04d80482a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="a9f01-102">Operatory porównania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9f01-102">Comparison Operators (Visual Basic)</span></span>
<span data-ttu-id="a9f01-103">Poniżej przedstawiono operatory porównania zdefiniowany w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a9f01-103">The following are the comparison operators defined in Visual Basic.</span></span>  
  
 <span data-ttu-id="a9f01-104">`<`operator</span><span class="sxs-lookup"><span data-stu-id="a9f01-104">`<` operator</span></span>  
  
 <span data-ttu-id="a9f01-105">`<=`operator</span><span class="sxs-lookup"><span data-stu-id="a9f01-105">`<=` operator</span></span>  
  
 <span data-ttu-id="a9f01-106">`>`operator</span><span class="sxs-lookup"><span data-stu-id="a9f01-106">`>` operator</span></span>  
  
 <span data-ttu-id="a9f01-107">`>=`operator</span><span class="sxs-lookup"><span data-stu-id="a9f01-107">`>=` operator</span></span>  
  
 <span data-ttu-id="a9f01-108">`=`operator</span><span class="sxs-lookup"><span data-stu-id="a9f01-108">`=` operator</span></span>  
  
 <span data-ttu-id="a9f01-109">`<>`operator</span><span class="sxs-lookup"><span data-stu-id="a9f01-109">`<>` operator</span></span>  
  
 [<span data-ttu-id="a9f01-110">Is — Operator</span><span class="sxs-lookup"><span data-stu-id="a9f01-110">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [<span data-ttu-id="a9f01-111">IsNot — Operator</span><span class="sxs-lookup"><span data-stu-id="a9f01-111">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [<span data-ttu-id="a9f01-112">Like — Operator</span><span class="sxs-lookup"><span data-stu-id="a9f01-112">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 <span data-ttu-id="a9f01-113">Te operatory porównania dwóch wyrażeń w celu ustalenia, czy są równe, a jeśli nie, jak różnią się one.</span><span class="sxs-lookup"><span data-stu-id="a9f01-113">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="a9f01-114">`Is`, `IsNot`, i `Like` opisano szczegółowo na oddzielnych stronach pomocy.</span><span class="sxs-lookup"><span data-stu-id="a9f01-114">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="a9f01-115">Operatory relacyjne opisano szczegółowo na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="a9f01-115">The relational comparison operators are discussed in detail on this page.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9f01-116">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9f01-116">Syntax</span></span>  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="a9f01-117">Części</span><span class="sxs-lookup"><span data-stu-id="a9f01-117">Parts</span></span>  
 `result`  
 <span data-ttu-id="a9f01-118">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a9f01-118">Required.</span></span> <span data-ttu-id="a9f01-119">A `Boolean` wartość reprezentująca wynik porównania.</span><span class="sxs-lookup"><span data-stu-id="a9f01-119">A `Boolean` value representing the result of the comparison.</span></span>  
  
 `expression`  
 <span data-ttu-id="a9f01-120">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a9f01-120">Required.</span></span> <span data-ttu-id="a9f01-121">Dowolne wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="a9f01-121">Any expression.</span></span>  
  
 `comparisonoperator`  
 <span data-ttu-id="a9f01-122">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a9f01-122">Required.</span></span> <span data-ttu-id="a9f01-123">Dowolny relacyjny operator porównania.</span><span class="sxs-lookup"><span data-stu-id="a9f01-123">Any relational comparison operator.</span></span>  
  
 <span data-ttu-id="a9f01-124">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="a9f01-124">`object1`, `object2`</span></span>  
 <span data-ttu-id="a9f01-125">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a9f01-125">Required.</span></span> <span data-ttu-id="a9f01-126">Wszystkie nazwy obiektu odwołania.</span><span class="sxs-lookup"><span data-stu-id="a9f01-126">Any reference object names.</span></span>  
  
 `string`  
 <span data-ttu-id="a9f01-127">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a9f01-127">Required.</span></span> <span data-ttu-id="a9f01-128">Wszelkie `String` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a9f01-128">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="a9f01-129">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a9f01-129">Required.</span></span> <span data-ttu-id="a9f01-130">Wszelkie `String` wyrażenie lub zakres znaków.</span><span class="sxs-lookup"><span data-stu-id="a9f01-130">Any `String` expression or range of characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9f01-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9f01-131">Remarks</span></span>  
 <span data-ttu-id="a9f01-132">Poniższa tabela zawiera listę operatory relacyjne i warunków, które określają, czy `result` jest `True` lub `False`.</span><span class="sxs-lookup"><span data-stu-id="a9f01-132">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>  
  
|<span data-ttu-id="a9f01-133">Operator</span><span class="sxs-lookup"><span data-stu-id="a9f01-133">Operator</span></span>|<span data-ttu-id="a9f01-134">`True`Jeśli</span><span class="sxs-lookup"><span data-stu-id="a9f01-134">`True` if</span></span>|<span data-ttu-id="a9f01-135">`False`Jeśli</span><span class="sxs-lookup"><span data-stu-id="a9f01-135">`False` if</span></span>|  
|--------------|---------------|----------------|  
|<span data-ttu-id="a9f01-136">`<`(Poniżej)</span><span class="sxs-lookup"><span data-stu-id="a9f01-136">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|  
|<span data-ttu-id="a9f01-137">`<=`(Mniejsze niż lub równe)</span><span class="sxs-lookup"><span data-stu-id="a9f01-137">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|  
|<span data-ttu-id="a9f01-138">`>`(Więcej niż)</span><span class="sxs-lookup"><span data-stu-id="a9f01-138">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|  
|<span data-ttu-id="a9f01-139">`>=`(Większe niż lub równe)</span><span class="sxs-lookup"><span data-stu-id="a9f01-139">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|  
|<span data-ttu-id="a9f01-140">`=`(Równe)</span><span class="sxs-lookup"><span data-stu-id="a9f01-140">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|  
|<span data-ttu-id="a9f01-141">`<>`(Nie ma wartości)</span><span class="sxs-lookup"><span data-stu-id="a9f01-141">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  <span data-ttu-id="a9f01-142">[= — Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) jest również używany jako operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="a9f01-142">The [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) is also used as an assignment operator.</span></span>  
  
 <span data-ttu-id="a9f01-143">`Is` Operatora, `IsNot` , operator i `Like` operator ma funkcje określonych porównanie, które różnią się od operatorów w powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="a9f01-143">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>  
  
## <a name="comparing-numbers"></a><span data-ttu-id="a9f01-144">Porównanie liczby</span><span class="sxs-lookup"><span data-stu-id="a9f01-144">Comparing Numbers</span></span>  
 <span data-ttu-id="a9f01-145">Jeśli wyrażenie typu do porównania `Single` do jednego z typów `Double`, `Single` wyrażenie jest konwertowana na `Double`.</span><span class="sxs-lookup"><span data-stu-id="a9f01-145">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="a9f01-146">To zachowanie jest przeciwnej zachowanie w języku Visual Basic 6.</span><span class="sxs-lookup"><span data-stu-id="a9f01-146">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>  
  
 <span data-ttu-id="a9f01-147">Podobnie, jeśli do porównania wyrażenia typu `Decimal` do wyrażenia typu `Single` lub `Double`, `Decimal` wyrażenie jest konwertowana na `Single` lub `Double`.</span><span class="sxs-lookup"><span data-stu-id="a9f01-147">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="a9f01-148">Aby uzyskać `Decimal` wyrażenia, każda wartość ułamkową mniej niż 28 1E mogą zostać utracone.</span><span class="sxs-lookup"><span data-stu-id="a9f01-148">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="a9f01-149">Takie utraty wartość ułamkową może spowodować dwie wartości porównać jako równe, jeśli nie są one.</span><span class="sxs-lookup"><span data-stu-id="a9f01-149">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="a9f01-150">Z tego powodu należy zajmie się przy użyciu równości (`=`) do porównania dwóch zmienne zmiennoprzecinkowe.</span><span class="sxs-lookup"><span data-stu-id="a9f01-150">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="a9f01-151">Jest bezpieczniejsze sprawdzić, czy wartość bezwzględna różnicy między dwiema liczbami jest mniejsza niż małych dopuszczalnych granicach.</span><span class="sxs-lookup"><span data-stu-id="a9f01-151">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>  
  
### <a name="floating-point-imprecision"></a><span data-ttu-id="a9f01-152">Zmiennoprzecinkowe błędu</span><span class="sxs-lookup"><span data-stu-id="a9f01-152">Floating-point Imprecision</span></span>  
 <span data-ttu-id="a9f01-153">Podczas pracy z liczb zmiennoprzecinkowych, należy pamiętać, że nie zawsze mają dokładne reprezentacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="a9f01-153">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="a9f01-154">Może to prowadzić do nieoczekiwanych wyników z niektórych operacji, takich jak porównania wartości i [Mod Operator](../../../visual-basic/language-reference/operators/mod-operator.md).</span><span class="sxs-lookup"><span data-stu-id="a9f01-154">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](../../../visual-basic/language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="a9f01-155">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="a9f01-155">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="comparing-strings"></a><span data-ttu-id="a9f01-156">Porównywanie ciągów</span><span class="sxs-lookup"><span data-stu-id="a9f01-156">Comparing Strings</span></span>  
 <span data-ttu-id="a9f01-157">Podczas porównywania ciągów wyrażenia parametrów są oceniane w oparciu ich kolejność sortowania alfabetyczne, zależy od `Option Compare` ustawienie.</span><span class="sxs-lookup"><span data-stu-id="a9f01-157">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>  
  
 <span data-ttu-id="a9f01-158">`Option Compare Binary`podstawy ciągu porównania na kolejność sortowania, pochodzi z wewnętrznego reprezentacje binarne znaków.</span><span class="sxs-lookup"><span data-stu-id="a9f01-158">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="a9f01-159">Kolejność sortowania jest określany za pomocą stron kodowych.</span><span class="sxs-lookup"><span data-stu-id="a9f01-159">The sort order is determined by the code page.</span></span> <span data-ttu-id="a9f01-160">W poniższym przykładzie przedstawiono typowe binarny porządek sortowania.</span><span class="sxs-lookup"><span data-stu-id="a9f01-160">The following example shows a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="a9f01-161">`Option Compare Text`podstawy ciągu porównania w kolejności sortowania bez uwzględniania wielkości liter, tekstowych określają ustawienia regionalne aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9f01-161">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="a9f01-162">Podczas ustawiania `Option Compare Text` i sortowania znaków w poprzednim przykładzie, mają zastosowanie następujące tekstowy porządek sortowania:</span><span class="sxs-lookup"><span data-stu-id="a9f01-162">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a><span data-ttu-id="a9f01-163">Zależność od ustawień regionalnych</span><span class="sxs-lookup"><span data-stu-id="a9f01-163">Locale Dependence</span></span>  
 <span data-ttu-id="a9f01-164">Podczas ustawiania `Option Compare Text`, wynik porównania ciągów może być zależny od ustawień regionalnych, w którym aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="a9f01-164">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="a9f01-165">Dwa znaki może porównać jako równe co ustawień regionalnych, ale nie w innym.</span><span class="sxs-lookup"><span data-stu-id="a9f01-165">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="a9f01-166">Jeśli używasz porównania ciągów podjęcie istotnych decyzji, takich jak zaakceptowanie próba logowania, należy alert do wrażliwości ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="a9f01-166">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="a9f01-167">Należy wziąć pod uwagę ustawienia `Option Compare Binary` lub wywoływania <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, która uwzględnia ustawienia regionalne.</span><span class="sxs-lookup"><span data-stu-id="a9f01-167">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="a9f01-168">Programowanie Nietypowane przy użyciu operatorów relacyjnych porównania</span><span class="sxs-lookup"><span data-stu-id="a9f01-168">Typeless Programming with Relational Comparison Operators</span></span>  
 <span data-ttu-id="a9f01-169">Korzystanie z operatorów relacyjnych porównania z `Object` wyrażenia jest niedozwolone w obszarze `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="a9f01-169">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="a9f01-170">Gdy `Option Strict` jest `Off`oraz `expression1` lub `expression2` jest `Object` wyrażenia, typy środowiska wykonawczego określają, jak są one porównywane.</span><span class="sxs-lookup"><span data-stu-id="a9f01-170">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="a9f01-171">W poniższej tabeli przedstawiono, jak są porównywane wyrażeń i wynik porównania, zależnie od typu środowiska uruchomieniowego argumenty operacji.</span><span class="sxs-lookup"><span data-stu-id="a9f01-171">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>  
  
|<span data-ttu-id="a9f01-172">W przypadku argumentów operacji</span><span class="sxs-lookup"><span data-stu-id="a9f01-172">If operands are</span></span>|<span data-ttu-id="a9f01-173">Wynik porównania ma</span><span class="sxs-lookup"><span data-stu-id="a9f01-173">Comparison is</span></span>|  
|---------------------|-------------------|  
|<span data-ttu-id="a9f01-174">Zarówno`String`</span><span class="sxs-lookup"><span data-stu-id="a9f01-174">Both `String`</span></span>|<span data-ttu-id="a9f01-175">Aby posortować porównań opartych na ciąg sortowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="a9f01-175">Sort comparison based on string sorting characteristics.</span></span>|  
|<span data-ttu-id="a9f01-176">Zarówno liczbowe</span><span class="sxs-lookup"><span data-stu-id="a9f01-176">Both numeric</span></span>|<span data-ttu-id="a9f01-177">Obiekty konwertowane na `Double`, porównanie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="a9f01-177">Objects converted to `Double`, numeric comparison.</span></span>|  
|<span data-ttu-id="a9f01-178">Jeden numeryczne i jeden`String`</span><span class="sxs-lookup"><span data-stu-id="a9f01-178">One numeric and one `String`</span></span>|<span data-ttu-id="a9f01-179">`String` Jest konwertowana na `Double` i wykonywane jest porównanie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="a9f01-179">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="a9f01-180">Jeśli `String` nie można przekonwertować na `Double`, <xref:System.InvalidCastException> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="a9f01-180">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|  
|<span data-ttu-id="a9f01-181">Jedno lub obydwa są typy referencyjne innych niż`String`</span><span class="sxs-lookup"><span data-stu-id="a9f01-181">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="a9f01-182"><xref:System.InvalidCastException> Jest generowany.</span><span class="sxs-lookup"><span data-stu-id="a9f01-182">An <xref:System.InvalidCastException> is thrown.</span></span>|  
  
 <span data-ttu-id="a9f01-183">Traktuj porównanie liczbowe `Nothing` jako 0.</span><span class="sxs-lookup"><span data-stu-id="a9f01-183">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="a9f01-184">Porównywanie ciągów Traktuj `Nothing` jako `""` (ciągiem pustym).</span><span class="sxs-lookup"><span data-stu-id="a9f01-184">String comparisons treat `Nothing` as `""` (an empty string).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a9f01-185">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="a9f01-185">Overloading</span></span>  
 <span data-ttu-id="a9f01-186">Operatory relacyjne (`<`.</span><span class="sxs-lookup"><span data-stu-id="a9f01-186">The relational comparison operators (`<`.</span></span> <span data-ttu-id="a9f01-187">`<=``>`, `>=`, `=`, `<>`) może być *przeciążony*, co oznacza, że klasy lub struktury można zmienić ich zachowania, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="a9f01-187">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a9f01-188">Jeśli kod używa żadnego z tych operatorów dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowanie.</span><span class="sxs-lookup"><span data-stu-id="a9f01-188">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="a9f01-189">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a9f01-189">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
 <span data-ttu-id="a9f01-190">Zwróć uwagę, że [= — Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) może być przeciążona tylko jako operator porównania relacyjne, a nie jako operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="a9f01-190">Notice that the [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9f01-191">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9f01-191">Example</span></span>  
 <span data-ttu-id="a9f01-192">W poniższym przykładzie przedstawiono różnych zastosowań operatory porównania relacyjne, które umożliwia porównywanie wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="a9f01-192">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="a9f01-193">Operatory relacyjne porównania zwracać `Boolean` wynik, który reprezentuje czy podane wyrażenie daje w wyniku `True`.</span><span class="sxs-lookup"><span data-stu-id="a9f01-193">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="a9f01-194">Po zastosowaniu `>` i `<` operatory ciągów, porównując przy użyciu normalnego alfabetycznie sortowania ciągi.</span><span class="sxs-lookup"><span data-stu-id="a9f01-194">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="a9f01-195">To zamówienie mogą być zależne od ustawienia regionalne.</span><span class="sxs-lookup"><span data-stu-id="a9f01-195">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="a9f01-196">Sortowanie jest rozróżniana wielkość liter i nie jest zależna od [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) ustawienie.</span><span class="sxs-lookup"><span data-stu-id="a9f01-196">Whether the sort is case-sensitive or not depends on the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) setting.</span></span>  
  
 [!code-vb[VbVbalrOperators#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 <span data-ttu-id="a9f01-197">W powyższym przykładzie zwraca pierwszy porównanie `False` i zwracać pozostałych porównań `True`.</span><span class="sxs-lookup"><span data-stu-id="a9f01-197">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9f01-198">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9f01-198">See Also</span></span>  
 <xref:System.InvalidCastException>  
 [<span data-ttu-id="a9f01-199">= — Operator</span><span class="sxs-lookup"><span data-stu-id="a9f01-199">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [<span data-ttu-id="a9f01-200">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a9f01-200">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="a9f01-201">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="a9f01-201">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="a9f01-202">Rozwiązywanie problemów z typów danych</span><span class="sxs-lookup"><span data-stu-id="a9f01-202">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="a9f01-203">Operatory porównania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a9f01-203">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
