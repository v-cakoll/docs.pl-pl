---
title: Typy o wartości zerowalnej
ms.date: 07/20/2015
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
ms.openlocfilehash: beed8262c50dc68330b8f03aa3d864ed2f8df0d5
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249685"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="d6684-102">Typy o wartości zerowalnej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6684-102">Nullable Value Types (Visual Basic)</span></span>

<span data-ttu-id="d6684-103">Czasami pracujesz z typem wartości, który nie ma zdefiniowanej wartości w pewnych okolicznościach.</span><span class="sxs-lookup"><span data-stu-id="d6684-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="d6684-104">Na przykład pole w bazie danych może być konieczności rozróżnienia między o przypisanej wartości, która ma znaczenie i nie ma przypisanej wartości.</span><span class="sxs-lookup"><span data-stu-id="d6684-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="d6684-105">Typy wartości można rozszerzyć, aby wziąć ich wartości normalne lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="d6684-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="d6684-106">Takie rozszerzenie jest nazywane *typem nullable*.</span><span class="sxs-lookup"><span data-stu-id="d6684-106">Such an extension is called a *nullable type*.</span></span>

<span data-ttu-id="d6684-107">Każdy typ wartości nullable jest <xref:System.Nullable%601> konstruowany ze struktury ogólnej.</span><span class="sxs-lookup"><span data-stu-id="d6684-107">Each nullable value type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="d6684-108">Należy wziąć pod uwagę bazę danych, która śledzi działania związane z pracą.</span><span class="sxs-lookup"><span data-stu-id="d6684-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="d6684-109">Poniższy przykład konstruuje `Boolean` typ nullable i deklaruje zmienną tego typu.</span><span class="sxs-lookup"><span data-stu-id="d6684-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="d6684-110">Deklarację można napisać na trzy sposoby:</span><span class="sxs-lookup"><span data-stu-id="d6684-110">You can write the declaration in three ways:</span></span>

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

<span data-ttu-id="d6684-111">Zmienna `ridesBusToWork` może zawierać `True`wartość , `False`wartość , lub w ogóle nie.</span><span class="sxs-lookup"><span data-stu-id="d6684-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="d6684-112">Jego początkowa wartość domyślna nie jest wcale wartością, co w tym przypadku może oznaczać, że informacje nie zostały jeszcze uzyskane dla tej osoby.</span><span class="sxs-lookup"><span data-stu-id="d6684-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="d6684-113">W przeciwieństwie `False` do tego, może to oznaczać, że informacje zostały uzyskane, a osoba nie jedzie autobusem do pracy.</span><span class="sxs-lookup"><span data-stu-id="d6684-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>

<span data-ttu-id="d6684-114">Można zadeklarować zmienne i właściwości z typami wartości nullable i można zadeklarować tablicę z elementami typu wartości nullable.</span><span class="sxs-lookup"><span data-stu-id="d6684-114">You can declare variables and properties with nullable value types, and you can declare an array with elements of a nullable value type.</span></span> <span data-ttu-id="d6684-115">Można zadeklarować procedury z typami wartości nullable jako parametry i `Function` można zwrócić typ wartości nullable z procedury.</span><span class="sxs-lookup"><span data-stu-id="d6684-115">You can declare procedures with nullable value types as parameters, and you can return a nullable value type from a `Function` procedure.</span></span>

<span data-ttu-id="d6684-116">Nie można skonstruować typu nullable na typ odwołania, takich jak tablica, `String`, lub klasy.</span><span class="sxs-lookup"><span data-stu-id="d6684-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="d6684-117">Typ podstawowy musi być typem wartości.</span><span class="sxs-lookup"><span data-stu-id="d6684-117">The underlying type must be a value type.</span></span> <span data-ttu-id="d6684-118">Aby uzyskać więcej informacji, zobacz [Typy wartości i Typy odwołań](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="d6684-118">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>

## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="d6684-119">Korzystanie ze zmiennej typu możliwego do wartości null</span><span class="sxs-lookup"><span data-stu-id="d6684-119">Using a Nullable Type Variable</span></span>

<span data-ttu-id="d6684-120">Najważniejszymi elementami elementów członkowskich typu <xref:System.Nullable%601.HasValue%2A> <xref:System.Nullable%601.Value%2A> wartości możliwego do wartości null są jego i właściwości.</span><span class="sxs-lookup"><span data-stu-id="d6684-120">The most important members of a nullable value type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="d6684-121">Dla zmiennej typu wartości możliwej do wartości null informuje, <xref:System.Nullable%601.HasValue%2A> czy zmienna zawiera zdefiniowaną wartość.</span><span class="sxs-lookup"><span data-stu-id="d6684-121">For a variable of a nullable value type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="d6684-122">Jeśli <xref:System.Nullable%601.HasValue%2A> `True`tak, można odczytać <xref:System.Nullable%601.Value%2A>wartość z .</span><span class="sxs-lookup"><span data-stu-id="d6684-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="d6684-123">Należy zauważyć, <xref:System.Nullable%601.Value%2A> `ReadOnly` że oba <xref:System.Nullable%601.HasValue%2A> i są właściwości.</span><span class="sxs-lookup"><span data-stu-id="d6684-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>

### <a name="default-values"></a><span data-ttu-id="d6684-124">Wartości domyślne</span><span class="sxs-lookup"><span data-stu-id="d6684-124">Default Values</span></span>

<span data-ttu-id="d6684-125">Podczas deklarowania zmiennej z typem <xref:System.Nullable%601.HasValue%2A> wartości możliwej do `False`wartości null jej właściwość ma wartość domyślną .</span><span class="sxs-lookup"><span data-stu-id="d6684-125">When you declare a variable with a nullable value type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="d6684-126">Oznacza to, że domyślnie zmienna nie ma zdefiniowanej wartości, zamiast wartości domyślnej jej typa wartości podstawowej.</span><span class="sxs-lookup"><span data-stu-id="d6684-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="d6684-127">W poniższym przykładzie `numberOfChildren` zmienna początkowo nie ma zdefiniowanej `Integer` wartości, nawet jeśli domyślną wartością typu jest 0.</span><span class="sxs-lookup"><span data-stu-id="d6684-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

<span data-ttu-id="d6684-128">Wartość null jest przydatna do wskazania wartości niezdefiniowanej lub nieznanej.</span><span class="sxs-lookup"><span data-stu-id="d6684-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="d6684-129">Gdyby `numberOfChildren` został zadeklarowany jako `Integer`, nie byłoby żadnej wartości, która mogłaby wskazywać, że informacje nie są obecnie dostępne.</span><span class="sxs-lookup"><span data-stu-id="d6684-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>

### <a name="storing-values"></a><span data-ttu-id="d6684-130">Przechowywanie wartości</span><span class="sxs-lookup"><span data-stu-id="d6684-130">Storing Values</span></span>

<span data-ttu-id="d6684-131">Wartość jest przechowywana w zmiennej lub właściwości typu wartości nullable w typowy sposób.</span><span class="sxs-lookup"><span data-stu-id="d6684-131">You store a value in a variable or property of a nullable value type in the typical way.</span></span> <span data-ttu-id="d6684-132">Poniższy przykład przypisuje wartość do `numberOfChildren` zmiennej zadeklarowanej w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d6684-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

