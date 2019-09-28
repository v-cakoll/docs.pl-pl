---
title: Typy wartości null-Visual Basic
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
ms.openlocfilehash: 072496a560775a8f79274f1d44dd389d6ed5b40d
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351762"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="9d127-102">Typy o wartości zerowalnej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d127-102">Nullable Value Types (Visual Basic)</span></span>

<span data-ttu-id="9d127-103">Czasami pracujesz z typem wartości, który nie ma zdefiniowanej wartości w pewnych okolicznościach.</span><span class="sxs-lookup"><span data-stu-id="9d127-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="9d127-104">Na przykład w przypadku pola w bazie danych może być konieczne odróżnienie od posiadania przypisanej wartości, która jest istotna i nie ma przypisanej wartości.</span><span class="sxs-lookup"><span data-stu-id="9d127-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="9d127-105">Typy wartości można rozszerzyć, aby przyjmować ich normalne wartości lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="9d127-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="9d127-106">Takie rozszerzenie jest nazywane *typem dopuszczającym wartość null*.</span><span class="sxs-lookup"><span data-stu-id="9d127-106">Such an extension is called a *nullable type*.</span></span>

<span data-ttu-id="9d127-107">Każdy typ dopuszczający wartość null jest konstruowany z ogólnej struktury <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="9d127-107">Each nullable type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="9d127-108">Rozważmy bazę danych, która śledzi działania związane z pracą.</span><span class="sxs-lookup"><span data-stu-id="9d127-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="9d127-109">Poniższy przykład tworzy wartość null typu `Boolean` i deklaruje zmienną tego typu.</span><span class="sxs-lookup"><span data-stu-id="9d127-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="9d127-110">Deklarację można napisać na trzy sposoby:</span><span class="sxs-lookup"><span data-stu-id="9d127-110">You can write the declaration in three ways:</span></span>

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

<span data-ttu-id="9d127-111">Zmienna `ridesBusToWork` może mieć wartość `True`, wartość `False` lub brak wartości.</span><span class="sxs-lookup"><span data-stu-id="9d127-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="9d127-112">Jego początkowa wartość domyślna nie jest wcale, co w tym przypadku może oznaczać, że informacje nie zostały jeszcze uzyskane dla tej osoby.</span><span class="sxs-lookup"><span data-stu-id="9d127-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="9d127-113">W przeciwieństwie do `False` może oznaczać, że informacje zostały uzyskane i osoba nie przełączy magistrali do pracy.</span><span class="sxs-lookup"><span data-stu-id="9d127-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>

<span data-ttu-id="9d127-114">Można zadeklarować zmienne i właściwości z typami dopuszczających wartość null i można zadeklarować tablicę z elementami typu dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="9d127-114">You can declare variables and properties with nullable types, and you can declare an array with elements of a nullable type.</span></span> <span data-ttu-id="9d127-115">Można zadeklarować procedury z typami dopuszczających wartość null jako parametry, a typ dopuszczający wartość null można zwrócić z procedury `Function`.</span><span class="sxs-lookup"><span data-stu-id="9d127-115">You can declare procedures with nullable types as parameters, and you can return a nullable type from a `Function` procedure.</span></span>

<span data-ttu-id="9d127-116">Nie można skonstruować typu dopuszczającego wartość null w typie referencyjnym, takim jak tablica, `String` lub Klasa.</span><span class="sxs-lookup"><span data-stu-id="9d127-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="9d127-117">Typ podstawowy musi być typem wartości.</span><span class="sxs-lookup"><span data-stu-id="9d127-117">The underlying type must be a value type.</span></span> <span data-ttu-id="9d127-118">Aby uzyskać więcej informacji, zobacz [typy wartości i typy odwołań](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="9d127-118">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>

## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="9d127-119">Użycie zmiennej typu dopuszczającego wartość null</span><span class="sxs-lookup"><span data-stu-id="9d127-119">Using a Nullable Type Variable</span></span>

<span data-ttu-id="9d127-120">Najważniejszymi elementami członkowskimi typu dopuszczającego wartość null są właściwości <xref:System.Nullable%601.HasValue%2A> i <xref:System.Nullable%601.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="9d127-120">The most important members of a nullable type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="9d127-121">Dla zmiennej typu dopuszczającego wartość null, <xref:System.Nullable%601.HasValue%2A> informuje, czy zmienna zawiera zdefiniowaną wartość.</span><span class="sxs-lookup"><span data-stu-id="9d127-121">For a variable of a nullable type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="9d127-122">Jeśli <xref:System.Nullable%601.HasValue%2A> jest `True`, można odczytać wartość z <xref:System.Nullable%601.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="9d127-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="9d127-123">Należy zauważyć, że obie <xref:System.Nullable%601.HasValue%2A> i <xref:System.Nullable%601.Value%2A> są właściwościami `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="9d127-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>

