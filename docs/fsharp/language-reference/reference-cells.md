---
title: Komórki odwołań
description: Dowiedz F# się, w jaki sposób komórki referencyjne są lokalizacjami przechowywania, które umożliwiają tworzenie modyfikowalnych wartości przy użyciu semantyki odwołania.
ms.date: 05/16/2016
ms.openlocfilehash: 2bca7797b272c0e7d5bf54df07041dc08e33709a
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216769"
---
# <a name="reference-cells"></a><span data-ttu-id="9a02c-103">Komórki odwołań</span><span class="sxs-lookup"><span data-stu-id="9a02c-103">Reference Cells</span></span>

<span data-ttu-id="9a02c-104">*Komórki odwołań* to lokalizacje przechowywania, które umożliwiają tworzenie modyfikowalnych wartości z semantyką odwołania.</span><span class="sxs-lookup"><span data-stu-id="9a02c-104">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="9a02c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a02c-105">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="9a02c-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a02c-106">Remarks</span></span>

<span data-ttu-id="9a02c-107">Użyj `ref` operatora przed wartością, aby utworzyć nową komórkę odwołania, która hermetyzuje wartość.</span><span class="sxs-lookup"><span data-stu-id="9a02c-107">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="9a02c-108">Podstawową wartość można będzie wtedy zmieniać, ponieważ jest ona modyfikowalna.</span><span class="sxs-lookup"><span data-stu-id="9a02c-108">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="9a02c-109">Komórka odwołania zawiera wartość rzeczywistą, a nie sam adres.</span><span class="sxs-lookup"><span data-stu-id="9a02c-109">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="9a02c-110">Podczas tworzenia komórki odniesienia przy użyciu `ref` operatora należy utworzyć kopię bazowej wartości jako hermetyzowaną wartość modyfikowalną.</span><span class="sxs-lookup"><span data-stu-id="9a02c-110">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="9a02c-111">Można usunąć odwołanie do komórki odwołania przy użyciu `!` operatora (wykrzyknika).</span><span class="sxs-lookup"><span data-stu-id="9a02c-111">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="9a02c-112">Poniższy przykład kodu ilustruje deklarowanie i używanie komórek odwołań.</span><span class="sxs-lookup"><span data-stu-id="9a02c-112">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="9a02c-113">Dane wyjściowe to `50`.</span><span class="sxs-lookup"><span data-stu-id="9a02c-113">The output is `50`.</span></span>

<span data-ttu-id="9a02c-114">Komórki odwołań są wystąpieniami `Ref` typu rekordu ogólnego, który jest zadeklarowany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="9a02c-114">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="9a02c-115">Typ `'a ref` jest synonimem dla `Ref<'a>`.</span><span class="sxs-lookup"><span data-stu-id="9a02c-115">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="9a02c-116">Pierwszy zapis jest stosowany do wyświetlania tego typu w kompilatorze i technologii IntelliSense w środowisku IDE, jednak podstawowa definicja ma postać jak w drugim zapisie.</span><span class="sxs-lookup"><span data-stu-id="9a02c-116">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="9a02c-117">`ref` Operator tworzy nową komórkę odwołania.</span><span class="sxs-lookup"><span data-stu-id="9a02c-117">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="9a02c-118">Poniższy kod jest deklaracją `ref` operatora.</span><span class="sxs-lookup"><span data-stu-id="9a02c-118">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="9a02c-119">W poniższej tabeli przedstawiono funkcje, które są dostępne w komórce odwołania.</span><span class="sxs-lookup"><span data-stu-id="9a02c-119">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="9a02c-120">Operator, element członkowski lub pole</span><span class="sxs-lookup"><span data-stu-id="9a02c-120">Operator, member, or field</span></span>|<span data-ttu-id="9a02c-121">Opis</span><span class="sxs-lookup"><span data-stu-id="9a02c-121">Description</span></span>|<span data-ttu-id="9a02c-122">Typ</span><span class="sxs-lookup"><span data-stu-id="9a02c-122">Type</span></span>|<span data-ttu-id="9a02c-123">Definicja</span><span class="sxs-lookup"><span data-stu-id="9a02c-123">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="9a02c-124">`!`(operator dereferencji)</span><span class="sxs-lookup"><span data-stu-id="9a02c-124">`!` (dereference operator)</span></span>|<span data-ttu-id="9a02c-125">Zwraca podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="9a02c-125">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="9a02c-126">`:=`(operator przypisania)</span><span class="sxs-lookup"><span data-stu-id="9a02c-126">`:=` (assignment operator)</span></span>|<span data-ttu-id="9a02c-127">Zmienia podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="9a02c-127">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="9a02c-128">`ref`zakład</span><span class="sxs-lookup"><span data-stu-id="9a02c-128">`ref` (operator)</span></span>|<span data-ttu-id="9a02c-129">Hermetyzuje wartość do nowej komórki odwołania.</span><span class="sxs-lookup"><span data-stu-id="9a02c-129">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="9a02c-130">`Value`wartość</span><span class="sxs-lookup"><span data-stu-id="9a02c-130">`Value` (property)</span></span>|<span data-ttu-id="9a02c-131">Pobiera lub ustawia podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="9a02c-131">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="9a02c-132">`contents`(pole rekordu)</span><span class="sxs-lookup"><span data-stu-id="9a02c-132">`contents` (record field)</span></span>|<span data-ttu-id="9a02c-133">Pobiera lub ustawia podstawową wartość.</span><span class="sxs-lookup"><span data-stu-id="9a02c-133">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|