<span data-ttu-id="d6684-133">Jeśli zmienna lub właściwość typu wartości możliwej do wartości null zawiera zdefiniowaną wartość, może spowodować, że powróci do stanu początkowego, który nie ma przypisanej wartości.</span><span class="sxs-lookup"><span data-stu-id="d6684-133">If a variable or property of a nullable value type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="d6684-134">Można to zrobić, ustawiając `Nothing`zmienną lub właściwość na , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d6684-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> <span data-ttu-id="d6684-135">Chociaż można `Nothing` przypisać do zmiennej typu wartości nullable, `Nothing` nie można przetestować go za pomocą znaku równości.</span><span class="sxs-lookup"><span data-stu-id="d6684-135">Although you can assign `Nothing` to a variable of a nullable value type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="d6684-136">Porównanie, które używa znaku `someVar = Nothing`równości, zawsze `Nothing`ocenia .</span><span class="sxs-lookup"><span data-stu-id="d6684-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="d6684-137">Właściwość zmiennej można przetestować pod kątem `False` `Is` , lub przetestować za pomocą operatora lub. `IsNot` <xref:System.Nullable%601.HasValue%2A></span><span class="sxs-lookup"><span data-stu-id="d6684-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>

### <a name="retrieving-values"></a><span data-ttu-id="d6684-138">Pobieranie wartości</span><span class="sxs-lookup"><span data-stu-id="d6684-138">Retrieving Values</span></span>

<span data-ttu-id="d6684-139">Aby pobrać wartość zmiennej typu wartości możliwej do wartości <xref:System.Nullable%601.HasValue%2A> null, należy najpierw przetestować jej właściwość, aby potwierdzić, że ma wartość.</span><span class="sxs-lookup"><span data-stu-id="d6684-139">To retrieve the value of a variable of a nullable value type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="d6684-140">Jeśli spróbujesz odczytać <xref:System.Nullable%601.HasValue%2A> wartość, gdy jest `False` <xref:System.InvalidOperationException> , Visual Basic zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d6684-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="d6684-141">W poniższym przykładzie przedstawiono `numberOfChildren` zalecany sposób odczytywania zmiennej poprzednich przykładów.</span><span class="sxs-lookup"><span data-stu-id="d6684-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a><span data-ttu-id="d6684-142">Porównywanie typów powodujących wartość null</span><span class="sxs-lookup"><span data-stu-id="d6684-142">Comparing Nullable Types</span></span>

