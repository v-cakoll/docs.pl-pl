---
title: "Typy o wartości zerowalnej (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8734114b9d657066a0ef0b2d648f0290c03b1cbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="ac317-102">Typy o wartości zerowalnej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac317-102">Nullable Value Types (Visual Basic)</span></span>
<span data-ttu-id="ac317-103">Czasami użytkownik pracuje z typem wartości, która nie ma zdefiniowanej wartości w pewnych okolicznościach.</span><span class="sxs-lookup"><span data-stu-id="ac317-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="ac317-104">Na przykład pola w bazie danych może być konieczne rozróżnienia o przypisane wartości, który jest łatwy do rozpoznania i nie ma przypisanej wartości.</span><span class="sxs-lookup"><span data-stu-id="ac317-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="ac317-105">Typy wartości można rozszerzyć ich normalne wartości lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="ac317-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="ac317-106">Przedłużenie jest nazywany *typ dopuszczający wartość null*.</span><span class="sxs-lookup"><span data-stu-id="ac317-106">Such an extension is called a *nullable type*.</span></span>  
  
 <span data-ttu-id="ac317-107">Każdy typ dopuszczający wartość null jest utworzone na podstawie ogólnego <xref:System.Nullable%601> struktury.</span><span class="sxs-lookup"><span data-stu-id="ac317-107">Each nullable type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="ac317-108">Należy wziąć pod uwagę służący do śledzenia działań związanych z pracą bazy danych.</span><span class="sxs-lookup"><span data-stu-id="ac317-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="ac317-109">Poniższy przykład tworzy nullable `Boolean` wpisz i deklaruje zmienną tego typu.</span><span class="sxs-lookup"><span data-stu-id="ac317-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="ac317-110">Deklaracja może zapisać trzy sposoby:</span><span class="sxs-lookup"><span data-stu-id="ac317-110">You can write the declaration in three ways:</span></span>  
  
 [!code-vb[VbVbalrNullableValue#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_1.vb)]  
  
 <span data-ttu-id="ac317-111">Zmienna `ridesBusToWork` może zawierać wartości `True`, wartość `False`, lub nie wartości we wszystkich.</span><span class="sxs-lookup"><span data-stu-id="ac317-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="ac317-112">Wartość domyślną początkowej mają żadnej wartości, które w tym przypadku może oznaczać, że informacje nie ma jeszcze uzyskać tej osoby.</span><span class="sxs-lookup"><span data-stu-id="ac317-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="ac317-113">Z kolei `False` może oznaczać, że uzyskano informacje, a osoby nie które wywołują magistrali do pracy.</span><span class="sxs-lookup"><span data-stu-id="ac317-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>  
  
 <span data-ttu-id="ac317-114">Można zadeklarować zmienne i właściwości z typów dopuszczających wartości zerowe i można zadeklarować tablicy z elementami typu dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="ac317-114">You can declare variables and properties with nullable types, and you can declare an array with elements of a nullable type.</span></span> <span data-ttu-id="ac317-115">Można zadeklarować procedur z typy dopuszczające wartości null jako parametry, a można zwrócić wartości null typu z `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="ac317-115">You can declare procedures with nullable types as parameters, and you can return a nullable type from a `Function` procedure.</span></span>  
  
 <span data-ttu-id="ac317-116">Nie można skonstruować typu dopuszczającego wartość null na typ referencyjny, takich jak tablicy, `String`, lub klasy.</span><span class="sxs-lookup"><span data-stu-id="ac317-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="ac317-117">Typ podstawowy musi być typem wartości.</span><span class="sxs-lookup"><span data-stu-id="ac317-117">The underlying type must be a value type.</span></span> <span data-ttu-id="ac317-118">Aby uzyskać więcej informacji, zobacz [typów wartości i typy referencyjne](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="ac317-118">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="ac317-119">Użycie zmiennej typu dopuszczającego wartość null</span><span class="sxs-lookup"><span data-stu-id="ac317-119">Using a Nullable Type Variable</span></span>  
 <span data-ttu-id="ac317-120">Najważniejsze elementy członkowskie typu dopuszczającego wartości null są jego <xref:System.Nullable%601.HasValue%2A> i <xref:System.Nullable%601.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ac317-120">The most important members of a nullable type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="ac317-121">Dla zmiennej typu dopuszczającego wartość null <xref:System.Nullable%601.HasValue%2A> informuje, czy zmienna zawiera zdefiniowanej wartości.</span><span class="sxs-lookup"><span data-stu-id="ac317-121">For a variable of a nullable type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="ac317-122">Jeśli <xref:System.Nullable%601.HasValue%2A> jest `True`, można odczytać wartości z <xref:System.Nullable%601.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="ac317-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="ac317-123">Należy pamiętać, że oba <xref:System.Nullable%601.HasValue%2A> i <xref:System.Nullable%601.Value%2A> są `ReadOnly` właściwości.</span><span class="sxs-lookup"><span data-stu-id="ac317-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>  
  
### <a name="default-values"></a><span data-ttu-id="ac317-124">Wartości domyślne</span><span class="sxs-lookup"><span data-stu-id="ac317-124">Default Values</span></span>  
 <span data-ttu-id="ac317-125">Deklaracja zmiennej typu dopuszczającego wartość null, jego <xref:System.Nullable%601.HasValue%2A> właściwość ma wartość domyślną równą `False`.</span><span class="sxs-lookup"><span data-stu-id="ac317-125">When you declare a variable with a nullable type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="ac317-126">Oznacza to, że domyślnie zmienna nie ma zdefiniowanej wartości, zamiast wartości domyślnej z jego typem podstawowym wartość.</span><span class="sxs-lookup"><span data-stu-id="ac317-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="ac317-127">W poniższym przykładzie zmienna `numberOfChildren` początkowo nie ma zdefiniowanej wartości, nawet jeśli wartość domyślną `Integer` typ jest 0.</span><span class="sxs-lookup"><span data-stu-id="ac317-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_2.vb)]  
  
 <span data-ttu-id="ac317-128">Wartość null jest wskazuje niezdefiniowaną lub nieznaną wartość.</span><span class="sxs-lookup"><span data-stu-id="ac317-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="ac317-129">Jeśli `numberOfChildren` zadeklarowano jako `Integer`, nie byłoby żadna wartość, która może wskazywać, że informacje nie są obecnie dostępne.</span><span class="sxs-lookup"><span data-stu-id="ac317-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>  
  
### <a name="storing-values"></a><span data-ttu-id="ac317-130">Przechowywanie wartości</span><span class="sxs-lookup"><span data-stu-id="ac317-130">Storing Values</span></span>  
 <span data-ttu-id="ac317-131">Wartości są przechowywane w zmiennej lub właściwości typu dopuszczającego wartość null w typowy sposób.</span><span class="sxs-lookup"><span data-stu-id="ac317-131">You store a value in a variable or property of a nullable type in the typical way.</span></span> <span data-ttu-id="ac317-132">Poniższy przykład przypisuje wartość do zmiennej `numberOfChildren` zadeklarowany w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ac317-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#3](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_3.vb)]  
  
 <span data-ttu-id="ac317-133">Zmienna lub właściwość typu dopuszczającego wartość null, zawiera wartość zdefiniowane, może spowodować jej powraca do stanu początkowego wyeliminowanie konieczności przypisaną wartość.</span><span class="sxs-lookup"><span data-stu-id="ac317-133">If a variable or property of a nullable type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="ac317-134">Możesz to zrobić przez ustawienie zmiennej lub właściwości do `Nothing`, jak pokazano na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ac317-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#4](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_4.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="ac317-135">Chociaż można przypisać `Nothing` do zmiennej typu dopuszczającego wartość null, nie można przetestować go dla `Nothing` przy użyciu znaku równości.</span><span class="sxs-lookup"><span data-stu-id="ac317-135">Although you can assign `Nothing` to a variable of a nullable type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="ac317-136">Porównanie, które używa znaku równości `someVar = Nothing`, zawsze daje w wyniku `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ac317-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="ac317-137">Można przetestować zmiennej <xref:System.Nullable%601.HasValue%2A> właściwość `False`, lub testowania przy użyciu `Is` lub `IsNot` operatora.</span><span class="sxs-lookup"><span data-stu-id="ac317-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>  
  
### <a name="retrieving-values"></a><span data-ttu-id="ac317-138">Pobieranie wartości</span><span class="sxs-lookup"><span data-stu-id="ac317-138">Retrieving Values</span></span>  
 <span data-ttu-id="ac317-139">Można pobrać wartości zmiennej typu dopuszczającego wartość null, należy najpierw przetestować jego <xref:System.Nullable%601.HasValue%2A> właściwości, aby upewnić się, że ma ona wartość.</span><span class="sxs-lookup"><span data-stu-id="ac317-139">To retrieve the value of a variable of a nullable type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="ac317-140">Jeśli użytkownik próbuje odczytać wartości podczas <xref:System.Nullable%601.HasValue%2A> jest `False`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zgłasza <xref:System.InvalidOperationException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ac317-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="ac317-141">W poniższym przykładzie przedstawiono zalecany sposób odczytać zmiennej `numberOfChildren` poprzednich przykładach.</span><span class="sxs-lookup"><span data-stu-id="ac317-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#5](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_5.vb)]  
  
## <a name="comparing-nullable-types"></a><span data-ttu-id="ac317-142">Porównanie typów dopuszczających wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="ac317-142">Comparing Nullable Types</span></span>  
 <span data-ttu-id="ac317-143">W przypadku wartości null `Boolean` zmienne są używane w wyrażeniach logicznych, może to spowodować powstanie `True`, `False`, lub `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ac317-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="ac317-144">Poniżej znajduje się Tabela prawdy dla `And` i `Or`.</span><span class="sxs-lookup"><span data-stu-id="ac317-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="ac317-145">Ponieważ `b1` i `b2` już trzema możliwymi wartościami są dziewięć kombinacji do oceny.</span><span class="sxs-lookup"><span data-stu-id="ac317-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>  
  
|<span data-ttu-id="ac317-146">B1</span><span class="sxs-lookup"><span data-stu-id="ac317-146">b1</span></span>|<span data-ttu-id="ac317-147">B2</span><span class="sxs-lookup"><span data-stu-id="ac317-147">b2</span></span>|<span data-ttu-id="ac317-148">B1 i b2</span><span class="sxs-lookup"><span data-stu-id="ac317-148">b1 And b2</span></span>|<span data-ttu-id="ac317-149">B1 lub b2</span><span class="sxs-lookup"><span data-stu-id="ac317-149">b1 Or b2</span></span>|  
|--------|--------|---------------|--------------|  
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|  
|`Nothing`|`True`|`Nothing`|`True`|  
|`Nothing`|`False`|`False`|`Nothing`|  
|`True`|`Nothing`|`Nothing`|`True`|  
|`True`|`True`|`True`|`True`|  
|`True`|`False`|`False`|`True`|  
|`False`|`Nothing`|`False`|`Nothing`|  
|`False`|`True`|`False`|`True`|  
|`False`|`False`|`False`|`False`|  
  
 <span data-ttu-id="ac317-150">Gdy jest wartość logiczna lub wyrażenie `Nothing`, nie jest `true` ani `false`.</span><span class="sxs-lookup"><span data-stu-id="ac317-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="ac317-151">Rozważmy następujący przykład.</span><span class="sxs-lookup"><span data-stu-id="ac317-151">Consider the following example.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#6](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_6.vb)]  
  
 <span data-ttu-id="ac317-152">W tym przykładzie `b1 And b2` daje w wyniku `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ac317-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="ac317-153">W związku z tym `Else` klauzuli jest wykonywana w każdym `If` instrukcji i dane wyjściowe wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="ac317-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  <span data-ttu-id="ac317-154">`AndAlso`i `OrElse`, wykorzystującymi zwarcia oceny, musi mieć drugi operandy po pierwszym daje w wyniku `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ac317-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>  
  
## <a name="propagation"></a><span data-ttu-id="ac317-155">Propagacja</span><span class="sxs-lookup"><span data-stu-id="ac317-155">Propagation</span></span>  
 <span data-ttu-id="ac317-156">Jeśli jeden lub oba argumenty operacji arytmetyczne, porównania, shift lub typ operacji jest wartość null, wynik operacji jest również wartości null.</span><span class="sxs-lookup"><span data-stu-id="ac317-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is nullable, the result of the operation is also nullable.</span></span> <span data-ttu-id="ac317-157">Jeśli oba argumenty mają wartości, które nie są `Nothing`, operacja jest wykonywana na wartości podstawowych argumentów operacji, tak, jakby nie był typ dopuszczający wartość null.</span><span class="sxs-lookup"><span data-stu-id="ac317-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable type.</span></span> <span data-ttu-id="ac317-158">W poniższym przykładzie, zmienne `compare1` i `sum1` niejawnie wpisywania.</span><span class="sxs-lookup"><span data-stu-id="ac317-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="ac317-159">Jeśli wskaźnik myszy nad nimi, zobaczysz, że kompilator wnioskuje typy dopuszczające wartości null dla obu z nich.</span><span class="sxs-lookup"><span data-stu-id="ac317-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable types for both of them.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#7](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_7.vb)]  
  
 <span data-ttu-id="ac317-160">Jeśli jeden lub oba argumenty mają wartość `Nothing`, wynikiem będzie `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ac317-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#8](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_8.vb)]  
  
## <a name="using-nullable-types-with-data"></a><span data-ttu-id="ac317-161">Używanie typów dopuszczających wartości zerowe z danymi</span><span class="sxs-lookup"><span data-stu-id="ac317-161">Using Nullable Types with Data</span></span>  
 <span data-ttu-id="ac317-162">Baza danych jest jednym z najważniejszych miejsc, można używać typu dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="ac317-162">A database is one of the most important places to use nullable types.</span></span> <span data-ttu-id="ac317-163">Nie wszystkie obiekty bazy danych nie obsługiwało typy dopuszczające wartości null, ale nie adaptery wygenerowany przez projektanta tabel.</span><span class="sxs-lookup"><span data-stu-id="ac317-163">Not all database objects currently support nullable types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="ac317-164">Sekcja "Obsługa TableAdapter typy dopuszczające wartości zerowe" w [TableAdapter — Przegląd](/visualstudio/data-tools/tableadapter-overview).</span><span class="sxs-lookup"><span data-stu-id="ac317-164">See "TableAdapter Support for Nullable Types" in [TableAdapter Overview](/visualstudio/data-tools/tableadapter-overview).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac317-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ac317-165">See Also</span></span>  
 <xref:System.InvalidOperationException>  
 <xref:System.Nullable%601.HasValue%2A>  
 [<span data-ttu-id="ac317-166">Przy użyciu typów dopuszczających wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="ac317-166">Using Nullable Types</span></span>](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
 [<span data-ttu-id="ac317-167">Typy danych</span><span class="sxs-lookup"><span data-stu-id="ac317-167">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="ac317-168">Typy wartości i typy referencyjne</span><span class="sxs-lookup"><span data-stu-id="ac317-168">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="ac317-169">Rozwiązywanie problemów z typów danych</span><span class="sxs-lookup"><span data-stu-id="ac317-169">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="ac317-170">TableAdapter — Przegląd</span><span class="sxs-lookup"><span data-stu-id="ac317-170">TableAdapter Overview</span></span>](/visualstudio/data-tools/tableadapter-overview)  
 [<span data-ttu-id="ac317-171">Jeśli — Operator</span><span class="sxs-lookup"><span data-stu-id="ac317-171">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="ac317-172">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="ac317-172">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="ac317-173">Is — Operator</span><span class="sxs-lookup"><span data-stu-id="ac317-173">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="ac317-174">IsNot — Operator</span><span class="sxs-lookup"><span data-stu-id="ac317-174">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)