### <a name="default-values"></a><span data-ttu-id="9d127-124">Wartości domyślne</span><span class="sxs-lookup"><span data-stu-id="9d127-124">Default Values</span></span>

<span data-ttu-id="9d127-125">Po zadeklarowaniu zmiennej z typem dopuszczającym wartość null, jej Właściwość <xref:System.Nullable%601.HasValue%2A> ma wartość domyślną `False`.</span><span class="sxs-lookup"><span data-stu-id="9d127-125">When you declare a variable with a nullable type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="9d127-126">Oznacza to, że domyślnie zmienna nie ma zdefiniowanej wartości, a nie wartości domyślnej jej bazowego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="9d127-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="9d127-127">W poniższym przykładzie zmienna `numberOfChildren` początkowo nie ma zdefiniowanej wartości, mimo że wartość domyślna typu `Integer` wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="9d127-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

<span data-ttu-id="9d127-128">Wartość null jest przydatna do wskazania niezdefiniowanej lub nieznanej wartości.</span><span class="sxs-lookup"><span data-stu-id="9d127-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="9d127-129">Jeśli `numberOfChildren` został zadeklarowany jako `Integer`, nie byłoby żadnej wartości, która może wskazywać, że informacje nie są obecnie dostępne.</span><span class="sxs-lookup"><span data-stu-id="9d127-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>

### <a name="storing-values"></a><span data-ttu-id="9d127-130">Przechowywanie wartości</span><span class="sxs-lookup"><span data-stu-id="9d127-130">Storing Values</span></span>

<span data-ttu-id="9d127-131">W typowy sposób przechowujesz wartość w zmiennej lub właściwości typu dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="9d127-131">You store a value in a variable or property of a nullable type in the typical way.</span></span> <span data-ttu-id="9d127-132">Poniższy przykład przypisuje wartość do zmiennej `numberOfChildren` zadeklarowane w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9d127-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

<span data-ttu-id="9d127-133">Jeśli zmienna lub właściwość typu Nullable zawiera zdefiniowaną wartość, można spowodować przywrócenie stanu początkowego nieprzypisanej wartości.</span><span class="sxs-lookup"><span data-stu-id="9d127-133">If a variable or property of a nullable type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="9d127-134">W tym celu należy ustawić zmienną lub właściwość na `Nothing`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9d127-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> <span data-ttu-id="9d127-135">Chociaż można przypisać `Nothing` do zmiennej typu dopuszczającego wartość null, nie można go przetestować dla `Nothing` przy użyciu znaku równości.</span><span class="sxs-lookup"><span data-stu-id="9d127-135">Although you can assign `Nothing` to a variable of a nullable type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="9d127-136">Porównanie, które używa znaku równości, `someVar = Nothing`, zawsze jest obliczane do `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="9d127-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="9d127-137">Można przetestować Właściwość <xref:System.Nullable%601.HasValue%2A> zmiennej dla `False` lub test przy użyciu operatora `Is` lub `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="9d127-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>

### <a name="retrieving-values"></a><span data-ttu-id="9d127-138">Pobieranie wartości</span><span class="sxs-lookup"><span data-stu-id="9d127-138">Retrieving Values</span></span>

<span data-ttu-id="9d127-139">Aby pobrać wartość zmiennej typu Nullable, należy najpierw przetestować jej <xref:System.Nullable%601.HasValue%2A> właściwość, aby potwierdzić, że ma wartość.</span><span class="sxs-lookup"><span data-stu-id="9d127-139">To retrieve the value of a variable of a nullable type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="9d127-140">Jeśli spróbujesz odczytać wartość, gdy <xref:System.Nullable%601.HasValue%2A> jest `False`, Visual Basic zgłasza wyjątek <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="9d127-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="9d127-141">W poniższym przykładzie przedstawiono zalecany sposób odczytywania zmiennej `numberOfChildren` z poprzednich przykładów.</span><span class="sxs-lookup"><span data-stu-id="9d127-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a><span data-ttu-id="9d127-142">Porównywanie typów dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="9d127-142">Comparing Nullable Types</span></span>

