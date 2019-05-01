---
title: Komórki odwołań
description: Dowiedz się, jak F# komórki odwołań są lokalizacje przechowywania, które umożliwiają tworzenie modyfikowalnych wartości z semantyką odwołań.
ms.date: 05/16/2016
ms.openlocfilehash: e4fcd3cf1abcf5f5e3b4d5439c9215b79ff8dbcd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795407"
---
# <a name="reference-cells"></a><span data-ttu-id="2a142-103">Komórki odwołań</span><span class="sxs-lookup"><span data-stu-id="2a142-103">Reference Cells</span></span>

<span data-ttu-id="2a142-104">*Komórki odwołań* to lokalizacje przechowywania, które umożliwiają tworzenie modyfikowalnych wartości z semantyką odwołań.</span><span class="sxs-lookup"><span data-stu-id="2a142-104">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="2a142-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a142-105">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="2a142-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a142-106">Remarks</span></span>

<span data-ttu-id="2a142-107">Możesz użyć `ref` przed wartością operatora do utworzenia nowej komórki odwołania, która hermetyzuje wartość.</span><span class="sxs-lookup"><span data-stu-id="2a142-107">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="2a142-108">Podstawową wartość można będzie wtedy zmieniać, ponieważ jest ona modyfikowalna.</span><span class="sxs-lookup"><span data-stu-id="2a142-108">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="2a142-109">Komórka odwołania zawiera wartość rzeczywistą, a nie sam adres.</span><span class="sxs-lookup"><span data-stu-id="2a142-109">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="2a142-110">Podczas tworzenia komórek odwołań za pomocą `ref` operatora, Utwórz kopię podstawowej wartości jako hermetyzowana wartość modyfikowalna.</span><span class="sxs-lookup"><span data-stu-id="2a142-110">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="2a142-111">Komórkę odwołania można wyłuskać za pomocą `!` — operator (wykrzyknika).</span><span class="sxs-lookup"><span data-stu-id="2a142-111">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="2a142-112">Poniższy przykład kodu ilustruje deklarowanie i używanie komórek odwołań.</span><span class="sxs-lookup"><span data-stu-id="2a142-112">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="2a142-113">Dane wyjściowe są `50`.</span><span class="sxs-lookup"><span data-stu-id="2a142-113">The output is `50`.</span></span>

<span data-ttu-id="2a142-114">Komórki odwołań są wystąpieniami `Ref` ogólnego typu rekordu, który jest zadeklarowany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="2a142-114">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="2a142-115">Typ `'a ref` jest synonimem dla `Ref<'a>`.</span><span class="sxs-lookup"><span data-stu-id="2a142-115">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="2a142-116">Pierwszy zapis jest stosowany do wyświetlania tego typu w kompilatorze i technologii IntelliSense w środowisku IDE, jednak podstawowa definicja ma postać jak w drugim zapisie.</span><span class="sxs-lookup"><span data-stu-id="2a142-116">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="2a142-117">`ref` Operatora powoduje utworzenie nowej komórki odwołania.</span><span class="sxs-lookup"><span data-stu-id="2a142-117">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="2a142-118">Poniższy kod stanowi deklarację `ref` operatora.</span><span class="sxs-lookup"><span data-stu-id="2a142-118">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="2a142-119">W poniższej tabeli przedstawiono funkcje, które są dostępne w komórce odwołania.</span><span class="sxs-lookup"><span data-stu-id="2a142-119">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="2a142-120">Operator, element członkowski lub pole</span><span class="sxs-lookup"><span data-stu-id="2a142-120">Operator, member, or field</span></span>|<span data-ttu-id="2a142-121">Opis</span><span class="sxs-lookup"><span data-stu-id="2a142-121">Description</span></span>|<span data-ttu-id="2a142-122">Typ</span><span class="sxs-lookup"><span data-stu-id="2a142-122">Type</span></span>|<span data-ttu-id="2a142-123">Definicja</span><span class="sxs-lookup"><span data-stu-id="2a142-123">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="2a142-124">`!` (operator dereferencji)</span><span class="sxs-lookup"><span data-stu-id="2a142-124">`!` (dereference operator)</span></span>|<span data-ttu-id="2a142-125">Zwraca podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="2a142-125">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="2a142-126">`:=` (operator przypisania)</span><span class="sxs-lookup"><span data-stu-id="2a142-126">`:=` (assignment operator)</span></span>|<span data-ttu-id="2a142-127">Zmienia podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="2a142-127">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="2a142-128">`ref` (operator)</span><span class="sxs-lookup"><span data-stu-id="2a142-128">`ref` (operator)</span></span>|<span data-ttu-id="2a142-129">Hermetyzuje wartość do nowej komórki odwołania.</span><span class="sxs-lookup"><span data-stu-id="2a142-129">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="2a142-130">`Value` (właściwość)</span><span class="sxs-lookup"><span data-stu-id="2a142-130">`Value` (property)</span></span>|<span data-ttu-id="2a142-131">Pobiera lub ustawia podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="2a142-131">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="2a142-132">`contents` (pole rekordu)</span><span class="sxs-lookup"><span data-stu-id="2a142-132">`contents` (record field)</span></span>|<span data-ttu-id="2a142-133">Pobiera lub ustawia podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="2a142-133">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|

