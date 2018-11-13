---
title: Krotki (F#)
description: Więcej informacji na temat F# krotki, grupowanie bez nazwy, ale uporządkowane wartości, prawdopodobnie różnych typów.
ms.date: 05/16/2016
ms.openlocfilehash: e7628e4c4b538c2fe52fca25d2597b10fec28d1c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43749226"
---
# <a name="tuples"></a><span data-ttu-id="e541a-103">Krotki</span><span class="sxs-lookup"><span data-stu-id="e541a-103">Tuples</span></span>

<span data-ttu-id="e541a-104">A *krotki* to zbiór wartości bez nazwy, ale uporządkowanym, prawdopodobnie różnych typów.</span><span class="sxs-lookup"><span data-stu-id="e541a-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="e541a-105">Kolekcje mogą być typami odwołań lub struktury.</span><span class="sxs-lookup"><span data-stu-id="e541a-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="e541a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e541a-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a><span data-ttu-id="e541a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e541a-107">Remarks</span></span>

<span data-ttu-id="e541a-108">Każdy *elementu* w poprzedniej składni może być dowolnym prawidłowym wyrażeniem języka F#.</span><span class="sxs-lookup"><span data-stu-id="e541a-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="e541a-109">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e541a-109">Examples</span></span>

<span data-ttu-id="e541a-110">Przykładami krotek pary, trójek i tak dalej, tych samych lub różnych typów.</span><span class="sxs-lookup"><span data-stu-id="e541a-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="e541a-111">Niektóre przykłady zostały zilustrowane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e541a-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a><span data-ttu-id="e541a-112">Uzyskiwanie poszczególne wartości</span><span class="sxs-lookup"><span data-stu-id="e541a-112">Obtaining Individual Values</span></span>

<span data-ttu-id="e541a-113">Dopasowanie do wzorca można użyć dostępu i przypisać nazwy elementów krotki, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e541a-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="e541a-114">Można również dekonstruować krotki za pomocą dopasowywania do wzorca poza `match` wyrażenia za pośrednictwem `let` powiązania:</span><span class="sxs-lookup"><span data-stu-id="e541a-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="e541a-115">Lub można wzorca dopasowania krotek jako dane wejściowe do funkcji:</span><span class="sxs-lookup"><span data-stu-id="e541a-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="e541a-116">Jeśli potrzebujesz tylko jeden element krotki symbol wieloznaczny (podkreślenie) można uniknąć, tworząc nową nazwę dla wartości, która nie ma potrzeby.</span><span class="sxs-lookup"><span data-stu-id="e541a-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="e541a-117">Kopiowanie elementów z krotki odwołania do krotki struktury również jest prosty:</span><span class="sxs-lookup"><span data-stu-id="e541a-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="e541a-118">Funkcje `fst` i `snd` (odwoływać się tylko krotek) zwraca pierwszy i drugi elementów krotki, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="e541a-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="e541a-119">Nie ma wbudowanych funkcji zwracającą trzeci element triple, ale łatwe napisania jednego w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="e541a-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="e541a-120">Ogólnie rzecz biorąc lepiej jest dostęp do elementów poszczególne krotki z za pomocą dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="e541a-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="e541a-121">Możliwość korzystania z krotek</span><span class="sxs-lookup"><span data-stu-id="e541a-121">Using Tuples</span></span>

<span data-ttu-id="e541a-122">Spójne kolekcje zapewniają wygodny sposób wielu wartości zwracane przez funkcję, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e541a-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="e541a-123">W tym przykładzie wykonuje dzielenie liczby całkowitej i zwraca zaokrąglony wynik operacji, ponieważ pierwszego elementu członkowskiego pary krotki, jak i resztę jako drugi element członkowski pary.</span><span class="sxs-lookup"><span data-stu-id="e541a-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="e541a-124">Kolekcje można również jako argumenty funkcji uniknąć niejawne currying argumentów funkcji, które jest implikowane przez zwykłe składnię.</span><span class="sxs-lookup"><span data-stu-id="e541a-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="e541a-125">Typowej składni do definiowania funkcji `let sum a b = a + b` pozwala na zdefiniowanie funkcja, która jest częściowym zastosowaniem pierwszy argument funkcji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e541a-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="e541a-126">Przy użyciu spójnych kolekcji jako parametr wyłącza currying.</span><span class="sxs-lookup"><span data-stu-id="e541a-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="e541a-127">Aby uzyskać więcej informacji, zobacz "Częściowe stosowanie argumentów" w [funkcji](functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="e541a-127">For more information, see "Partial Application of Arguments" in [Functions](functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="e541a-128">Nazwy typów krotki</span><span class="sxs-lookup"><span data-stu-id="e541a-128">Names of Tuple Types</span></span>

<span data-ttu-id="e541a-129">Kiedy piszesz się nazwę typu, który jest spójną kolekcją, możesz użyć `*` symbol do oddzielania elementów.</span><span class="sxs-lookup"><span data-stu-id="e541a-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="e541a-130">Dla spójną kolekcją, która składa się z `int`, `float`, a `string`, takich jak `(10, 10.0, "ten")`, typu, które powinny być zapisane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="e541a-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="e541a-131">Współdziałanie z Krotkami języka C#</span><span class="sxs-lookup"><span data-stu-id="e541a-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="e541a-132">C# 7.0 wprowadzono krotek języka.</span><span class="sxs-lookup"><span data-stu-id="e541a-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="e541a-133">Spójne kolekcje w języku C# są strukturami i są równoważne z krotek struktur w języku F#.</span><span class="sxs-lookup"><span data-stu-id="e541a-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="e541a-134">Jeśli musisz współdziałać z C#, należy użyć krotek struktur.</span><span class="sxs-lookup"><span data-stu-id="e541a-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="e541a-135">Jest to proste.</span><span class="sxs-lookup"><span data-stu-id="e541a-135">This is easy to do.</span></span>  <span data-ttu-id="e541a-136">Załóżmy, że trzeba przekazać krotki do klasy C#, a następnie zużyć je jej wynik, który jest również spójnej kolekcji:</span><span class="sxs-lookup"><span data-stu-id="e541a-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

<span data-ttu-id="e541a-137">W F# kodzie można przekazać krotki struktury jako parametr i korzystać z wynik w postaci krotki struktury.</span><span class="sxs-lookup"><span data-stu-id="e541a-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="e541a-138">Konwertowanie pomiędzy krotek struktur i kolekcje odwołania</span><span class="sxs-lookup"><span data-stu-id="e541a-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="e541a-139">Ponieważ krotek struktur i kolekcje odwołanie całkowicie różnych reprezentacji podstawowych, nie są one niejawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="e541a-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="e541a-140">Oznacza to, że nie będzie kompilacji kodu, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="e541a-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="e541a-141">Należy wzorca dopasowania po jednej krotce i konstruowania, pozostałe części składowe.</span><span class="sxs-lookup"><span data-stu-id="e541a-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="e541a-142">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e541a-142">For example:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="e541a-143">Skompilowanej formy krotek odwołania</span><span class="sxs-lookup"><span data-stu-id="e541a-143">Compiled Form of Reference Tuples</span></span>

<span data-ttu-id="e541a-144">W tej sekcji opisano formularza krotek, gdy są one skompilowane.</span><span class="sxs-lookup"><span data-stu-id="e541a-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="e541a-145">W tym miejscu nie są one niezbędne do odczytu, o ile nie są przeznaczone dla .NET Framework 3.5 lub niższą.</span><span class="sxs-lookup"><span data-stu-id="e541a-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="e541a-146">Kolekcje są kompilowane do jednego z kilku typów ogólnych, wszystkie nazwane obiekty `System.Tuple`, które są przeciążone na liczby argumentów lub liczbę parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="e541a-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="e541a-147">Typy krotek są wyświetlane w tym formularzu, podczas wyświetlania ich w innym języku, takich jak C# lub Visual Basic lub korzystając z narzędzia, która nie ma informacji o konstrukcje F#.</span><span class="sxs-lookup"><span data-stu-id="e541a-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="e541a-148">`Tuple` Typy zostały wprowadzone w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e541a-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="e541a-149">Jeśli jest przeznaczony dla starszej wersji programu .NET Framework, kompilator używa wersji [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) z podstawowej biblioteki języka F# w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="e541a-149">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="e541a-150">Typy w tej bibliotece są używane tylko w przypadku aplikacji przeznaczonych dla wersji 2.0, 3.0 i 3.5 wersje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e541a-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="e541a-151">Przekazywanie dalej typu jest używany w celu zapewnienia zgodność binarną między składnikami programu .NET Framework 2.0 i .NET Framework 4 F#.</span><span class="sxs-lookup"><span data-stu-id="e541a-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="e541a-152">Skompilowanej formy krotek struktur</span><span class="sxs-lookup"><span data-stu-id="e541a-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="e541a-153">Krotek struktur (na przykład `struct (x, y)`), są różni się od krotek odwołania.</span><span class="sxs-lookup"><span data-stu-id="e541a-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="e541a-154">Są one kompilowane do <xref:System.ValueTuple> typu przeciążony przez liczby argumentów lub liczbę parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="e541a-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="e541a-155">Są one równoważnymi [C# 7.0 krotek](../../csharp/tuples.md) i [krotek 2017 Visual Basic](../../visual-basic/programming-guide/language-features/data-types/tuples.md)oraz współpraca dwukierunkowo.</span><span class="sxs-lookup"><span data-stu-id="e541a-155">They are equivalent to [C# 7.0 Tuples](../../csharp/tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="e541a-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e541a-156">See also</span></span>

- [<span data-ttu-id="e541a-157">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="e541a-157">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="e541a-158">Typy F#</span><span class="sxs-lookup"><span data-stu-id="e541a-158">F# Types</span></span>](fsharp-types.md)