<span data-ttu-id="9d127-143">Gdy wartości null są używane w wyrażeniach logicznych `Boolean`, wynik może być `True`, `False` lub `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="9d127-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="9d127-144">Poniżej przedstawiono tabelę prawdziwą dla `And` i `Or`.</span><span class="sxs-lookup"><span data-stu-id="9d127-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="9d127-145">Ponieważ `b1` i `b2` ma teraz trzy możliwe wartości, istnieje dziewięć kombinacji do obliczenia.</span><span class="sxs-lookup"><span data-stu-id="9d127-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>

|<span data-ttu-id="9d127-146">b1</span><span class="sxs-lookup"><span data-stu-id="9d127-146">b1</span></span>|<span data-ttu-id="9d127-147">b2</span><span class="sxs-lookup"><span data-stu-id="9d127-147">b2</span></span>|<span data-ttu-id="9d127-148">B1 i B2</span><span class="sxs-lookup"><span data-stu-id="9d127-148">b1 And b2</span></span>|<span data-ttu-id="9d127-149">B1 lub B2</span><span class="sxs-lookup"><span data-stu-id="9d127-149">b1 Or b2</span></span>|
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

<span data-ttu-id="9d127-150">Gdy wartość zmiennej lub wyrażenia logicznego jest `Nothing`, nie jest `true` ani `false`.</span><span class="sxs-lookup"><span data-stu-id="9d127-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="9d127-151">Rozważmy następujący przykład.</span><span class="sxs-lookup"><span data-stu-id="9d127-151">Consider the following example.</span></span>

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

<span data-ttu-id="9d127-152">W tym przykładzie `b1 And b2` szacuje się na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="9d127-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="9d127-153">W efekcie klauzula `Else` jest wykonywana w każdej instrukcji `If`, a dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="9d127-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>

`Expression is not true`

`Expression is not false`

> [!NOTE]
> <span data-ttu-id="9d127-154">`AndAlso` i `OrElse`, które korzystają z oceny krótkiego obwodu, muszą ocenić dwa operandy, gdy pierwsze szacuje się na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="9d127-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>

## <a name="propagation"></a><span data-ttu-id="9d127-155">Propagacja</span><span class="sxs-lookup"><span data-stu-id="9d127-155">Propagation</span></span>

<span data-ttu-id="9d127-156">Jeśli jeden lub oba operandy operacji arytmetycznych, porównywania, przesunięcia lub typu mają wartość null, wynik operacji również dopuszcza wartość null.</span><span class="sxs-lookup"><span data-stu-id="9d127-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is nullable, the result of the operation is also nullable.</span></span> <span data-ttu-id="9d127-157">Jeśli oba operandy mają wartości, które nie są `Nothing`, operacja jest wykonywana na podstawowych wartościach operandów, tak jakby nie były typem dopuszczającym wartość null.</span><span class="sxs-lookup"><span data-stu-id="9d127-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable type.</span></span> <span data-ttu-id="9d127-158">W poniższym przykładzie zmienne `compare1` i `sum1` są wpisane niejawnie.</span><span class="sxs-lookup"><span data-stu-id="9d127-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="9d127-159">Jeśli umieścisz wskaźnik myszy nad nimi, zobaczysz, że kompilator wnioskuje Typy dopuszczające wartość null dla obu tych elementów.</span><span class="sxs-lookup"><span data-stu-id="9d127-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable types for both of them.</span></span>

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

<span data-ttu-id="9d127-160">Jeśli jeden lub oba operandy mają wartość `Nothing`, wynik będzie `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="9d127-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a><span data-ttu-id="9d127-161">Używanie typów dopuszczających wartości null z danymi</span><span class="sxs-lookup"><span data-stu-id="9d127-161">Using Nullable Types with Data</span></span>

<span data-ttu-id="9d127-162">Baza danych jest jednym z najważniejszych miejsc, w których można używać typów dopuszczających wartość null.</span><span class="sxs-lookup"><span data-stu-id="9d127-162">A database is one of the most important places to use nullable types.</span></span> <span data-ttu-id="9d127-163">Nie wszystkie obiekty bazy danych obsługują obecnie Typy dopuszczające wartość null, ale adaptery tabeli generowane przez projektanta.</span><span class="sxs-lookup"><span data-stu-id="9d127-163">Not all database objects currently support nullable types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="9d127-164">Zobacz [TableAdapter support for nullable Types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span><span class="sxs-lookup"><span data-stu-id="9d127-164">See [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d127-165">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d127-165">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="9d127-166">Typy danych</span><span class="sxs-lookup"><span data-stu-id="9d127-166">Data Types</span></span>](index.md)
- [<span data-ttu-id="9d127-167">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="9d127-167">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="9d127-168">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="9d127-168">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="9d127-169">Wypełnianie zestawów danych za pomocą adapterów TableAdapter</span><span class="sxs-lookup"><span data-stu-id="9d127-169">Fill datasets by using TableAdapters</span></span>](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [<span data-ttu-id="9d127-170">If, operator</span><span class="sxs-lookup"><span data-stu-id="9d127-170">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
- [<span data-ttu-id="9d127-171">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="9d127-171">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="9d127-172">Is, operator</span><span class="sxs-lookup"><span data-stu-id="9d127-172">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="9d127-173">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="9d127-173">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="9d127-174">Używanie typów wartości null (C#)</span><span class="sxs-lookup"><span data-stu-id="9d127-174">Using Nullable Value Types (C#)</span></span>](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
