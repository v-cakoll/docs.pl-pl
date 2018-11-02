---
title: Właściwości indeksowane (F#)
description: Więcej informacji na temat właściwości indeksowanych w F#, które umożliwiają dostęp tablicy do danych uporządkowanych.
ms.date: 10/17/2018
ms.openlocfilehash: 3dac60eba3d9e7a9c3e76ad7ee051e6b30b88636
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "49452251"
---
# <a name="indexed-properties"></a><span data-ttu-id="c69a0-103">Właściwości indeksowane</span><span class="sxs-lookup"><span data-stu-id="c69a0-103">Indexed Properties</span></span>

<span data-ttu-id="c69a0-104">Podczas definiowania klasy, która przenosi danych uporządkowanych, czasami może być przydatne do udostępnienia indeksowane dane bez narażania podstawowej implementacji.</span><span class="sxs-lookup"><span data-stu-id="c69a0-104">When defining a class that abstracts over ordered data, it can sometimes be helpful to provide indexed access to that data without exposing the underlying implementation.</span></span> <span data-ttu-id="c69a0-105">Jest to zrobić za pomocą `Index` elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="c69a0-105">This is done with the `Index` member.</span></span>

## <a name="syntax"></a><span data-ttu-id="c69a0-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c69a0-106">Syntax</span></span>

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.Index
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property with get only
member self-identifier.Index
    with get(index-values) =
        get-member-body

// Indexed property that has set only.
member self-identifier.Index
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a><span data-ttu-id="c69a0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c69a0-107">Remarks</span></span>

<span data-ttu-id="c69a0-108">Formy składnia poprzednich pokazują, jak zdefiniować właściwości indeksowanych mających zarówno `get` i `set` metody mają `get` tylko metody lub `set` tylko metody.</span><span class="sxs-lookup"><span data-stu-id="c69a0-108">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="c69a0-109">Można także połączyć oba te składni przedstawionej tylko polecenie get i składni przedstawionej tylko zestaw i generuje właściwości, która ma zarówno get i set.</span><span class="sxs-lookup"><span data-stu-id="c69a0-109">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="c69a0-110">Ten formularz, ostatnie pozwala umieścić modyfikatory dostępności różnych i atrybuty w get i ustawianie metody.</span><span class="sxs-lookup"><span data-stu-id="c69a0-110">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="c69a0-111">Przy użyciu nazwy `Item`, kompilator traktuje właściwości jako domyślnie indeksowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="c69a0-111">By using the name `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="c69a0-112">A *Właściwość indeksowana domyślnie* jest właściwością, która może uzyskać dostęp za pomocą składni tablicy na wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="c69a0-112">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="c69a0-113">Na przykład jeśli `o` jest obiektem typu, który definiuje tę właściwość, składnia `o.[index]` umożliwia dostęp do właściwości.</span><span class="sxs-lookup"><span data-stu-id="c69a0-113">For example, if `o` is an object of the type that defines this property, the syntax `o.[index]` is used to access the property.</span></span>

<span data-ttu-id="c69a0-114">Składnia służąca do uzyskiwania dostępu do właściwości indeksowanych innych niż domyślne jest do podania nazwy właściwości i indeksu w nawiasach, podobnie jak regularny członek.</span><span class="sxs-lookup"><span data-stu-id="c69a0-114">The syntax for accessing a non-default indexed property is to provide the name of the property and the index in parentheses, just like a regular member.</span></span> <span data-ttu-id="c69a0-115">Na przykład jeśli właściwość `o` nosi nazwę `Ordinal`, piszesz `o.Ordinal(index)` do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="c69a0-115">For example, if the property on `o` is called `Ordinal`, you write `o.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="c69a0-116">Niezależnie od tego formularza, którego używasz należy zawsze używać rozwinięte formularza metody set dla właściwości indeksowanych.</span><span class="sxs-lookup"><span data-stu-id="c69a0-116">Regardless of which form you use, you should always use the curried form for the set method on an indexed property.</span></span> <span data-ttu-id="c69a0-117">Aby uzyskać informacje na temat funkcji rozwinięte zobacz [funkcji](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="c69a0-117">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="c69a0-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="c69a0-118">Example</span></span>

<span data-ttu-id="c69a0-119">Poniższy przykład kodu ilustruje definicja oraz wykorzystanie domyślnej i właściwości indeksowanych innych niż domyślne, które get i ustawianie metody.</span><span class="sxs-lookup"><span data-stu-id="c69a0-119">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="c69a0-120">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="c69a0-120">Output</span></span>

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a><span data-ttu-id="c69a0-121">Właściwości indeksowane, za pomocą wielu zmiennych indeksu</span><span class="sxs-lookup"><span data-stu-id="c69a0-121">Indexed Properties with Multiple Index Variables</span></span>

<span data-ttu-id="c69a0-122">Właściwości indeksowane może mieć więcej niż jedną zmienną indeksu.</span><span class="sxs-lookup"><span data-stu-id="c69a0-122">Indexed properties can have more than one index variable.</span></span> <span data-ttu-id="c69a0-123">W takim przypadku zmienne są oddzielone przecinkami, gdy jest używana.</span><span class="sxs-lookup"><span data-stu-id="c69a0-123">In that case, the variables are separated by commas when the property is used.</span></span> <span data-ttu-id="c69a0-124">Metody set w takiej właściwości musi mieć dwa argumenty rozwinięte, pierwszy z nich jest krotkę zawierającą klucze, a drugi z nich jest wartość.</span><span class="sxs-lookup"><span data-stu-id="c69a0-124">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value being set.</span></span>

<span data-ttu-id="c69a0-125">Poniższy przykład demonstruje użycie Właściwość indeksowana z wielu zmiennych indeksu.</span><span class="sxs-lookup"><span data-stu-id="c69a0-125">The following code demonstrates the use of an indexed property with multiple index variables.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]

## <a name="see-also"></a><span data-ttu-id="c69a0-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c69a0-126">See also</span></span>

- [<span data-ttu-id="c69a0-127">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c69a0-127">Members</span></span>](index.md)
