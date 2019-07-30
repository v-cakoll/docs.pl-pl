---
title: Krotki
description: Dowiedz się F# więcej na temat krotki, grupowania nienazwanych, ale uporządkowanych wartości, prawdopodobnie różnych typów.
ms.date: 05/16/2016
ms.openlocfilehash: 7a15d7e0c6c9b42118dd75066f02cbb2e05335fc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630241"
---
# <a name="tuples"></a><span data-ttu-id="dc7d8-103">Krotki</span><span class="sxs-lookup"><span data-stu-id="dc7d8-103">Tuples</span></span>

<span data-ttu-id="dc7d8-104">*Krotka* to grupa nienazwanych, ale uporządkowanych wartości, prawdopodobnie różnych typów.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="dc7d8-105">Krotki mogą być typami referencyjnymi lub strukturami.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="dc7d8-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc7d8-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a><span data-ttu-id="dc7d8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc7d8-107">Remarks</span></span>

<span data-ttu-id="dc7d8-108">Każdy *element* w poprzedniej składni może być dowolnym prawidłowym F# wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="dc7d8-109">Przykłady</span><span class="sxs-lookup"><span data-stu-id="dc7d8-109">Examples</span></span>

<span data-ttu-id="dc7d8-110">Przykłady krotek obejmują pary, potrójne i tak dalej, o tych samych lub różnych typach.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="dc7d8-111">Przykłady przedstawiono w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a><span data-ttu-id="dc7d8-112">Uzyskiwanie pojedynczych wartości</span><span class="sxs-lookup"><span data-stu-id="dc7d8-112">Obtaining Individual Values</span></span>

<span data-ttu-id="dc7d8-113">Możesz użyć dopasowania wzorca, aby uzyskać dostęp i przypisać nazwy dla elementów krotki, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="dc7d8-114">Możesz również odtworzyć krotkę przez dopasowanie wzorca poza `match` wyrażeniem za pośrednictwem `let` powiązania:</span><span class="sxs-lookup"><span data-stu-id="dc7d8-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="dc7d8-115">Lub można dopasować do wzorca spójnych krotek jako dane wejściowe do funkcji:</span><span class="sxs-lookup"><span data-stu-id="dc7d8-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="dc7d8-116">Jeśli potrzebujesz tylko jednego elementu krotki, symbol wieloznaczny (podkreślenie) można użyć, aby uniknąć tworzenia nowej nazwy dla niepotrzebnej wartości.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="dc7d8-117">Kopiowanie elementów z krotki referencyjnej do krotki struktury jest również proste:</span><span class="sxs-lookup"><span data-stu-id="dc7d8-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="dc7d8-118">Funkcje `fst` i`snd` (tylko krotki referencyjne) zwracają odpowiednio pierwszy i drugi element spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="dc7d8-119">Nie istnieje Wbudowana funkcja, która zwraca trzeci element trzykrotności, ale można ją łatwo napisać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="dc7d8-120">Ogólnie rzecz biorąc lepiej jest używać dopasowywania wzorców w celu uzyskania dostępu do poszczególnych elementów krotki.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="dc7d8-121">Używanie krotek</span><span class="sxs-lookup"><span data-stu-id="dc7d8-121">Using Tuples</span></span>

