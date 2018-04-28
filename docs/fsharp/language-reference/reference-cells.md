---
title: Komórki odwołań (F#)
description: 'Dowiedz się, jak F # odwołanie do komórki są lokalizacje magazynu, które umożliwiają tworzenie wartości modyfikowalne z semantykę odwołania.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: e017adb2a031dff996892e2bb6585fc95f644ff9
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="reference-cells"></a><span data-ttu-id="c07c4-103">Komórki odwołań</span><span class="sxs-lookup"><span data-stu-id="c07c4-103">Reference Cells</span></span>

<span data-ttu-id="c07c4-104">*Odwołanie do komórki* są lokalizacje magazynu, które umożliwiają tworzenie wartości modyfikowalne z semantykę odwołania.</span><span class="sxs-lookup"><span data-stu-id="c07c4-104">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="c07c4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c07c4-105">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="c07c4-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c07c4-106">Remarks</span></span>
<span data-ttu-id="c07c4-107">Możesz użyć `ref` operator przed wartością do utworzenia nowego hermetyzujący wartość komórki odwołania.</span><span class="sxs-lookup"><span data-stu-id="c07c4-107">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="c07c4-108">Podstawową wartość można będzie wtedy zmieniać, ponieważ jest ona modyfikowalna.</span><span class="sxs-lookup"><span data-stu-id="c07c4-108">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="c07c4-109">Komórka odwołania zawiera wartość rzeczywistą, a nie sam adres.</span><span class="sxs-lookup"><span data-stu-id="c07c4-109">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="c07c4-110">Po utworzeniu komórka odwołania przy użyciu `ref` operatora, Utwórz kopię odpowiednia wartość jako hermetyzowany modyfikowalne wartości.</span><span class="sxs-lookup"><span data-stu-id="c07c4-110">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="c07c4-111">Odwołanie do komórki można wyłuskać przy użyciu `!` — operator (eliminacja).</span><span class="sxs-lookup"><span data-stu-id="c07c4-111">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="c07c4-112">Poniższy przykład kodu ilustruje deklarowanie i używanie komórek odwołań.</span><span class="sxs-lookup"><span data-stu-id="c07c4-112">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="c07c4-113">Dane wyjściowe `50`.</span><span class="sxs-lookup"><span data-stu-id="c07c4-113">The output is `50`.</span></span>

<span data-ttu-id="c07c4-114">Komórki odwołań są wystąpieniami klasy `Ref` typu ogólnego rekordu, który został zadeklarowany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="c07c4-114">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="c07c4-115">Typ `'a ref` jest synonimem `Ref<'a>`.</span><span class="sxs-lookup"><span data-stu-id="c07c4-115">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="c07c4-116">Pierwszy zapis jest stosowany do wyświetlania tego typu w kompilatorze i technologii IntelliSense w środowisku IDE, jednak podstawowa definicja ma postać jak w drugim zapisie.</span><span class="sxs-lookup"><span data-stu-id="c07c4-116">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="c07c4-117">`ref` Operator tworzy nowe odwołanie do komórki.</span><span class="sxs-lookup"><span data-stu-id="c07c4-117">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="c07c4-118">Następujący kod jest deklaracja `ref` operatora.</span><span class="sxs-lookup"><span data-stu-id="c07c4-118">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="c07c4-119">W poniższej tabeli przedstawiono funkcje, które są dostępne w komórce odwołania.</span><span class="sxs-lookup"><span data-stu-id="c07c4-119">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="c07c4-120">Operator, element członkowski lub pole</span><span class="sxs-lookup"><span data-stu-id="c07c4-120">Operator, member, or field</span></span>|<span data-ttu-id="c07c4-121">Opis</span><span class="sxs-lookup"><span data-stu-id="c07c4-121">Description</span></span>|<span data-ttu-id="c07c4-122">Typ</span><span class="sxs-lookup"><span data-stu-id="c07c4-122">Type</span></span>|<span data-ttu-id="c07c4-123">Definicja</span><span class="sxs-lookup"><span data-stu-id="c07c4-123">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="c07c4-124">`!` (operatora anulowania odwołania do)</span><span class="sxs-lookup"><span data-stu-id="c07c4-124">`!` (dereference operator)</span></span>|<span data-ttu-id="c07c4-125">Zwraca podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="c07c4-125">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="c07c4-126">`:=` (operator przypisania)</span><span class="sxs-lookup"><span data-stu-id="c07c4-126">`:=` (assignment operator)</span></span>|<span data-ttu-id="c07c4-127">Zmienia podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="c07c4-127">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="c07c4-128">`ref` (operator)</span><span class="sxs-lookup"><span data-stu-id="c07c4-128">`ref` (operator)</span></span>|<span data-ttu-id="c07c4-129">Hermetyzuje wartość do nowej komórki odwołania.</span><span class="sxs-lookup"><span data-stu-id="c07c4-129">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="c07c4-130">`Value` (właściwości)</span><span class="sxs-lookup"><span data-stu-id="c07c4-130">`Value` (property)</span></span>|<span data-ttu-id="c07c4-131">Pobiera lub ustawia podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="c07c4-131">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="c07c4-132">`contents` (pola rekordu)</span><span class="sxs-lookup"><span data-stu-id="c07c4-132">`contents` (record field)</span></span>|<span data-ttu-id="c07c4-133">Pobiera lub ustawia podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="c07c4-133">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|
<span data-ttu-id="c07c4-134">Istnieje kilka sposobów dostępu do podstawowej wartości.</span><span class="sxs-lookup"><span data-stu-id="c07c4-134">There are several ways to access the underlying value.</span></span> <span data-ttu-id="c07c4-135">Wartość zwracana przez dereference operator (`!`) nie jest możliwa do przypisania wartości.</span><span class="sxs-lookup"><span data-stu-id="c07c4-135">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="c07c4-136">W związku z tym jeśli modyfikujesz odpowiednia wartość, należy użyć operatora przypisania (`:=`) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="c07c4-136">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="c07c4-137">Zarówno `Value` właściwości i `contents` pola są można przypisać wartości.</span><span class="sxs-lookup"><span data-stu-id="c07c4-137">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="c07c4-138">W związku z tym można za ich pomocą uzyskać dostęp do podstawowej wartości albo ją zmienić, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c07c4-138">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="c07c4-139">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="c07c4-139">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="c07c4-140">Pole `contents` zapewnia zgodność z innymi wersjami programu ML i spowoduje wygenerowanie ostrzeżenia podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c07c4-140">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="c07c4-141">Aby wyłączyć ostrzeżenia, należy użyć `--mlcompatibility` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c07c4-141">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="c07c4-142">Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="c07c4-142">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="c07c4-143">Poniższy fragment kodu ilustruje używanie komórek odwołań w przekazywaniu parametrów.</span><span class="sxs-lookup"><span data-stu-id="c07c4-143">The following code illustrates the use of reference cells in parameter passing.</span></span> <span data-ttu-id="c07c4-144">Typ Incrementor ma metodę przyrostu, która przyjmuje parametr, który zawiera parametr typu byref.</span><span class="sxs-lookup"><span data-stu-id="c07c4-144">The Incrementor type has a method Increment that takes a parameter that includes byref in the parameter type.</span></span> <span data-ttu-id="c07c4-145">Byref w typ parametru wskazuje, że obiekty wywołujące musi upłynąć komórka odwołania lub adresu zmiennej typowe określonego typu w tej sprawy int. Pozostały kod przedstawia sposób wywołania przyrostu z obu typów argumentów i pokazano sposób użycia operatora ref w zmiennej, aby utworzyć komórka odwołania (ref myDelta1).</span><span class="sxs-lookup"><span data-stu-id="c07c4-145">The byref in the parameter type indicates that callers must pass a reference cell or the address of a typical variable of the specified type, in this case int. The remaining code illustrates how to call Increment with both of these types of arguments, and shows the use of the ref operator on a variable to create a reference cell (ref myDelta1).</span></span> <span data-ttu-id="c07c4-146">Następnie przedstawiono użycie address-of — operator (&amp;) do generowania odpowiednich argumentu.</span><span class="sxs-lookup"><span data-stu-id="c07c4-146">It then shows the use of the address-of operator (&amp;) to generate an appropriate argument.</span></span> <span data-ttu-id="c07c4-147">Na koniec Increment — metoda jest wywoływana ponownie przy użyciu komórka odwołania, które są zadeklarowane za pomocą powiązania let.</span><span class="sxs-lookup"><span data-stu-id="c07c4-147">Finally, the Increment method is called again by using a reference cell that is declared by using a let binding.</span></span> <span data-ttu-id="c07c4-148">Końcowe wiersz kodu przedstawiono użycie!</span><span class="sxs-lookup"><span data-stu-id="c07c4-148">The final line of code demonstrates the use of the !</span></span> <span data-ttu-id="c07c4-149">operatora, aby usunąć odwołania do komórka odwołania do drukowania.</span><span class="sxs-lookup"><span data-stu-id="c07c4-149">operator to dereference the reference cell for printing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

<span data-ttu-id="c07c4-150">Aby uzyskać więcej informacji na temat przekazywane przez odwołanie, zobacz [parametry i argumenty](parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="c07c4-150">For more information about how to pass by reference, see [Parameters and Arguments](parameters-and-arguments.md).</span></span>

>[!NOTE]
<span data-ttu-id="c07c4-151">C# programistów wiedzieć, że ten ref działa inaczej w języku F # niż w języku C#.</span><span class="sxs-lookup"><span data-stu-id="c07c4-151">C# programmers should know that ref works differently in F# than it does in C#.</span></span> <span data-ttu-id="c07c4-152">Na przykład użycie ref, jeśli argument nie ma ten sam efekt w języku F # jak w języku C#.</span><span class="sxs-lookup"><span data-stu-id="c07c4-152">For example, the use of ref when you pass an argument does not have the same effect in F# as it does in C#.</span></span>

## <a name="consuming-c-ref-returns"></a><span data-ttu-id="c07c4-153">C# — zużywanie `ref` zwraca</span><span class="sxs-lookup"><span data-stu-id="c07c4-153">Consuming C# `ref` returns</span></span>

<span data-ttu-id="c07c4-154">Począwszy od 4.1 F #, będzie można korzystać z `ref` zwraca wygenerowany w języku C#.</span><span class="sxs-lookup"><span data-stu-id="c07c4-154">Starting with F# 4.1, you can consume `ref` returns generated in C#.</span></span>  <span data-ttu-id="c07c4-155">Wynik wywołania takie jest `byref<_>` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="c07c4-155">The result of such a call is a `byref<_>` pointer.</span></span>

<span data-ttu-id="c07c4-156">Następujące C# metody:</span><span class="sxs-lookup"><span data-stu-id="c07c4-156">The following C# method:</span></span>

```csharp
namespace RefReturns
{
    public static class RefClass
    {
        public static ref int Find(int val, int[] vals)
        {
            for (int i = 0; i < vals.Length; i++)
            {
                if (vals[i] == val)
                {
                    return ref numbers[i]; // Returns the location, not the value
                }
            }

            throw new IndexOutOfRangeException($"{nameof(number)} not found");
        }
    }
}
```

<span data-ttu-id="c07c4-157">Może być przezroczysty wywołany przez język F # z nie specjalnych składni:</span><span class="sxs-lookup"><span data-stu-id="c07c4-157">Can be transparently called by F# with no special syntax:</span></span>

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

<span data-ttu-id="c07c4-158">Można również zadeklarować funkcji, które można podjąć `ref` zwracać jako danych wejściowych, na przykład:</span><span class="sxs-lookup"><span data-stu-id="c07c4-158">You can also declare functions which could take a `ref` return as input, for example:</span></span>

```fsharp
let f (x: byref<int>) = &x
```

<span data-ttu-id="c07c4-159">Obecnie nie istnieje sposób do generowania `ref` zwracany w języku F #, który może być używana w języku C#.</span><span class="sxs-lookup"><span data-stu-id="c07c4-159">There is currently no way to generate a `ref` return in F# which could be consumed in C#.</span></span>

## <a name="see-also"></a><span data-ttu-id="c07c4-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c07c4-160">See Also</span></span>
[<span data-ttu-id="c07c4-161">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="c07c4-161">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="c07c4-162">Parametry i argumenty</span><span class="sxs-lookup"><span data-stu-id="c07c4-162">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="c07c4-163">Odwołanie do symboli i operatorów</span><span class="sxs-lookup"><span data-stu-id="c07c4-163">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)
