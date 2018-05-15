---
title: Krotki (F#)
description: 'Więcej informacji na temat F # krotki, grupowanie bez nazwy, ale uporządkowanej wartości, prawdopodobnie różnych typów.'
ms.date: 05/16/2016
ms.openlocfilehash: d017a2ce8a6ad9b3cec8dfa2ee15b47f06d8f67c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="tuples"></a><span data-ttu-id="cbb01-103">Krotki</span><span class="sxs-lookup"><span data-stu-id="cbb01-103">Tuples</span></span>

<span data-ttu-id="cbb01-104">A *krotki* to grupa bez nazwy, ale uporządkowanej wartości, prawdopodobnie różnych typów.</span><span class="sxs-lookup"><span data-stu-id="cbb01-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="cbb01-105">Krotki może być typu odwołania lub struktury.</span><span class="sxs-lookup"><span data-stu-id="cbb01-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="cbb01-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="cbb01-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```
## <a name="remarks"></a><span data-ttu-id="cbb01-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cbb01-107">Remarks</span></span>
<span data-ttu-id="cbb01-108">Każdy *elementu* w poprzednim składni może być dowolne prawidłowe wyrażenie F #.</span><span class="sxs-lookup"><span data-stu-id="cbb01-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="cbb01-109">Przykłady</span><span class="sxs-lookup"><span data-stu-id="cbb01-109">Examples</span></span>
<span data-ttu-id="cbb01-110">Przykładami krotek pary, triples i tak dalej, w tym samym lub różnych typów.</span><span class="sxs-lookup"><span data-stu-id="cbb01-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="cbb01-111">Przykłady zostały przedstawione w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="cbb01-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]
    
## <a name="obtaining-individual-values"></a><span data-ttu-id="cbb01-112">Uzyskiwanie poszczególne wartości</span><span class="sxs-lookup"><span data-stu-id="cbb01-112">Obtaining Individual Values</span></span>
<span data-ttu-id="cbb01-113">Umożliwia dopasowanie wzorca dostępu i przypisać nazwy dla spójnej kolekcji elementów, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="cbb01-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="cbb01-114">Można również deconstruct krotka za pomocą dopasowywania do wzorca poza `match` wyrażenia za pośrednictwem `let` powiązania:</span><span class="sxs-lookup"><span data-stu-id="cbb01-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="cbb01-115">Lub może wzorzec dopasowywania w krotek jako dane wejściowe do funkcji:</span><span class="sxs-lookup"><span data-stu-id="cbb01-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="cbb01-116">Tylko jeden element spójnej kolekcji, należy symbol wieloznaczny (podkreślenie) można uniknąć nową nazwę wartość, która nie ma potrzeby tworzenia.</span><span class="sxs-lookup"><span data-stu-id="cbb01-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="cbb01-117">Kopiowanie elementów z krotka odwołania do krotka struktury również jest prosty:</span><span class="sxs-lookup"><span data-stu-id="cbb01-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="cbb01-118">Funkcje `fst` i `snd` (odwoływać się tylko krotek) zwraca pierwsze i drugie elementy krotki, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="cbb01-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="cbb01-119">Nie jest nie wbudowanych funkcji zwracającą trzeciego elementu trzykrotnie, ale łatwo zapisu jedną w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="cbb01-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="cbb01-120">Ogólnie rzecz biorąc lepiej jest na potrzeby dopasowywania do wzorca dostęp do poszczególnych spójnej kolekcji elementów.</span><span class="sxs-lookup"><span data-stu-id="cbb01-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="cbb01-121">Przy użyciu spójnych kolekcji</span><span class="sxs-lookup"><span data-stu-id="cbb01-121">Using Tuples</span></span>
<span data-ttu-id="cbb01-122">Krotki zapewnić wygodny sposób wielu wartości zwracane przez funkcję, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cbb01-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="cbb01-123">W tym przykładzie przeprowadza dzielenie liczby całkowitej i zwraca zaokrąglony wynik operacji jako pierwszego elementu członkowskiego pary spójnej kolekcji, a reszta jako drugiego elementu członkowskiego pary.</span><span class="sxs-lookup"><span data-stu-id="cbb01-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="cbb01-124">Krotek również może służyć jako argumenty funkcji, gdy chce się uniknąć niejawne currying argumentów funkcji, które jest implikowana przez zwykłe składnię.</span><span class="sxs-lookup"><span data-stu-id="cbb01-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="cbb01-125">Zwykle składnia definiujący funkcję `let sum a b = a + b` umożliwia zdefiniowanie funkcja, która jest aplikacja częściowa pierwszego argumentu funkcji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="cbb01-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="cbb01-126">Przy użyciu spójnych kolekcji jako parametr wyłącza currying.</span><span class="sxs-lookup"><span data-stu-id="cbb01-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="cbb01-127">Aby uzyskać więcej informacji, zobacz "Częściowe aplikacji argumenty" w [funkcji](functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="cbb01-127">For more information, see "Partial Application of Arguments" in [Functions](functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="cbb01-128">Nazwy typów spójnej kolekcji</span><span class="sxs-lookup"><span data-stu-id="cbb01-128">Names of Tuple Types</span></span>
<span data-ttu-id="cbb01-129">Podczas pisania limit nazwę typu, który jest spójnej kolekcji, użyj `*` symbol do oddzielania elementów.</span><span class="sxs-lookup"><span data-stu-id="cbb01-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="cbb01-130">Dla krotka składająca się z `int`, `float`, a `string`, takich jak `(10, 10.0, "ten")`, typu powinny być zapisane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="cbb01-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="cbb01-131">Współdziałanie z krotek C#</span><span class="sxs-lookup"><span data-stu-id="cbb01-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="cbb01-132">C# 7.0 wprowadzono spójnych kolekcji dla języka.</span><span class="sxs-lookup"><span data-stu-id="cbb01-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="cbb01-133">Spójne kolekcje w języku C# są struktury i odpowiadające krotek struktury w języku F #.</span><span class="sxs-lookup"><span data-stu-id="cbb01-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="cbb01-134">Współdziałanie z C#, należy użyć krotek struktury.</span><span class="sxs-lookup"><span data-stu-id="cbb01-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="cbb01-135">Jest to łatwo zrobić.</span><span class="sxs-lookup"><span data-stu-id="cbb01-135">This is easy to do.</span></span>  <span data-ttu-id="cbb01-136">Załóżmy, że trzeba przekazać krotka do klasy C# i korzystać z jej wynik, który jest także spójnych kolekcji:</span><span class="sxs-lookup"><span data-stu-id="cbb01-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

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

<span data-ttu-id="cbb01-137">W F # kodu można przekazać krotka struktury jako parametr i korzystać z wynik w postaci spójnej kolekcji struktury.</span><span class="sxs-lookup"><span data-stu-id="cbb01-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="cbb01-138">Konwertowanie pomiędzy krotek odwołania i krotek — struktura</span><span class="sxs-lookup"><span data-stu-id="cbb01-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="cbb01-139">Ponieważ krotek odwołania i struktury krotek dwóch zupełnie różnych reprezentacji podstawowych, nie są one umożliwiają niejawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="cbb01-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="cbb01-140">Oznacza to nie będzie kompilacji kodu, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="cbb01-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="cbb01-141">Musi być wzorzec dopasowywania w jednej krotce i utworzyć drugi z elementów składowych.</span><span class="sxs-lookup"><span data-stu-id="cbb01-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="cbb01-142">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cbb01-142">For example:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="cbb01-143">Skompilowanej postaci krotek odwołania</span><span class="sxs-lookup"><span data-stu-id="cbb01-143">Compiled Form of Reference Tuples</span></span>
<span data-ttu-id="cbb01-144">W tej sekcji opisano formę krotek, gdy są one kompilowane.</span><span class="sxs-lookup"><span data-stu-id="cbb01-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="cbb01-145">Informacje w tym miejscu nie jest konieczne do odczytu, chyba że ma być przeznaczona dla programu .NET Framework 3.5 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="cbb01-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="cbb01-146">Spójne kolekcje są kompilowane w obiektach jednego z kilku typów ogólnych, wszystkie nazwane `System.Tuple`, które są przeciążone w liczbie argumentów lub liczba parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="cbb01-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="cbb01-147">Typy spójnej kolekcji są wyświetlane w tym formularzu podczas przeglądania w innym języku, takich jak C# lub Visual Basic lub korzystając z narzędzia, które nie są znane konstrukcji F #.</span><span class="sxs-lookup"><span data-stu-id="cbb01-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="cbb01-148">`Tuple` Typy zostały wprowadzone w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="cbb01-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="cbb01-149">Jeśli aplikacja jest przeznaczona dla starszej wersji programu .NET Framework, kompilator używa wersji [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) w wersji 2.0 biblioteki podstawowej F #.</span><span class="sxs-lookup"><span data-stu-id="cbb01-149">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="cbb01-150">Typy w tej bibliotece są używane tylko dla aplikacji przeznaczonych dla 2.0, 3.0 i 3.5 wersje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cbb01-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="cbb01-151">Przekazywanie dalej typu jest używany do zapewniania zgodności plików binarnych między składnikami programu .NET Framework 2.0 i .NET Framework 4 F #.</span><span class="sxs-lookup"><span data-stu-id="cbb01-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="cbb01-152">Skompilowanej postaci krotek — struktura</span><span class="sxs-lookup"><span data-stu-id="cbb01-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="cbb01-153">Struktura krotek (na przykład `struct (x, y)`), są różni się od krotek odwołania.</span><span class="sxs-lookup"><span data-stu-id="cbb01-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="cbb01-154">Są one kompilowane do <xref:System.ValueTuple> typu przeciążony przez argumentów lub liczba parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="cbb01-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="cbb01-155">Są równoważne [krotek 7.0 C#](../../csharp/tuples.md) i [krotek 2017 Visual Basic](../../visual-basic/programming-guide/language-features/data-types/tuples.md)oraz współpraca dwukierunkowo.</span><span class="sxs-lookup"><span data-stu-id="cbb01-155">They are equivalent to [C# 7.0 Tuples](../../csharp/tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="cbb01-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbb01-156">See Also</span></span>
[<span data-ttu-id="cbb01-157">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="cbb01-157">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="cbb01-158">Typy F#</span><span class="sxs-lookup"><span data-stu-id="cbb01-158">F# Types</span></span>](fsharp-types.md)
