---
title: "Komórki odwołań (F#)"
description: "Dowiedz się, jak F # odwołanie do komórki są lokalizacje magazynu, które umożliwiają tworzenie wartości modyfikowalne z semantykę odwołania."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 09a0b221-ea21-45c4-bae8-5e4a339750c4
ms.openlocfilehash: c7470c9a36cf2cd24dd89ceffcf6e90c6dc4d2dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="reference-cells"></a><span data-ttu-id="92ca6-104">Komórki odwołań</span><span class="sxs-lookup"><span data-stu-id="92ca6-104">Reference Cells</span></span>

<span data-ttu-id="92ca6-105">*Odwołanie do komórki* są lokalizacje magazynu, które umożliwiają tworzenie wartości modyfikowalne z semantykę odwołania.</span><span class="sxs-lookup"><span data-stu-id="92ca6-105">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="92ca6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="92ca6-106">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="92ca6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92ca6-107">Remarks</span></span>
<span data-ttu-id="92ca6-108">Możesz użyć `ref` operator przed wartością do utworzenia nowego hermetyzujący wartość komórki odwołania.</span><span class="sxs-lookup"><span data-stu-id="92ca6-108">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="92ca6-109">Podstawową wartość można będzie wtedy zmieniać, ponieważ jest ona modyfikowalna.</span><span class="sxs-lookup"><span data-stu-id="92ca6-109">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="92ca6-110">Komórka odwołania zawiera wartość rzeczywistą, a nie sam adres.</span><span class="sxs-lookup"><span data-stu-id="92ca6-110">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="92ca6-111">Po utworzeniu komórka odwołania przy użyciu `ref` operatora, Utwórz kopię odpowiednia wartość jako hermetyzowany modyfikowalne wartości.</span><span class="sxs-lookup"><span data-stu-id="92ca6-111">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="92ca6-112">Odwołanie do komórki można wyłuskać przy użyciu `!` — operator (eliminacja).</span><span class="sxs-lookup"><span data-stu-id="92ca6-112">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="92ca6-113">Poniższy przykład kodu ilustruje deklarowanie i używanie komórek odwołań.</span><span class="sxs-lookup"><span data-stu-id="92ca6-113">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="92ca6-114">Dane wyjściowe `50`.</span><span class="sxs-lookup"><span data-stu-id="92ca6-114">The output is `50`.</span></span>