<span data-ttu-id="d6684-143">Gdy zmienne `Boolean` nullowalne są używane w wyrażeniach `True` `False`logicznych, wynikiem może być , lub `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="d6684-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="d6684-144">Poniżej znajduje się `And` tabela prawdy dla i `Or`.</span><span class="sxs-lookup"><span data-stu-id="d6684-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="d6684-145">Ponieważ `b1` `b2` i teraz mają trzy możliwe wartości, istnieje dziewięć kombinacji do oceny.</span><span class="sxs-lookup"><span data-stu-id="d6684-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>

|<span data-ttu-id="d6684-146">b1</span><span class="sxs-lookup"><span data-stu-id="d6684-146">b1</span></span>|<span data-ttu-id="d6684-147">B2</span><span class="sxs-lookup"><span data-stu-id="d6684-147">b2</span></span>|<span data-ttu-id="d6684-148">b1 I b2</span><span class="sxs-lookup"><span data-stu-id="d6684-148">b1 And b2</span></span>|<span data-ttu-id="d6684-149">b1 Lub b2</span><span class="sxs-lookup"><span data-stu-id="d6684-149">b1 Or b2</span></span>|
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

<span data-ttu-id="d6684-150">Gdy wartość zmiennej logicznej lub `Nothing`wyrażenia jest `true` , `false`nie jest ani, ani .</span><span class="sxs-lookup"><span data-stu-id="d6684-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="d6684-151">Rozważmy następujący przykład.</span><span class="sxs-lookup"><span data-stu-id="d6684-151">Consider the following example.</span></span>

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

<span data-ttu-id="d6684-152">W tym `b1 And b2` przykładzie `Nothing`ocenia .</span><span class="sxs-lookup"><span data-stu-id="d6684-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="d6684-153">W rezultacie klauzula `Else` jest wykonywana `If` w każdej instrukcji, a dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="d6684-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>

`Expression is not true`

`Expression is not false`

> [!NOTE]
> <span data-ttu-id="d6684-154">`AndAlso`i `OrElse`, które korzystają z oceny zwarcia, muszą ocenić `Nothing`swoje drugie argumenty, gdy pierwszy ocenia.</span><span class="sxs-lookup"><span data-stu-id="d6684-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>

## <a name="propagation"></a><span data-ttu-id="d6684-155">Propagacja</span><span class="sxs-lookup"><span data-stu-id="d6684-155">Propagation</span></span>

<span data-ttu-id="d6684-156">Jeśli jeden lub oba argumenty operacji arytmetycznej, porównania, przesunięcia lub typu jest typem wartości możliwej do wartości null, wynikiem operacji jest również typ wartości powodującej wartość null.</span><span class="sxs-lookup"><span data-stu-id="d6684-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is a nullable value type, the result of the operation is also a nullable value type.</span></span> <span data-ttu-id="d6684-157">Jeśli oba argumenty mają wartości, `Nothing`które nie są, operacja jest wykonywana na podstawowych wartości operands, tak jakby nie były typu wartości nullable.</span><span class="sxs-lookup"><span data-stu-id="d6684-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable value type.</span></span> <span data-ttu-id="d6684-158">W poniższym przykładzie `compare1` `sum1` zmienne i są niejawnie wpisane.</span><span class="sxs-lookup"><span data-stu-id="d6684-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="d6684-159">Jeśli opierasz wskaźnik myszy na nich, zobaczysz, że kompilator wnioskuje nullable typów wartości dla obu z nich.</span><span class="sxs-lookup"><span data-stu-id="d6684-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable value types for both of them.</span></span>

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

<span data-ttu-id="d6684-160">Jeśli jeden lub oba argumenty mają `Nothing`wartość , `Nothing`wynik będzie .</span><span class="sxs-lookup"><span data-stu-id="d6684-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a><span data-ttu-id="d6684-161">Używanie typów nullable z danymi</span><span class="sxs-lookup"><span data-stu-id="d6684-161">Using Nullable Types with Data</span></span>

<span data-ttu-id="d6684-162">Baza danych jest jednym z najważniejszych miejsc do użycia typów wartości nullable.</span><span class="sxs-lookup"><span data-stu-id="d6684-162">A database is one of the most important places to use nullable value types.</span></span> <span data-ttu-id="d6684-163">Nie wszystkie obiekty bazy danych obsługują obecnie typy wartości nullable, ale karty tabel generowane przez projektanta zrobić.</span><span class="sxs-lookup"><span data-stu-id="d6684-163">Not all database objects currently support nullable value types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="d6684-164">Zobacz [TableAdapter wsparcie dla typów nullable](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span><span class="sxs-lookup"><span data-stu-id="d6684-164">See [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="d6684-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6684-165">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="d6684-166">Typy danych</span><span class="sxs-lookup"><span data-stu-id="d6684-166">Data Types</span></span>](index.md)
- [<span data-ttu-id="d6684-167">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="d6684-167">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="d6684-168">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="d6684-168">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="d6684-169">Wypełnianie zestawów danych za pomocą adapterów TableAdapter</span><span class="sxs-lookup"><span data-stu-id="d6684-169">Fill datasets by using TableAdapters</span></span>](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [<span data-ttu-id="d6684-170">If, operator</span><span class="sxs-lookup"><span data-stu-id="d6684-170">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
- [<span data-ttu-id="d6684-171">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="d6684-171">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="d6684-172">Is, operator</span><span class="sxs-lookup"><span data-stu-id="d6684-172">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="d6684-173">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="d6684-173">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="d6684-174">Typy wartości z dopuszczalną wartości (C#)</span><span class="sxs-lookup"><span data-stu-id="d6684-174">Nullable Value Types (C#)</span></span>](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