<span data-ttu-id="dc7d8-122">Krotki zapewniają wygodny sposób zwracania wielu wartości z funkcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="dc7d8-123">Ten przykład wykonuje dzielenie liczby całkowitej i zwraca zaokrąglony wynik operacji jako pierwszy element członkowski pary krotek i resztę jako drugi element członkowski pary.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="dc7d8-124">Krotki mogą być również używane jako argumenty funkcji, gdy chcesz uniknąć niejawnego currying argumentów funkcji, które są implikowane przez normalną składnię funkcji.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="dc7d8-125">Zwykła Składnia służąca do definiowania funkcji `let sum a b = a + b` umożliwia zdefiniowanie funkcji, która jest częściową aplikacją pierwszego argumentu funkcji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="dc7d8-126">Użycie krotki jako parametru powoduje wyłączenie currying.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="dc7d8-127">Aby uzyskać więcej informacji, zobacz "częściowe stosowanie argumentów" w [funkcjach](./functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="dc7d8-127">For more information, see "Partial Application of Arguments" in [Functions](./functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="dc7d8-128">Nazwy typów krotek</span><span class="sxs-lookup"><span data-stu-id="dc7d8-128">Names of Tuple Types</span></span>

<span data-ttu-id="dc7d8-129">Podczas wpisywania nazwy typu, który jest krotką, należy użyć `*` symbolu do oddzielenia elementów.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="dc7d8-130">Dla krotki, która składa się `int`z `float`, a, i `string`a, takich `(10, 10.0, "ten")`jak, typ zostałby zapisany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="dc7d8-131">Współdziałanie C# z krotkami</span><span class="sxs-lookup"><span data-stu-id="dc7d8-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="dc7d8-132">C#7,0 wprowadza krotki do języka.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="dc7d8-133">Krotki w C# są strukturami i są odpowiednikami krotek struktury w F#.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="dc7d8-134">Jeśli musisz współpracować z programem C#, musisz użyć krotek struktury.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="dc7d8-135">Jest to bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-135">This is easy to do.</span></span>  <span data-ttu-id="dc7d8-136">Załóżmy na przykład, że musisz przekazać krotkę do C# klasy, a następnie użyć jej wyniku, która jest również krotką:</span><span class="sxs-lookup"><span data-stu-id="dc7d8-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

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

<span data-ttu-id="dc7d8-137">W F# kodzie można następnie przekazać krotkę struktury jako parametr i użyć wyniku jako krotki struktury.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="dc7d8-138">Konwertowanie między Krotekmi referencyjnymi a krotkami struktury</span><span class="sxs-lookup"><span data-stu-id="dc7d8-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="dc7d8-139">Ponieważ krotki referencyjne i krotek struktury mają zupełnie inną reprezentację podstawową, nie są one niejawnie konwertowane.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="dc7d8-140">Oznacza to, że kod, taki jak następujące, nie zostanie skompilowany:</span><span class="sxs-lookup"><span data-stu-id="dc7d8-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="dc7d8-141">Musisz dopasować wzorzec dla jednej krotki i utworzyć drugą z częściami elementów.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="dc7d8-142">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="dc7d8-142">For example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="dc7d8-143">Skompilowana forma kolekcji referencyjnych</span><span class="sxs-lookup"><span data-stu-id="dc7d8-143">Compiled Form of Reference Tuples</span></span>

<span data-ttu-id="dc7d8-144">W tej sekcji opisano formę krotek, gdy są one kompilowane.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="dc7d8-145">Informacje w tym miejscu nie są niezbędne do odczytania, chyba że jest przeznaczony .NET Framework 3,5 lub niższy.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="dc7d8-146">Krotki są kompilowane do obiektów jednego z kilku typów ogólnych, wszystkie nazwane `System.Tuple`, które są przeciążone dla liczby argumentów lub liczby parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="dc7d8-147">Typy krotek są wyświetlane w tym formularzu podczas wyświetlania ich z innego języka, takiego jak C# lub Visual Basic, lub podczas korzystania z narzędzia, które nie ma informacji o F# konstrukcjach.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="dc7d8-148">`Tuple` Typy zostały wprowadzone w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="dc7d8-149">Jeśli obiektem docelowym jest wcześniejsza wersja .NET Framework, kompilator używa wersji elementu [System. krotka](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) z wersji 2,0 biblioteki F# podstawowej.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-149">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="dc7d8-150">Typy w tej bibliotece są używane tylko dla aplikacji przeznaczonych dla wersji 2,0, 3,0 i 3,5 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="dc7d8-151">Przekazywanie typu jest używane w celu zapewnienia zgodności binarnej między składnikami .NET Framework F# 2,0 i .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="dc7d8-152">Skompilowana forma krotek struktury</span><span class="sxs-lookup"><span data-stu-id="dc7d8-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="dc7d8-153">Krotki struktury (na przykład `struct (x, y)`) różnią się zasadniczo od krotek odwołania.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="dc7d8-154">Są one kompilowane w <xref:System.ValueTuple> typie, przeciążonym przez liczbę argumentów lub liczbie parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="dc7d8-155">Są one równoważne z [ C# 7,0 krotkami](../../csharp/tuples.md) i [Visual Basic 2017 krotek](../../visual-basic/programming-guide/language-features/data-types/tuples.md)i współdziałają dwukierunkowo.</span><span class="sxs-lookup"><span data-stu-id="dc7d8-155">They are equivalent to [C# 7.0 Tuples](../../csharp/tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc7d8-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc7d8-156">See also</span></span>

- [<span data-ttu-id="dc7d8-157">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="dc7d8-157">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="dc7d8-158">Typy F#</span><span class="sxs-lookup"><span data-stu-id="dc7d8-158">F# Types</span></span>](fsharp-types.md)