<span data-ttu-id="2a142-134">Istnieje kilka sposobów dostępu do podstawowej wartości.</span><span class="sxs-lookup"><span data-stu-id="2a142-134">There are several ways to access the underlying value.</span></span> <span data-ttu-id="2a142-135">Wartość zwracana przez operator wyłuskania (`!`) nie jest przypisywalna.</span><span class="sxs-lookup"><span data-stu-id="2a142-135">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="2a142-136">W związku z tym, jeśli w przypadku modyfikowania podstawowej wartości należy użyć operatora przypisania (`:=`) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="2a142-136">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="2a142-137">Zarówno `Value` właściwości i `contents` są przypisywalne.</span><span class="sxs-lookup"><span data-stu-id="2a142-137">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="2a142-138">W związku z tym można za ich pomocą uzyskać dostęp do podstawowej wartości albo ją zmienić, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2a142-138">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="2a142-139">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="2a142-139">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="2a142-140">Pole `contents` zapewnia zgodność z innymi wersjami języka ML i spowoduje wygenerowanie ostrzeżenia podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2a142-140">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="2a142-141">Aby wyłączyć to ostrzeżenie, użyj `--mlcompatibility` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="2a142-141">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="2a142-142">Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="2a142-142">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="2a142-143">C#Programiści powinni wiedzieć, że `ref` w C# nie jest tak samo jak `ref` w F#.</span><span class="sxs-lookup"><span data-stu-id="2a142-143">C# programmers should know that `ref` in C# is not the same thing as `ref` in F#.</span></span> <span data-ttu-id="2a142-144">Odpowiednik konstrukcje w F# są [zkratka](byrefs.md), które są różne koncepcji z komórki odwołań.</span><span class="sxs-lookup"><span data-stu-id="2a142-144">The equivalent constructs in F# are [byrefs](byrefs.md), which are a different concept from reference cells.</span></span>

<span data-ttu-id="2a142-145">Wartości oznaczone jako `mutable`może zostać automatycznie podwyższony do `'a ref` przechwycone przez zamknięcie; zobacz [wartości](values/index.md).</span><span class="sxs-lookup"><span data-stu-id="2a142-145">Values marked as `mutable`may be automatically promoted to `'a ref` if captured by a closure; see [Values](values/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2a142-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a142-146">See also</span></span>

- [<span data-ttu-id="2a142-147">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="2a142-147">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="2a142-148">Parametry i argumenty</span><span class="sxs-lookup"><span data-stu-id="2a142-148">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="2a142-149">Odwołanie do symboli i operatorów</span><span class="sxs-lookup"><span data-stu-id="2a142-149">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)
- [<span data-ttu-id="2a142-150">Wartości</span><span class="sxs-lookup"><span data-stu-id="2a142-150">Values</span></span>](values/index.md)