<span data-ttu-id="92ca6-115">Komórki odwołań są wystąpieniami klasy `Ref` typu ogólnego rekordu, który został zadeklarowany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="92ca6-115">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="92ca6-116">Typ `'a ref` jest synonimem `Ref<'a>`.</span><span class="sxs-lookup"><span data-stu-id="92ca6-116">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="92ca6-117">Pierwszy zapis jest stosowany do wyświetlania tego typu w kompilatorze i technologii IntelliSense w środowisku IDE, jednak podstawowa definicja ma postać jak w drugim zapisie.</span><span class="sxs-lookup"><span data-stu-id="92ca6-117">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="92ca6-118">`ref` Operator tworzy nowe odwołanie do komórki.</span><span class="sxs-lookup"><span data-stu-id="92ca6-118">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="92ca6-119">Następujący kod jest deklaracja `ref` operatora.</span><span class="sxs-lookup"><span data-stu-id="92ca6-119">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="92ca6-120">W poniższej tabeli przedstawiono funkcje, które są dostępne w komórce odwołania.</span><span class="sxs-lookup"><span data-stu-id="92ca6-120">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="92ca6-121">Operator, element członkowski lub pole</span><span class="sxs-lookup"><span data-stu-id="92ca6-121">Operator, member, or field</span></span>|<span data-ttu-id="92ca6-122">Opis</span><span class="sxs-lookup"><span data-stu-id="92ca6-122">Description</span></span>|<span data-ttu-id="92ca6-123">Typ</span><span class="sxs-lookup"><span data-stu-id="92ca6-123">Type</span></span>|<span data-ttu-id="92ca6-124">Definicja</span><span class="sxs-lookup"><span data-stu-id="92ca6-124">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="92ca6-125">`!`(operatora anulowania odwołania do)</span><span class="sxs-lookup"><span data-stu-id="92ca6-125">`!` (dereference operator)</span></span>|<span data-ttu-id="92ca6-126">Zwraca podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="92ca6-126">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="92ca6-127">`:=`(operator przypisania)</span><span class="sxs-lookup"><span data-stu-id="92ca6-127">`:=` (assignment operator)</span></span>|<span data-ttu-id="92ca6-128">Zmienia podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="92ca6-128">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="92ca6-129">`ref`(operator)</span><span class="sxs-lookup"><span data-stu-id="92ca6-129">`ref` (operator)</span></span>|<span data-ttu-id="92ca6-130">Hermetyzuje wartość do nowej komórki odwołania.</span><span class="sxs-lookup"><span data-stu-id="92ca6-130">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="92ca6-131">`Value`(właściwości)</span><span class="sxs-lookup"><span data-stu-id="92ca6-131">`Value` (property)</span></span>|<span data-ttu-id="92ca6-132">Pobiera lub ustawia podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="92ca6-132">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="92ca6-133">`contents`(pola rekordu)</span><span class="sxs-lookup"><span data-stu-id="92ca6-133">`contents` (record field)</span></span>|<span data-ttu-id="92ca6-134">Pobiera lub ustawia podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="92ca6-134">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|
<span data-ttu-id="92ca6-135">Istnieje kilka sposobów dostępu do podstawowej wartości.</span><span class="sxs-lookup"><span data-stu-id="92ca6-135">There are several ways to access the underlying value.</span></span> <span data-ttu-id="92ca6-136">Wartość zwracana przez dereference operator (`!`) nie jest możliwa do przypisania wartości.</span><span class="sxs-lookup"><span data-stu-id="92ca6-136">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="92ca6-137">W związku z tym jeśli modyfikujesz odpowiednia wartość, należy użyć operatora przypisania (`:=`) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="92ca6-137">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="92ca6-138">Zarówno `Value` właściwości i `contents` pola są można przypisać wartości.</span><span class="sxs-lookup"><span data-stu-id="92ca6-138">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="92ca6-139">W związku z tym można za ich pomocą uzyskać dostęp do podstawowej wartości albo ją zmienić, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="92ca6-139">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="92ca6-140">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="92ca6-140">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="92ca6-141">Pole `contents` zapewnia zgodność z innymi wersjami programu ML i spowoduje wygenerowanie ostrzeżenia podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="92ca6-141">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="92ca6-142">Aby wyłączyć ostrzeżenia, należy użyć `--mlcompatibility` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="92ca6-142">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="92ca6-143">Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="92ca6-143">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="92ca6-144">Poniższy fragment kodu ilustruje używanie komórek odwołań w przekazywaniu parametrów.</span><span class="sxs-lookup"><span data-stu-id="92ca6-144">The following code illustrates the use of reference cells in parameter passing.</span></span> <span data-ttu-id="92ca6-145">Typ Incrementor ma metodę przyrostu, która przyjmuje parametr, który zawiera parametr typu byref.</span><span class="sxs-lookup"><span data-stu-id="92ca6-145">The Incrementor type has a method Increment that takes a parameter that includes byref in the parameter type.</span></span> <span data-ttu-id="92ca6-146">Byref w typ parametru wskazuje, że obiekty wywołujące musi upłynąć komórka odwołania lub adresu zmiennej typowe określonego typu w tej sprawy int. Pozostały kod przedstawia sposób wywołania przyrostu z obu typów argumentów i pokazano sposób użycia operatora ref w zmiennej, aby utworzyć komórka odwołania (ref myDelta1).</span><span class="sxs-lookup"><span data-stu-id="92ca6-146">The byref in the parameter type indicates that callers must pass a reference cell or the address of a typical variable of the specified type, in this case int. The remaining code illustrates how to call Increment with both of these types of arguments, and shows the use of the ref operator on a variable to create a reference cell (ref myDelta1).</span></span> <span data-ttu-id="92ca6-147">Następnie przedstawiono użycie address-of — operator (&amp;) do generowania odpowiednich argumentu.</span><span class="sxs-lookup"><span data-stu-id="92ca6-147">It then shows the use of the address-of operator (&amp;) to generate an appropriate argument.</span></span> <span data-ttu-id="92ca6-148">Na koniec Increment — metoda jest wywoływana ponownie przy użyciu komórka odwołania, które są zadeklarowane za pomocą powiązania let.</span><span class="sxs-lookup"><span data-stu-id="92ca6-148">Finally, the Increment method is called again by using a reference cell that is declared by using a let binding.</span></span> <span data-ttu-id="92ca6-149">Końcowe wiersz kodu przedstawiono użycie!</span><span class="sxs-lookup"><span data-stu-id="92ca6-149">The final line of code demonstrates the use of the !</span></span> <span data-ttu-id="92ca6-150">operatora, aby usunąć odwołania do komórka odwołania do drukowania.</span><span class="sxs-lookup"><span data-stu-id="92ca6-150">operator to dereference the reference cell for printing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

