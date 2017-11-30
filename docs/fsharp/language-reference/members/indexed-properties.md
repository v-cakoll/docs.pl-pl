---
title: "Właściwości indeksowane (F#)"
description: "Więcej informacji na temat F # indeksowane właściwości, które są właściwości, które zapewniają dostęp tablicy do danych uporządkowanych."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f1266b8b-e2e3-4f49-9332-65c6d34dc0f3
ms.openlocfilehash: 78a09a70621e82f073346471e68ec826359641d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="indexed-properties"></a><span data-ttu-id="3e6ac-104">Właściwości indeksowane</span><span class="sxs-lookup"><span data-stu-id="3e6ac-104">Indexed Properties</span></span>

<span data-ttu-id="3e6ac-105">*Właściwości indeksowanych* są uporządkowane właściwości, które zapewniają dostęp tablicy do danych.</span><span class="sxs-lookup"><span data-stu-id="3e6ac-105">*Indexed properties* are properties that provide array-like access to ordered data.</span></span>


## <a name="syntax"></a><span data-ttu-id="3e6ac-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e6ac-106">Syntax</span></span>

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.PropertyName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.PropertyName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.PropertyName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.PropertyName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a><span data-ttu-id="3e6ac-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e6ac-107">Remarks</span></span>
<span data-ttu-id="3e6ac-108">Trzech rodzajów poprzedniej składni pokazują, jak zdefiniować właściwości indeksowanych, które mają zarówno `get` i `set` metody, ma `get` tylko metody lub ma `set` tylko metody.</span><span class="sxs-lookup"><span data-stu-id="3e6ac-108">The three forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="3e6ac-109">Można także połączyć oba składni pokazano tylko polecenie get i składni pokazano tylko zestawu i tworzy właściwość, która ma zarówno get i set.</span><span class="sxs-lookup"><span data-stu-id="3e6ac-109">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="3e6ac-110">Ten ostatni formularz umożliwia zawiesić modyfikatory dostępności różnych i atrybuty get i ustaw metody.</span><span class="sxs-lookup"><span data-stu-id="3e6ac-110">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="3e6ac-111">Gdy *PropertyName* jest `Item`, kompilator traktuje właściwość jako domyślnie indeksowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="3e6ac-111">When the *PropertyName* is `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="3e6ac-112">A *Właściwość indeksowana domyślnie* jest właściwością, której będziesz mieć dostęp za pomocą składni tablicy w wystąpieniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="3e6ac-112">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="3e6ac-113">Na przykład jeśli `obj` jest obiektem typu, który definiuje tę właściwość, składnia `obj.[index]` służy do dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="3e6ac-113">For example, if `obj` is an object of the type that defines this property, the syntax `obj.[index]` is used to access the property.</span></span>

<span data-ttu-id="3e6ac-114">Składnia do uzyskiwania dostępu do właściwości indeksowanych niestandardowy jest zapewnienie nazwy właściwości oraz indeksu w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="3e6ac-114">The syntax for accessing a nondefault indexed property is to provide the name of the property and the index in parentheses.</span></span> <span data-ttu-id="3e6ac-115">Na przykład, jeśli właściwość jest `Ordinal`, możesz zapisać `obj.Ordinal(index)` do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="3e6ac-115">For example, if the property is `Ordinal`, you write `obj.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="3e6ac-116">Niezależnie od tego formularza, którego używasz, zawsze należy używać rozwinięte forma `set` metody dla właściwości indeksowanej.</span><span class="sxs-lookup"><span data-stu-id="3e6ac-116">Regardless of which form you use, you should always use the curried form for the `set` method on an indexed property.</span></span> <span data-ttu-id="3e6ac-117">Aby uzyskać informacje o funkcje rozwinięte, zobacz [funkcji](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="3e6ac-117">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="3e6ac-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e6ac-118">Example</span></span>

<span data-ttu-id="3e6ac-119">Poniższy przykładowy kod przedstawia definicja oraz wykorzystanie domyślnych i właściwości indeksowanych innych niż domyślne, które i ustaw metody get.</span><span class="sxs-lookup"><span data-stu-id="3e6ac-119">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="3e6ac-120">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="3e6ac-120">Output</span></span>

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a><span data-ttu-id="3e6ac-121">Właściwości indeksowane wiele zmiennych indeksu</span><span class="sxs-lookup"><span data-stu-id="3e6ac-121">Indexed Properties with Multiple Index Variables</span></span>
<span data-ttu-id="3e6ac-122">Właściwości indeksowane może mieć więcej niż jedną zmienną indeksu.</span><span class="sxs-lookup"><span data-stu-id="3e6ac-122">Indexed properties can have more than one index variable.</span></span> <span data-ttu-id="3e6ac-123">W takim przypadku zmienne są oddzielone przecinkami, gdy jest używana.</span><span class="sxs-lookup"><span data-stu-id="3e6ac-123">In that case, the variables are separated by commas when the property is used.</span></span> <span data-ttu-id="3e6ac-124">W takich właściwości metody zestaw musi mieć dwa argumenty curried, z których pierwszy jest spójnych kolekcji zawierający klucze, a drugi z nich jest wartość.</span><span class="sxs-lookup"><span data-stu-id="3e6ac-124">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value being set.</span></span>

<span data-ttu-id="3e6ac-125">Poniższy kod przedstawia użycie właściwości indeksowanych wiele zmiennych indeksu.</span><span class="sxs-lookup"><span data-stu-id="3e6ac-125">The following code demonstrates the use of an indexed property with multiple index variables.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="3e6ac-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e6ac-126">See Also</span></span>
[<span data-ttu-id="3e6ac-127">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3e6ac-127">Members</span></span>](index.md)
