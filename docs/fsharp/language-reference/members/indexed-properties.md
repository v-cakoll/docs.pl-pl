---
title: Właściwości indeksowane
description: Dowiedz się więcej na F#temat właściwości indeksowanych w programie, które umożliwiają dostęp do danych uporządkowanych w postaci zbliżonej do tablic.
ms.date: 10/17/2018
ms.openlocfilehash: 379417e31b8e178d8c939e5b23dc144bfb17e562
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627555"
---
# <a name="indexed-properties"></a><span data-ttu-id="37970-103">Właściwości indeksowane</span><span class="sxs-lookup"><span data-stu-id="37970-103">Indexed Properties</span></span>

<span data-ttu-id="37970-104">Podczas definiowania klasy, która jest abstrakcyjna względem uporządkowanych danych, może być czasem przydatna do zapewnienia indeksowanego dostępu do tych danych bez uwidaczniania podstawowej implementacji.</span><span class="sxs-lookup"><span data-stu-id="37970-104">When defining a class that abstracts over ordered data, it can sometimes be helpful to provide indexed access to that data without exposing the underlying implementation.</span></span> <span data-ttu-id="37970-105">Odbywa się to za pomocą `Item` elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="37970-105">This is done with the `Item` member.</span></span>

## <a name="syntax"></a><span data-ttu-id="37970-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="37970-106">Syntax</span></span>

```fsharp
// Indexed property that can be read and written to
member self-identifier.Item
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property can only be read
member self-identifier.Item
    with get(index-values) =
        get-member-body

// Indexed property that can only be set
member self-identifier.Item
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a><span data-ttu-id="37970-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37970-107">Remarks</span></span>

<span data-ttu-id="37970-108">Formy poprzedniej składni pokazują, jak definiować indeksowane właściwości `get` , które mają zarówno metodę, jak `set` i, mają `get` tylko metodę, lub `set` tylko metodę.</span><span class="sxs-lookup"><span data-stu-id="37970-108">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="37970-109">Można również połączyć składnię pokazaną tylko do pobrania i składnię wyświetlaną tylko dla zestawu i utworzyć właściwość, która ma oba metody get i Set.</span><span class="sxs-lookup"><span data-stu-id="37970-109">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="37970-110">Ten ostatni formularz umożliwia umieszczenie różnych modyfikatorów dostępności i atrybutów w metodach get i Set.</span><span class="sxs-lookup"><span data-stu-id="37970-110">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="37970-111">Używając nazwy `Item`, kompilator traktuje właściwość jako domyślną właściwość indeksowaną.</span><span class="sxs-lookup"><span data-stu-id="37970-111">By using the name `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="37970-112">*Domyślną indeksowaną właściwością* jest właściwość, do której można uzyskać dostęp za pomocą składni podobnej do tablic w wystąpieniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="37970-112">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="37970-113">Na przykład jeśli `o` jest obiektem typu, który definiuje tę właściwość, składnia `o.[index]` jest używana w celu uzyskania dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="37970-113">For example, if `o` is an object of the type that defines this property, the syntax `o.[index]` is used to access the property.</span></span>

<span data-ttu-id="37970-114">Składnia służąca do uzyskiwania dostępu do właściwości indeksowanej innej niż domyślna to podanie nazwy właściwości i indeksu w nawiasach, podobnie jak zwykłego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="37970-114">The syntax for accessing a non-default indexed property is to provide the name of the property and the index in parentheses, just like a regular member.</span></span> <span data-ttu-id="37970-115">Na przykład, jeśli właściwość `o` jest wywoływana `Ordinal`, nastąpi zapis `o.Ordinal(index)` w celu uzyskania do niej dostępu.</span><span class="sxs-lookup"><span data-stu-id="37970-115">For example, if the property on `o` is called `Ordinal`, you write `o.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="37970-116">Niezależnie od tego, który formularz jest używany, należy zawsze używać formularza rozwinięte dla metody Set dla właściwości indeksowanej.</span><span class="sxs-lookup"><span data-stu-id="37970-116">Regardless of which form you use, you should always use the curried form for the set method on an indexed property.</span></span> <span data-ttu-id="37970-117">Aby uzyskać informacje o funkcjach rozwinięte [](../functions/index.md), zobacz Functions.</span><span class="sxs-lookup"><span data-stu-id="37970-117">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="37970-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="37970-118">Example</span></span>

<span data-ttu-id="37970-119">Poniższy przykład kodu ilustruje definicję i użycie domyślnych i niedomyślnych właściwości indeksowanych, które mają metody get i Set.</span><span class="sxs-lookup"><span data-stu-id="37970-119">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="37970-120">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="37970-120">Output</span></span>

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a><span data-ttu-id="37970-121">Właściwości indeksowane z wieloma wartościami indeksu</span><span class="sxs-lookup"><span data-stu-id="37970-121">Indexed Properties with multiple index values</span></span>

<span data-ttu-id="37970-122">Indeksowane właściwości mogą mieć więcej niż jedną wartość indeksu.</span><span class="sxs-lookup"><span data-stu-id="37970-122">Indexed properties can have more than one index value.</span></span> <span data-ttu-id="37970-123">W takim przypadku wartości są oddzielane przecinkami, gdy właściwość jest używana.</span><span class="sxs-lookup"><span data-stu-id="37970-123">In that case, the values are separated by commas when the property is used.</span></span> <span data-ttu-id="37970-124">Metoda Set w takiej właściwości musi mieć dwa argumenty rozwinięte, z których pierwszy jest krotką zawierającą klucze, a druga wartość do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="37970-124">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value to set.</span></span>

<span data-ttu-id="37970-125">Poniższy kod ilustruje użycie właściwości indeksowanej z wieloma wartościami indeksu.</span><span class="sxs-lookup"><span data-stu-id="37970-125">The following code demonstrates the use of an indexed property with multiple index values.</span></span>

```fsharp
open System.Collections.Generic

/// Basic implementation of a sparse matrix based on a dictionary
type SparseMatrix() =
    let table = new Dictionary<(int * int), float>()
    member __.Item
        // Because the key is comprised of two values, 'get' has two index values
        with get(key1, key2) = table.[(key1, key2)]

        // 'set' has two index values and a new value to place in the key's position
        and set (key1, key2) value = table.[(key1, key2)] <- value

let sm = new SparseMatrix()
for i in 1..1000 do
    sm.[i, i] <- float i * float i
```

## <a name="see-also"></a><span data-ttu-id="37970-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37970-126">See also</span></span>

- [<span data-ttu-id="37970-127">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="37970-127">Members</span></span>](index.md)