<span data-ttu-id="92ca6-151">Aby uzyskać więcej informacji na temat przekazywane przez odwołanie, zobacz [parametry i argumenty](parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="92ca6-151">For more information about how to pass by reference, see [Parameters and Arguments](parameters-and-arguments.md).</span></span>

>[!NOTE]
<span data-ttu-id="92ca6-152">C# programistów wiedzieć, że ten ref działa inaczej w języku F # niż w języku C#.</span><span class="sxs-lookup"><span data-stu-id="92ca6-152">C# programmers should know that ref works differently in F# than it does in C#.</span></span> <span data-ttu-id="92ca6-153">Na przykład użycie ref, jeśli argument nie ma ten sam efekt w języku F # jak w języku C#.</span><span class="sxs-lookup"><span data-stu-id="92ca6-153">For example, the use of ref when you pass an argument does not have the same effect in F# as it does in C#.</span></span>

## <a name="consuming-c-ref-returns"></a><span data-ttu-id="92ca6-154">C# — zużywanie `ref` zwraca</span><span class="sxs-lookup"><span data-stu-id="92ca6-154">Consuming C# `ref` returns</span></span>

<span data-ttu-id="92ca6-155">Począwszy od 4.1 F #, będzie można korzystać z `ref` zwraca wygenerowany w języku C#.</span><span class="sxs-lookup"><span data-stu-id="92ca6-155">Starting with F# 4.1, you can consume `ref` returns generated in C#.</span></span>  <span data-ttu-id="92ca6-156">Wynik wywołania takie jest `byref<_>` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="92ca6-156">The result of such a call is a `byref<_>` pointer.</span></span>

<span data-ttu-id="92ca6-157">Następujące C# metody:</span><span class="sxs-lookup"><span data-stu-id="92ca6-157">The following C# method:</span></span>

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

<span data-ttu-id="92ca6-158">Może być przezroczysty wywołany przez język F # z nie specjalnych składni:</span><span class="sxs-lookup"><span data-stu-id="92ca6-158">Can be transparently called by F# with no special syntax:</span></span>

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

<span data-ttu-id="92ca6-159">Można również zadeklarować funkcji, które można podjąć `ref` zwracać jako danych wejściowych, na przykład:</span><span class="sxs-lookup"><span data-stu-id="92ca6-159">You can also declare functions which could take a `ref` return as input, for example:</span></span>

```fsharp
let f (x: byref<int>) = &x
```

<span data-ttu-id="92ca6-160">Obecnie nie istnieje sposób do generowania `ref` zwracany w języku F #, który może być używana w języku C#.</span><span class="sxs-lookup"><span data-stu-id="92ca6-160">There is currently no way to generate a `ref` return in F# which could be consumed in C#.</span></span>

## <a name="see-also"></a><span data-ttu-id="92ca6-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92ca6-161">See Also</span></span>
[<span data-ttu-id="92ca6-162">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="92ca6-162">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="92ca6-163">Parametry i argumenty</span><span class="sxs-lookup"><span data-stu-id="92ca6-163">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="92ca6-164">Operator odwołanie do symbolu i</span><span class="sxs-lookup"><span data-stu-id="92ca6-164">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)
