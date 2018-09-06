---
title: Komórki odwołań (F#)
description: 'Dowiedz się, jak komórki odwołań F # są lokalizacje przechowywania, które umożliwiają tworzenie modyfikowalnych wartości z semantyką odwołań.'
ms.date: 05/16/2016
ms.openlocfilehash: 133aec6b162a13306a05c9afa172f859890565eb
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892427"
---
# <a name="reference-cells"></a><span data-ttu-id="b2da3-103">Komórki odwołań</span><span class="sxs-lookup"><span data-stu-id="b2da3-103">Reference Cells</span></span>

<span data-ttu-id="b2da3-104">*Komórki odwołań* to lokalizacje przechowywania, które umożliwiają tworzenie modyfikowalnych wartości z semantyką odwołań.</span><span class="sxs-lookup"><span data-stu-id="b2da3-104">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2da3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2da3-105">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="b2da3-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2da3-106">Remarks</span></span>

<span data-ttu-id="b2da3-107">Możesz użyć `ref` przed wartością operatora do utworzenia nowej komórki odwołania, która hermetyzuje wartość.</span><span class="sxs-lookup"><span data-stu-id="b2da3-107">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="b2da3-108">Podstawową wartość można będzie wtedy zmieniać, ponieważ jest ona modyfikowalna.</span><span class="sxs-lookup"><span data-stu-id="b2da3-108">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="b2da3-109">Komórka odwołania zawiera wartość rzeczywistą, a nie sam adres.</span><span class="sxs-lookup"><span data-stu-id="b2da3-109">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="b2da3-110">Podczas tworzenia komórek odwołań za pomocą `ref` operatora, Utwórz kopię podstawowej wartości jako hermetyzowana wartość modyfikowalna.</span><span class="sxs-lookup"><span data-stu-id="b2da3-110">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="b2da3-111">Komórkę odwołania można wyłuskać za pomocą `!` — operator (wykrzyknika).</span><span class="sxs-lookup"><span data-stu-id="b2da3-111">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="b2da3-112">Poniższy przykład kodu ilustruje deklarowanie i używanie komórek odwołań.</span><span class="sxs-lookup"><span data-stu-id="b2da3-112">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="b2da3-113">Dane wyjściowe są `50`.</span><span class="sxs-lookup"><span data-stu-id="b2da3-113">The output is `50`.</span></span>

<span data-ttu-id="b2da3-114">Komórki odwołań są wystąpieniami `Ref` ogólnego typu rekordu, który jest zadeklarowany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="b2da3-114">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="b2da3-115">Typ `'a ref` jest synonimem dla `Ref<'a>`.</span><span class="sxs-lookup"><span data-stu-id="b2da3-115">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="b2da3-116">Pierwszy zapis jest stosowany do wyświetlania tego typu w kompilatorze i technologii IntelliSense w środowisku IDE, jednak podstawowa definicja ma postać jak w drugim zapisie.</span><span class="sxs-lookup"><span data-stu-id="b2da3-116">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="b2da3-117">`ref` Operatora powoduje utworzenie nowej komórki odwołania.</span><span class="sxs-lookup"><span data-stu-id="b2da3-117">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="b2da3-118">Poniższy kod stanowi deklarację `ref` operatora.</span><span class="sxs-lookup"><span data-stu-id="b2da3-118">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="b2da3-119">W poniższej tabeli przedstawiono funkcje, które są dostępne w komórce odwołania.</span><span class="sxs-lookup"><span data-stu-id="b2da3-119">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="b2da3-120">Operator, element członkowski lub pole</span><span class="sxs-lookup"><span data-stu-id="b2da3-120">Operator, member, or field</span></span>|<span data-ttu-id="b2da3-121">Opis</span><span class="sxs-lookup"><span data-stu-id="b2da3-121">Description</span></span>|<span data-ttu-id="b2da3-122">Typ</span><span class="sxs-lookup"><span data-stu-id="b2da3-122">Type</span></span>|<span data-ttu-id="b2da3-123">Definicja</span><span class="sxs-lookup"><span data-stu-id="b2da3-123">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="b2da3-124">`!` (operator dereferencji)</span><span class="sxs-lookup"><span data-stu-id="b2da3-124">`!` (dereference operator)</span></span>|<span data-ttu-id="b2da3-125">Zwraca podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="b2da3-125">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="b2da3-126">`:=` (operator przypisania)</span><span class="sxs-lookup"><span data-stu-id="b2da3-126">`:=` (assignment operator)</span></span>|<span data-ttu-id="b2da3-127">Zmienia podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="b2da3-127">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="b2da3-128">`ref` (operator)</span><span class="sxs-lookup"><span data-stu-id="b2da3-128">`ref` (operator)</span></span>|<span data-ttu-id="b2da3-129">Hermetyzuje wartość do nowej komórki odwołania.</span><span class="sxs-lookup"><span data-stu-id="b2da3-129">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="b2da3-130">`Value` (właściwość)</span><span class="sxs-lookup"><span data-stu-id="b2da3-130">`Value` (property)</span></span>|<span data-ttu-id="b2da3-131">Pobiera lub ustawia podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="b2da3-131">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="b2da3-132">`contents` (pole rekordu)</span><span class="sxs-lookup"><span data-stu-id="b2da3-132">`contents` (record field)</span></span>|<span data-ttu-id="b2da3-133">Pobiera lub ustawia podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="b2da3-133">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|
<span data-ttu-id="b2da3-134">Istnieje kilka sposobów dostępu do podstawowej wartości.</span><span class="sxs-lookup"><span data-stu-id="b2da3-134">There are several ways to access the underlying value.</span></span> <span data-ttu-id="b2da3-135">Wartość zwracana przez operator wyłuskania (`!`) nie jest przypisywalna.</span><span class="sxs-lookup"><span data-stu-id="b2da3-135">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="b2da3-136">W związku z tym, jeśli w przypadku modyfikowania podstawowej wartości należy użyć operatora przypisania (`:=`) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="b2da3-136">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="b2da3-137">Zarówno `Value` właściwości i `contents` są przypisywalne.</span><span class="sxs-lookup"><span data-stu-id="b2da3-137">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="b2da3-138">W związku z tym można za ich pomocą uzyskać dostęp do podstawowej wartości albo ją zmienić, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b2da3-138">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="b2da3-139">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="b2da3-139">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="b2da3-140">Pole `contents` zapewnia zgodność z innymi wersjami języka ML i spowoduje wygenerowanie ostrzeżenia podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b2da3-140">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="b2da3-141">Aby wyłączyć to ostrzeżenie, użyj `--mlcompatibility` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="b2da3-141">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="b2da3-142">Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="b2da3-142">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="b2da3-143">Poniższy fragment kodu ilustruje używanie komórek odwołań w przekazywaniu parametrów.</span><span class="sxs-lookup"><span data-stu-id="b2da3-143">The following code illustrates the use of reference cells in parameter passing.</span></span> <span data-ttu-id="b2da3-144">Typ Incrementor ma metodę inkrementacji, który przyjmuje parametr, który zawiera typ parametru byref.</span><span class="sxs-lookup"><span data-stu-id="b2da3-144">The Incrementor type has a method Increment that takes a parameter that includes byref in the parameter type.</span></span> <span data-ttu-id="b2da3-145">Byref w typie parametru wskazuje, że obiekty wywołujące muszą przekazywać komórkę odwołania lub adres typowej zmiennej o określonym typie, w tym przypadków int. Pozostały kod ilustruje sposób wywołania metody przyrostu z oboma tymi typami argumentów i pokazuje użycie operatora ref w zmiennej, aby utworzyć komórki odwołania (ref myDelta1).</span><span class="sxs-lookup"><span data-stu-id="b2da3-145">The byref in the parameter type indicates that callers must pass a reference cell or the address of a typical variable of the specified type, in this case int. The remaining code illustrates how to call Increment with both of these types of arguments, and shows the use of the ref operator on a variable to create a reference cell (ref myDelta1).</span></span> <span data-ttu-id="b2da3-146">Następnie prezentuje użycie operatora address-of (&amp;) do wygenerowania odpowiedniego argumentu.</span><span class="sxs-lookup"><span data-stu-id="b2da3-146">It then shows the use of the address-of operator (&amp;) to generate an appropriate argument.</span></span> <span data-ttu-id="b2da3-147">Na koniec przyrost jest ponownie wywoływana metoda przy użyciu komórki odwołania, która jest zadeklarowana za pomocą powiązania let.</span><span class="sxs-lookup"><span data-stu-id="b2da3-147">Finally, the Increment method is called again by using a reference cell that is declared by using a let binding.</span></span> <span data-ttu-id="b2da3-148">Ostatni wiersz kodu ilustruje użycie!</span><span class="sxs-lookup"><span data-stu-id="b2da3-148">The final line of code demonstrates the use of the !</span></span> <span data-ttu-id="b2da3-149">operator, który ma być wyłuskania komórki odwołania na potrzeby drukowania.</span><span class="sxs-lookup"><span data-stu-id="b2da3-149">operator to dereference the reference cell for printing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

<span data-ttu-id="b2da3-150">Aby uzyskać więcej informacji na temat przekazywania odwołania, zobacz [parametrami i argumentami](parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="b2da3-150">For more information about how to pass by reference, see [Parameters and Arguments](parameters-and-arguments.md).</span></span>

>[!NOTE]
<span data-ttu-id="b2da3-151">Programiści języka C# wiedzieć, że ten ref działa inaczej w języku F # niż w języku C#.</span><span class="sxs-lookup"><span data-stu-id="b2da3-151">C# programmers should know that ref works differently in F# than it does in C#.</span></span> <span data-ttu-id="b2da3-152">Na przykład użycie ref podczas przekazywania argumentu ma ten sam efekt w języku F # jak w języku C#.</span><span class="sxs-lookup"><span data-stu-id="b2da3-152">For example, the use of ref when you pass an argument does not have the same effect in F# as it does in C#.</span></span>

>[!NOTE]
<span data-ttu-id="b2da3-153">`mutable` Zmienne mogą zostać automatycznie podwyższony do `'a ref` przechwycone przez zamknięcie; zobacz [wartości](values/index.md).</span><span class="sxs-lookup"><span data-stu-id="b2da3-153">`mutable` variables may be automatically promoted to `'a ref` if captured by a closure; see [Values](values/index.md).</span></span>

## <a name="consuming-c-ref-returns"></a><span data-ttu-id="b2da3-154">C# — zużywanie `ref` zwraca</span><span class="sxs-lookup"><span data-stu-id="b2da3-154">Consuming C# `ref` returns</span></span>

<span data-ttu-id="b2da3-155">Począwszy od F # 4.1, mogą wykorzystywać `ref` zwraca generowane w języku C#.</span><span class="sxs-lookup"><span data-stu-id="b2da3-155">Starting with F# 4.1, you can consume `ref` returns generated in C#.</span></span>  <span data-ttu-id="b2da3-156">Wynik takich wywołań to `byref<_>` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="b2da3-156">The result of such a call is a `byref<_>` pointer.</span></span>

<span data-ttu-id="b2da3-157">Następujące metodę języka C#:</span><span class="sxs-lookup"><span data-stu-id="b2da3-157">The following C# method:</span></span>

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

<span data-ttu-id="b2da3-158">Może być przezroczysty wywołany przez język F # z nie specjalnej składni:</span><span class="sxs-lookup"><span data-stu-id="b2da3-158">Can be transparently called by F# with no special syntax:</span></span>

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

<span data-ttu-id="b2da3-159">Można również zadeklarować funkcji, może to potrwać `ref` Zwróć jako danych wejściowych, na przykład:</span><span class="sxs-lookup"><span data-stu-id="b2da3-159">You can also declare functions which could take a `ref` return as input, for example:</span></span>

```fsharp
let f (x: byref<int>) = &x
```

<span data-ttu-id="b2da3-160">Obecnie nie istnieje sposób do generowania `ref` zwracany w języku F #, która może być używane w języku C#.</span><span class="sxs-lookup"><span data-stu-id="b2da3-160">There is currently no way to generate a `ref` return in F# which could be consumed in C#.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2da3-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2da3-161">See also</span></span>

- [<span data-ttu-id="b2da3-162">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="b2da3-162">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="b2da3-163">Parametry i argumenty</span><span class="sxs-lookup"><span data-stu-id="b2da3-163">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="b2da3-164">Odwołanie do symboli i operatorów</span><span class="sxs-lookup"><span data-stu-id="b2da3-164">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)
- [<span data-ttu-id="b2da3-165">Wartości</span><span class="sxs-lookup"><span data-stu-id="b2da3-165">Values</span></span>](values/index.md)
