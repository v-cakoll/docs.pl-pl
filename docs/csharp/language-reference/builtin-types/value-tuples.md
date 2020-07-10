---
title: Typy krotek — odwołanie w C#
description: 'Dowiedz się więcej o kolekcjach języka C#: lekkie struktury danych, których można użyć do grupowania luźno powiązanych elementów danych'
ms.date: 07/09/2020
helpviewer_keywords:
- value tuples [C#]
ms.openlocfilehash: 3d79ab19117847e2364b154db33a1521416bb3f4
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174992"
---
# <a name="tuple-types-c-reference"></a><span data-ttu-id="2ea16-103">Typy krotek (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="2ea16-103">Tuple types (C# reference)</span></span>

<span data-ttu-id="2ea16-104">Dostępna w języku C# 7,0 i nowszych funkcja *kroteks* oferuje zwięzłą składnię do grupowania wielu elementów danych w lekkiej strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="2ea16-104">Available in C# 7.0 and later, the *tuples* feature provides concise syntax to group multiple data elements in a lightweight data structure.</span></span> <span data-ttu-id="2ea16-105">Poniższy przykład pokazuje, jak można zadeklarować zmienną krotki, zainicjować ją i uzyskać dostęp do jej członków danych:</span><span class="sxs-lookup"><span data-stu-id="2ea16-105">The following example shows how you can declare a tuple variable, initialize it, and access its data members:</span></span>

[!code-csharp-interactive[tuple intro](snippets/ValueTuples.cs#Introduction)]

<span data-ttu-id="2ea16-106">Jak pokazano w powyższym przykładzie, aby zdefiniować typ krotki, należy określić typy wszystkich elementów członkowskich danych i, opcjonalnie, [nazwy pól](#tuple-field-names).</span><span class="sxs-lookup"><span data-stu-id="2ea16-106">As the preceding example shows, to define a tuple type, you specify types of all its data members and, optionally, the [field names](#tuple-field-names).</span></span> <span data-ttu-id="2ea16-107">Nie można definiować metod w typie krotki, ale można użyć metod dostarczonych przez platformę .NET, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2ea16-107">You cannot define methods in a tuple type, but you can use the methods provided by .NET, as the following example shows:</span></span>

[!code-csharp-interactive[tuple methods](snippets/ValueTuples.cs#MethodOnTuples)]

<span data-ttu-id="2ea16-108">Począwszy od języka C# 7,3, typy krotek obsługują [Operatory równości](../operators/equality-operators.md) `==` i `!=` .</span><span class="sxs-lookup"><span data-stu-id="2ea16-108">Beginning with C# 7.3, tuple types support [equality operators](../operators/equality-operators.md) `==` and `!=`.</span></span> <span data-ttu-id="2ea16-109">Aby uzyskać więcej informacji, zobacz sekcję [równość krotki](#tuple-equality) .</span><span class="sxs-lookup"><span data-stu-id="2ea16-109">For more information, see the [Tuple equality](#tuple-equality) section.</span></span>

<span data-ttu-id="2ea16-110">Typy krotek to [typy wartości](value-types.md); elementy krotki są polami publicznymi.</span><span class="sxs-lookup"><span data-stu-id="2ea16-110">Tuple types are [value types](value-types.md); tuple elements are public fields.</span></span> <span data-ttu-id="2ea16-111">Sprawia, że typy wartości *modyfikowalnych* krotek.</span><span class="sxs-lookup"><span data-stu-id="2ea16-111">That makes tuples *mutable* value types.</span></span>

> [!NOTE]
> <span data-ttu-id="2ea16-112">Funkcja krotek wymaga <xref:System.ValueTuple?displayProperty=nameWithType> typu i pokrewnych typów ogólnych (na przykład <xref:System.ValueTuple%602?displayProperty=nameWithType> ), które są dostępne w oprogramowaniu .NET Core i .NET Framework 4,7 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="2ea16-112">The tuples feature requires the <xref:System.ValueTuple?displayProperty=nameWithType> type and related generic types (for example, <xref:System.ValueTuple%602?displayProperty=nameWithType>), which are available in .NET Core and .NET Framework 4.7 and later.</span></span> <span data-ttu-id="2ea16-113">Aby używać krotek w projekcie, który jest celem .NET Framework 4.6.2 lub wcześniejszym, Dodaj pakiet NuGet [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) do projektu.</span><span class="sxs-lookup"><span data-stu-id="2ea16-113">To use tuples in a project that targets .NET Framework 4.6.2 or earlier, add the NuGet package [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) to the project.</span></span>

<span data-ttu-id="2ea16-114">Można definiować krotki z dowolną dużą liczbą elementów:</span><span class="sxs-lookup"><span data-stu-id="2ea16-114">You can define tuples with an arbitrary large number of elements:</span></span>

[!code-csharp-interactive[large tuple](snippets/ValueTuples.cs#LargeTuple)]

## <a name="use-cases-of-tuples"></a><span data-ttu-id="2ea16-115">Przypadki użycia krotek</span><span class="sxs-lookup"><span data-stu-id="2ea16-115">Use cases of tuples</span></span>

<span data-ttu-id="2ea16-116">Jednym z najczęstszych przypadków użycia krotek jest jako zwracany typ metody.</span><span class="sxs-lookup"><span data-stu-id="2ea16-116">One of the most common use cases of tuples is as a method return type.</span></span> <span data-ttu-id="2ea16-117">Oznacza to, że zamiast definiować [ `out` Parametry metody](../keywords/out-parameter-modifier.md), można grupować wyniki metody w typie zwracanym spójnej kolekcji, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2ea16-117">That is, instead of defining [`out` method parameters](../keywords/out-parameter-modifier.md), you can group method results in a tuple return type, as the following example shows:</span></span>

[!code-csharp-interactive[multiple method outputs](snippets/ValueTuples.cs#MultipleReturns)]

<span data-ttu-id="2ea16-118">Jak pokazano w powyższym przykładzie, można współpracować z zwracanym wystąpieniem krotki bezpośrednio lub [dekonstruować](#tuple-assignment-and-deconstruction) go w oddzielnych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="2ea16-118">As the preceding example shows, you can work with the returned tuple instance directly or [deconstruct](#tuple-assignment-and-deconstruction) it in separate variables.</span></span>

<span data-ttu-id="2ea16-119">Można również użyć typów krotek zamiast [typów anonimowych](../../programming-guide/classes-and-structs/anonymous-types.md); na przykład w zapytaniach LINQ.</span><span class="sxs-lookup"><span data-stu-id="2ea16-119">You can also use tuple types instead of [anonymous types](../../programming-guide/classes-and-structs/anonymous-types.md); for example, in LINQ queries.</span></span> <span data-ttu-id="2ea16-120">Aby uzyskać więcej informacji, zobacz [Wybieranie typów anonimowych i krotek](../../../standard/base-types/choosing-between-anonymous-and-tuple.md).</span><span class="sxs-lookup"><span data-stu-id="2ea16-120">For more information, see [Choosing between anonymous and tuple types](../../../standard/base-types/choosing-between-anonymous-and-tuple.md).</span></span>

<span data-ttu-id="2ea16-121">Zwykle można używać krotek do grupowania luźno powiązanych elementów danych.</span><span class="sxs-lookup"><span data-stu-id="2ea16-121">Typically, you use tuples to group loosely related data elements.</span></span> <span data-ttu-id="2ea16-122">Jest to zazwyczaj przydatne w przypadku prywatnych i wewnętrznych metod narzędziowych.</span><span class="sxs-lookup"><span data-stu-id="2ea16-122">That is usually useful within private and internal utility methods.</span></span> <span data-ttu-id="2ea16-123">W przypadku publicznego interfejsu API Rozważ zdefiniowanie [klasy](../keywords/class.md) lub typu [struktury](struct.md) .</span><span class="sxs-lookup"><span data-stu-id="2ea16-123">In the case of public API, consider defining a [class](../keywords/class.md) or a [structure](struct.md) type.</span></span>

## <a name="tuple-field-names"></a><span data-ttu-id="2ea16-124">Nazwy pól krotki</span><span class="sxs-lookup"><span data-stu-id="2ea16-124">Tuple field names</span></span>

<span data-ttu-id="2ea16-125">Można jawnie określić nazwy pól spójnych w wyrażeniu inicjowania krotki lub w definicji typu krotki, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2ea16-125">You can explicitly specify the names of tuple fields either in a tuple initialization expression or in the definition of a tuple type, as the following example shows:</span></span>

[!code-csharp-interactive[explicit field names](snippets/ValueTuples.cs#ExplicitFieldNames)]

<span data-ttu-id="2ea16-126">Począwszy od języka C# 7,1, jeśli nie określisz nazwy pola, można wywnioskować ją z nazwy odpowiadającej zmiennej w wyrażeniu inicjowania kolekcji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2ea16-126">Beginning with C# 7.1, if you don't specify a field name, it may be inferred from the name of the corresponding variable in a tuple initialization expression, as the following example shows:</span></span>

[!code-csharp-interactive[inferred field names](snippets/ValueTuples.cs#InferFieldNames)]

<span data-ttu-id="2ea16-127">Są to znane jako inicjatory projekcji krotki.</span><span class="sxs-lookup"><span data-stu-id="2ea16-127">That's known as tuple projection initializers.</span></span> <span data-ttu-id="2ea16-128">Nazwa zmiennej nie jest rzutowana na nazwę pola krotki w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="2ea16-128">The name of a variable isn't projected onto a tuple field name in the following cases:</span></span>

- <span data-ttu-id="2ea16-129">Nazwa kandydata to nazwa elementu członkowskiego typu krotki, na przykład,, `Item3` `ToString` lub `Rest` .</span><span class="sxs-lookup"><span data-stu-id="2ea16-129">The candidate name is a member name of a tuple type, for example, `Item3`, `ToString`, or `Rest`.</span></span>
- <span data-ttu-id="2ea16-130">Nazwa kandydata jest duplikatem innej nazwy pola krotki, jawnej lub niejawnej.</span><span class="sxs-lookup"><span data-stu-id="2ea16-130">The candidate name is a duplicate of another tuple field name, either explicit or implicit.</span></span>

<span data-ttu-id="2ea16-131">W takich przypadkach można jawnie określić nazwę pola lub uzyskać dostęp do pola według jego nazwy domyślnej.</span><span class="sxs-lookup"><span data-stu-id="2ea16-131">In those cases you either explicitly specify the name of a field or access a field by its default name.</span></span>

<span data-ttu-id="2ea16-132">Domyślne nazwy pól krotki są `Item1` , `Item2` , `Item3` i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="2ea16-132">The default names of tuple fields are `Item1`, `Item2`, `Item3` and so on.</span></span> <span data-ttu-id="2ea16-133">Zawsze możesz użyć domyślnej nazwy pola, nawet jeśli nazwa pola jest określona jawnie lub wywnioskowana, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2ea16-133">You can always use the default name of a field, even when a field name is specified explicitly or inferred, as the following example shows:</span></span>

[!code-csharp-interactive[default field names](snippets/ValueTuples.cs#DefaultFieldNames)]

<span data-ttu-id="2ea16-134">Porównanie [kolekcji](#tuple-assignment-and-deconstruction) i [równości krotek](#tuple-equality) nie przyjmuje nazw pól w ramach konta.</span><span class="sxs-lookup"><span data-stu-id="2ea16-134">[Tuple assignment](#tuple-assignment-and-deconstruction) and [tuple equality comparisons](#tuple-equality) don't take field names into account.</span></span>

<span data-ttu-id="2ea16-135">W czasie kompilacji kompilator zastępuje nazwy pól inne niż domyślne odpowiednimi nazwami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="2ea16-135">At compile time, the compiler replaces non-default field names with the corresponding default names.</span></span> <span data-ttu-id="2ea16-136">W związku z tym jawnie określone lub wywnioskowane nazwy pól nie są dostępne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2ea16-136">As a result, explicitly specified or inferred field names aren't available at run time.</span></span>

## <a name="tuple-assignment-and-deconstruction"></a><span data-ttu-id="2ea16-137">Przypisanie krotki i dekonstrukcja</span><span class="sxs-lookup"><span data-stu-id="2ea16-137">Tuple assignment and deconstruction</span></span>

<span data-ttu-id="2ea16-138">Język C# obsługuje przypisanie między typami krotek, które spełniają oba z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="2ea16-138">C# supports assignment between tuple types that satisfy both of the following conditions:</span></span>

- <span data-ttu-id="2ea16-139">Oba typy krotek mają tę samą liczbę elementów</span><span class="sxs-lookup"><span data-stu-id="2ea16-139">both tuple types have the same number of elements</span></span>
- <span data-ttu-id="2ea16-140">dla każdej pozycji krotki typ elementu krotki po prawej stronie jest taki sam jak lub niejawnie konwertowany na typ odpowiadającego elementu krotki po lewej stronie</span><span class="sxs-lookup"><span data-stu-id="2ea16-140">for each tuple position, the type of the right-hand tuple element is the same as or implicitly convertible to the type of the corresponding left-hand tuple element</span></span>

<span data-ttu-id="2ea16-141">Wartości elementu krotki są przypisywane po kolejności elementów krotki.</span><span class="sxs-lookup"><span data-stu-id="2ea16-141">Tuple element values are assigned following the order of tuple elements.</span></span> <span data-ttu-id="2ea16-142">Nazwy pól krotek są ignorowane i nie są przypisywane, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2ea16-142">The names of tuple fields are ignored and not assigned, as the following example shows:</span></span>

[!code-csharp-interactive[tuple assignment](snippets/ValueTuples.cs#Assignment)]

<span data-ttu-id="2ea16-143">Można również użyć operatora przypisania, `=` Aby wypróbować wystąpienie krotki w oddzielnych zmiennych. *deconstruct*</span><span class="sxs-lookup"><span data-stu-id="2ea16-143">You can also use the assignment operator `=` to *deconstruct* a tuple instance in separate variables.</span></span> <span data-ttu-id="2ea16-144">Można to zrobić w jeden z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="2ea16-144">You can do that in one of the following ways:</span></span>

- <span data-ttu-id="2ea16-145">Jawnie Zadeklaruj typ każdej zmiennej w nawiasach:</span><span class="sxs-lookup"><span data-stu-id="2ea16-145">Explicitly declare the type of each variable inside parentheses:</span></span>

  [!code-csharp-interactive[specify types of variables](snippets/ValueTuples.cs#DeconstructExplicit)]

- <span data-ttu-id="2ea16-146">Użyj `var` słowa kluczowego poza nawiasami, aby zadeklarować zmienne niejawnie wpisane i pozwolić kompilatorowi na wnioskowanie typów:</span><span class="sxs-lookup"><span data-stu-id="2ea16-146">Use the `var` keyword outside the parentheses to declare implicitly typed variables and let the compiler infer their types:</span></span>

  [!code-csharp-interactive[implicitly typed variables](snippets/ValueTuples.cs#DeconstructVar)]

- <span data-ttu-id="2ea16-147">Użyj istniejących zmiennych:</span><span class="sxs-lookup"><span data-stu-id="2ea16-147">Use existing variables:</span></span>

  [!code-csharp-interactive[existing variables](snippets/ValueTuples.cs#DeconstructExisting)]

<span data-ttu-id="2ea16-148">Aby uzyskać więcej informacji na temat dekonstrukcji krotek i innych typów, zobacz [dekonstrukcja kroteks i innych typów](../../deconstruct.md).</span><span class="sxs-lookup"><span data-stu-id="2ea16-148">For more information about deconstruction of tuples and other types, see [Deconstructing tuples and other types](../../deconstruct.md).</span></span>

## <a name="tuple-equality"></a><span data-ttu-id="2ea16-149">Równość krotki</span><span class="sxs-lookup"><span data-stu-id="2ea16-149">Tuple equality</span></span>

<span data-ttu-id="2ea16-150">Począwszy od języka C# 7,3, typy krotek obsługują `==` `!=` Operatory i.</span><span class="sxs-lookup"><span data-stu-id="2ea16-150">Beginning with C# 7.3, tuple types support the `==` and `!=` operators.</span></span> <span data-ttu-id="2ea16-151">Te operatory porównują elementy członkowskie operandu po lewej stronie z odpowiednimi elementami członkowskimi operandu po prawej stronie po kolejności elementów krotki.</span><span class="sxs-lookup"><span data-stu-id="2ea16-151">These operators compare members of the left-hand operand with the corresponding members of the right-hand operand following the order of tuple elements.</span></span>

[!code-csharp-interactive[tuple equality](snippets/ValueTuples.cs#TupleEquality)]

<span data-ttu-id="2ea16-152">Jak pokazano w powyższym przykładzie `==` , `!=` operacje i nie uwzględniają nazw pól krotki.</span><span class="sxs-lookup"><span data-stu-id="2ea16-152">As the preceding example shows, the `==` and `!=` operations don't take into account tuple field names.</span></span>

<span data-ttu-id="2ea16-153">Dwie krotki są porównywalne, gdy spełnione są oba z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="2ea16-153">Two tuples are comparable when both of the following conditions are satisfied:</span></span>

- <span data-ttu-id="2ea16-154">Obie krotki mają tę samą liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="2ea16-154">Both tuples have the same number of elements.</span></span> <span data-ttu-id="2ea16-155">Na przykład, `t1 != t2` nie kompiluje, jeśli `t1` i `t2` mają różne liczby elementów.</span><span class="sxs-lookup"><span data-stu-id="2ea16-155">For example, `t1 != t2` doesn't compile if `t1` and `t2` have different numbers of elements.</span></span>
- <span data-ttu-id="2ea16-156">Dla każdej pozycji krotki odpowiednie elementy z operandów po lewej stronie i po prawej stronie są porównywalne z `==` `!=` operatorami i.</span><span class="sxs-lookup"><span data-stu-id="2ea16-156">For each tuple position, the corresponding elements from the left-hand and right-hand tuple operands are comparable with the `==` and `!=` operators.</span></span> <span data-ttu-id="2ea16-157">Na przykład `(1, (2, 3)) == ((1, 2), 3)` nie kompiluje się, ponieważ `1` nie jest porównywalna z `(1, 2)` .</span><span class="sxs-lookup"><span data-stu-id="2ea16-157">For example, `(1, (2, 3)) == ((1, 2), 3)` doesn't compile because `1` is not comparable with `(1, 2)`.</span></span>

<span data-ttu-id="2ea16-158">`==`Operatory i `!=` porównują krotki w sposób skrócony obwodu.</span><span class="sxs-lookup"><span data-stu-id="2ea16-158">The `==` and `!=` operators compare tuples in short-circuiting way.</span></span> <span data-ttu-id="2ea16-159">Oznacza to, że operacja zostaje zatrzymana, gdy tylko spełni parę elementów nierównych lub osiąga końce krotek.</span><span class="sxs-lookup"><span data-stu-id="2ea16-159">That is, an operation stops as soon as it meets a pair of non equal elements or reaches the ends of tuples.</span></span> <span data-ttu-id="2ea16-160">Jednak przed jakimkolwiek porównaniem *wszystkie* elementy krotki są oceniane, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2ea16-160">However, before any comparison, *all* tuple elements are evaluated, as the following example shows:</span></span>

[!code-csharp-interactive[tuple element evaluation](snippets/ValueTuples.cs#TupleEvaluationForEquality)]

## <a name="tuples-as-out-parameters"></a><span data-ttu-id="2ea16-161">Krotki jako parametry out</span><span class="sxs-lookup"><span data-stu-id="2ea16-161">Tuples as out parameters</span></span>

<span data-ttu-id="2ea16-162">Zazwyczaj refaktoryzacja jest metoda, która ma [ `out` Parametry](../keywords/out-parameter-modifier.md) w metodzie zwracającej krotkę.</span><span class="sxs-lookup"><span data-stu-id="2ea16-162">Typically, you refactor a method that has [`out` parameters](../keywords/out-parameter-modifier.md) into a method that returns a tuple.</span></span> <span data-ttu-id="2ea16-163">Istnieją jednak przypadki, w których `out` parametr może być typu krotki.</span><span class="sxs-lookup"><span data-stu-id="2ea16-163">However, there are cases in which an `out` parameter can be of a tuple type.</span></span> <span data-ttu-id="2ea16-164">Poniższy przykład pokazuje, jak używać krotek jako `out` parametrów:</span><span class="sxs-lookup"><span data-stu-id="2ea16-164">The following example shows how to work with tuples as `out` parameters:</span></span>

[!code-csharp-interactive[tuple as out parameter](snippets/ValueTuples.cs#TupleAsOutParameter)]

## <a name="tuples-vs-systemtuple"></a><span data-ttu-id="2ea16-165">Krotki a`System.Tuple`</span><span class="sxs-lookup"><span data-stu-id="2ea16-165">Tuples vs `System.Tuple`</span></span>

<span data-ttu-id="2ea16-166">Krotki języka C#, które są obsługiwane przez <xref:System.ValueTuple?displayProperty=nameWithType> typy, różnią się od krotek, które są reprezentowane przez <xref:System.Tuple?displayProperty=nameWithType> typy.</span><span class="sxs-lookup"><span data-stu-id="2ea16-166">C# tuples, which are backed by <xref:System.ValueTuple?displayProperty=nameWithType> types, are different from tuples that are represented by <xref:System.Tuple?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="2ea16-167">Główne różnice są następujące:</span><span class="sxs-lookup"><span data-stu-id="2ea16-167">The main differences are as follows:</span></span>

- <span data-ttu-id="2ea16-168">`ValueTuple`typy są [typami wartości](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="2ea16-168">`ValueTuple` types are [value types](value-types.md).</span></span> <span data-ttu-id="2ea16-169">`Tuple`typy to [typy odwołań](../keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="2ea16-169">`Tuple` types are [reference types](../keywords/reference-types.md).</span></span>
- <span data-ttu-id="2ea16-170">`ValueTuple`typy są modyfikowalne.</span><span class="sxs-lookup"><span data-stu-id="2ea16-170">`ValueTuple` types are mutable.</span></span> <span data-ttu-id="2ea16-171">`Tuple`typy są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="2ea16-171">`Tuple` types are immutable.</span></span>
- <span data-ttu-id="2ea16-172">Elementy członkowskie danych `ValueTuple` typów są polami.</span><span class="sxs-lookup"><span data-stu-id="2ea16-172">Data members of `ValueTuple` types are fields.</span></span> <span data-ttu-id="2ea16-173">Elementy członkowskie danych `Tuple` typów są właściwościami.</span><span class="sxs-lookup"><span data-stu-id="2ea16-173">Data members of `Tuple` types are properties.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2ea16-174">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2ea16-174">C# language specification</span></span>

<span data-ttu-id="2ea16-175">Aby uzyskać więcej informacji, zobacz następujące uwagi dotyczące propozycji funkcji:</span><span class="sxs-lookup"><span data-stu-id="2ea16-175">For more information, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="2ea16-176">Wywnioskowanie nazw krotek (aliasy projekcji w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2ea16-176">Infer tuple names (aka. tuple projection initializers)</span></span>](~/_csharplang/proposals/csharp-7.1/infer-tuple-names.md)
- [<span data-ttu-id="2ea16-177">Obsługa `==` typów krotek i dla nich `!=`</span><span class="sxs-lookup"><span data-stu-id="2ea16-177">Support for `==` and `!=` on tuple types</span></span>](~/_csharplang/proposals/csharp-7.3/tuple-equality.md)

## <a name="see-also"></a><span data-ttu-id="2ea16-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ea16-178">See also</span></span>

- [<span data-ttu-id="2ea16-179">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2ea16-179">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2ea16-180">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="2ea16-180">Value types</span></span>](value-types.md)
- [<span data-ttu-id="2ea16-181">Wybór między typami anonimowymi a kolekcjami</span><span class="sxs-lookup"><span data-stu-id="2ea16-181">Choosing between anonymous and tuple types</span></span>](../../../standard/base-types/choosing-between-anonymous-and-tuple.md)
- <xref:System.ValueTuple?displayProperty=nameWithType>