<span data-ttu-id="9a02c-134">Istnieje kilka sposobów dostępu do podstawowej wartości.</span><span class="sxs-lookup"><span data-stu-id="9a02c-134">There are several ways to access the underlying value.</span></span> <span data-ttu-id="9a02c-135">Wartość zwrócona przez operator dereferencji (`!`) nie jest wartością, którą można przypisać.</span><span class="sxs-lookup"><span data-stu-id="9a02c-135">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="9a02c-136">W związku z tym, jeśli modyfikujesz wartość podstawową, należy zamiast tego użyć operatora przypisania`:=`().</span><span class="sxs-lookup"><span data-stu-id="9a02c-136">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="9a02c-137">`Value` Obie właściwości`contents` i pola są wartościami możliwymi do przypisania.</span><span class="sxs-lookup"><span data-stu-id="9a02c-137">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="9a02c-138">W związku z tym można za ich pomocą uzyskać dostęp do podstawowej wartości albo ją zmienić, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9a02c-138">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="9a02c-139">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="9a02c-139">The output is as follows.</span></span>

```console
10
10
11
12
```

<span data-ttu-id="9a02c-140">Pole `contents` jest zapewniane pod kątem zgodności z innymi wersjami ml i podczas kompilacji generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="9a02c-140">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="9a02c-141">Aby wyłączyć ostrzeżenie, użyj `--mlcompatibility` opcji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="9a02c-141">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="9a02c-142">Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="9a02c-142">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="9a02c-143">C#Programiści powinni wiedzieć, `ref` że C# w programie nie są takie same `ref` jak F#w.</span><span class="sxs-lookup"><span data-stu-id="9a02c-143">C# programmers should know that `ref` in C# is not the same thing as `ref` in F#.</span></span> <span data-ttu-id="9a02c-144">Równoważne konstrukcje w F# to [ByRef](byrefs.md), które są różnymi koncepcjami z komórek odwołań.</span><span class="sxs-lookup"><span data-stu-id="9a02c-144">The equivalent constructs in F# are [byrefs](byrefs.md), which are a different concept from reference cells.</span></span>

<span data-ttu-id="9a02c-145">Wartości oznaczone jako `mutable`mogą zostać automatycznie podwyższone `'a ref` do, jeśli zostały przechwycone przez zamknięcie; zobacz [wartości](./values/index.md).</span><span class="sxs-lookup"><span data-stu-id="9a02c-145">Values marked as `mutable`may be automatically promoted to `'a ref` if captured by a closure; see [Values](./values/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9a02c-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a02c-146">See also</span></span>

- [<span data-ttu-id="9a02c-147">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="9a02c-147">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="9a02c-148">Parametry i argumenty</span><span class="sxs-lookup"><span data-stu-id="9a02c-148">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="9a02c-149">Odwołanie do symboli i operatorów</span><span class="sxs-lookup"><span data-stu-id="9a02c-149">Symbol and Operator Reference</span></span>](./symbol-and-operator-reference/index.md)
- [<span data-ttu-id="9a02c-150">Wartości</span><span class="sxs-lookup"><span data-stu-id="9a02c-150">Values</span></span>](./values/index.md)
