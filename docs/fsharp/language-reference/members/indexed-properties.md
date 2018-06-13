---
title: Właściwości indeksowane (F#)
description: 'Więcej informacji na temat F # indeksowane właściwości, które są właściwości, które zapewniają dostęp tablicy do danych uporządkowanych.'
ms.date: 05/16/2016
ms.openlocfilehash: 503cef9693cfe5e13d4e2d19a721d65bff1ce749
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235944"
---
# <a name="indexed-properties"></a><span data-ttu-id="ff902-103">Właściwości indeksowane</span><span class="sxs-lookup"><span data-stu-id="ff902-103">Indexed Properties</span></span>

<span data-ttu-id="ff902-104">*Właściwości indeksowanych* są uporządkowane właściwości, które zapewniają dostęp tablicy do danych.</span><span class="sxs-lookup"><span data-stu-id="ff902-104">*Indexed properties* are properties that provide array-like access to ordered data.</span></span> <span data-ttu-id="ff902-105">Pochodzą w trzech formularzach:</span><span class="sxs-lookup"><span data-stu-id="ff902-105">They come in three forms:</span></span>

* `Item`
* `Ordinal`
* `Cardinal`

<span data-ttu-id="ff902-106">Element członkowski F # musi mieć nazwę jednej z tych trzech nazw zapewnienie dostępu do tablicy.</span><span class="sxs-lookup"><span data-stu-id="ff902-106">An F# member must be named one of these three names to provide array-like access.</span></span> <span data-ttu-id="ff902-107">`IndexerName` jest używana do reprezentowania żadnego z trzech poniższych opcji:</span><span class="sxs-lookup"><span data-stu-id="ff902-107">`IndexerName` is used to represent any of the three options below:</span></span>


## <a name="syntax"></a><span data-ttu-id="ff902-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff902-108">Syntax</span></span>

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.IndexerName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.IndexerName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.IndexerName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.IndexerName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a><span data-ttu-id="ff902-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff902-109">Remarks</span></span>
<span data-ttu-id="ff902-110">Formularze poprzedniej składni pokazują, jak zdefiniować właściwości indeksowanych, które mają zarówno `get` i `set` metody, ma `get` metody tylko, lub ma `set` tylko metody.</span><span class="sxs-lookup"><span data-stu-id="ff902-110">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="ff902-111">Można także połączyć oba składni pokazano tylko polecenie get i składni pokazano tylko zestawu i tworzy właściwość, która ma zarówno get i set.</span><span class="sxs-lookup"><span data-stu-id="ff902-111">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="ff902-112">Ten ostatni formularz umożliwia zawiesić modyfikatory dostępności różnych i atrybuty get i ustaw metody.</span><span class="sxs-lookup"><span data-stu-id="ff902-112">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="ff902-113">Gdy *IndexerName* jest `Item`, kompilator traktuje właściwość jako domyślnie indeksowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="ff902-113">When the *IndexerName* is `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="ff902-114">A *Właściwość indeksowana domyślnie* jest właściwością, której będziesz mieć dostęp za pomocą składni tablicy w wystąpieniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="ff902-114">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="ff902-115">Na przykład jeśli `obj` jest obiektem typu, który definiuje tę właściwość, składnia `obj.[index]` służy do dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="ff902-115">For example, if `obj` is an object of the type that defines this property, the syntax `obj.[index]` is used to access the property.</span></span>

<span data-ttu-id="ff902-116">Składnia do uzyskiwania dostępu do właściwości indeksowanych niestandardowy jest zapewnienie nazwy właściwości oraz indeksu w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="ff902-116">The syntax for accessing a nondefault indexed property is to provide the name of the property and the index in parentheses.</span></span> <span data-ttu-id="ff902-117">Na przykład, jeśli właściwość jest `Ordinal`, możesz zapisać `obj.Ordinal(index)` do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="ff902-117">For example, if the property is `Ordinal`, you write `obj.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="ff902-118">Niezależnie od tego formularza, którego używasz, zawsze należy używać rozwinięte forma `set` metody dla właściwości indeksowanej.</span><span class="sxs-lookup"><span data-stu-id="ff902-118">Regardless of which form you use, you should always use the curried form for the `set` method on an indexed property.</span></span> <span data-ttu-id="ff902-119">Aby uzyskać informacje o funkcje rozwinięte, zobacz [funkcji](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="ff902-119">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="ff902-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff902-120">Example</span></span>

<span data-ttu-id="ff902-121">Poniższy przykładowy kod przedstawia definicja oraz wykorzystanie domyślnych i właściwości indeksowanych innych niż domyślne, które i ustaw metody get.</span><span class="sxs-lookup"><span data-stu-id="ff902-121">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="ff902-122">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="ff902-122">Output</span></span>

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a><span data-ttu-id="ff902-123">Właściwości indeksowane wiele zmiennych indeksu</span><span class="sxs-lookup"><span data-stu-id="ff902-123">Indexed Properties with Multiple Index Variables</span></span>
<span data-ttu-id="ff902-124">Właściwości indeksowane może mieć więcej niż jedną zmienną indeksu.</span><span class="sxs-lookup"><span data-stu-id="ff902-124">Indexed properties can have more than one index variable.</span></span> <span data-ttu-id="ff902-125">W takim przypadku zmienne są oddzielone przecinkami, gdy jest używana.</span><span class="sxs-lookup"><span data-stu-id="ff902-125">In that case, the variables are separated by commas when the property is used.</span></span> <span data-ttu-id="ff902-126">W takich właściwości metody zestaw musi mieć dwa argumenty curried, z których pierwszy jest spójnych kolekcji zawierający klucze, a drugi z nich jest wartość.</span><span class="sxs-lookup"><span data-stu-id="ff902-126">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value being set.</span></span>

<span data-ttu-id="ff902-127">Poniższy kod przedstawia użycie właściwości indeksowanych wiele zmiennych indeksu.</span><span class="sxs-lookup"><span data-stu-id="ff902-127">The following code demonstrates the use of an indexed property with multiple index variables.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="ff902-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff902-128">See Also</span></span>
[<span data-ttu-id="ff902-129">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ff902-129">Members</span></span>](index.md)
