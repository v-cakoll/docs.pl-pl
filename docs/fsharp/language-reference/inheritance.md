---
title: Dziedziczenie (F#)
description: 'Dowiedz się, jak określać dziedziczenia relacji F # za pomocą słowa kluczowego "inherit".'
ms.date: 05/16/2016
ms.openlocfilehash: 3d0c0785fc595315a8283979b99d0ec4fc5cbc0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564793"
---
# <a name="inheritance"></a><span data-ttu-id="e5ec3-103">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="e5ec3-103">Inheritance</span></span>

<span data-ttu-id="e5ec3-104">Dziedziczenie jest używana do modelowania relacji "jest a", lub subtyping w programowanie zorientowane obiektowo.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-104">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>


## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="e5ec3-105">Określanie relacji dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="e5ec3-105">Specifying Inheritance Relationships</span></span>
<span data-ttu-id="e5ec3-106">Należy określić przy użyciu relacji dziedziczenia `inherit` — słowo kluczowe w deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-106">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="e5ec3-107">W poniższym przykładzie przedstawiono podstawowe syntaktycznych formularza.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-107">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="e5ec3-108">Klasa może mieć co najwyżej jeden bezpośredniej klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-108">A class can have at most one direct base class.</span></span> <span data-ttu-id="e5ec3-109">Jeśli nie określisz klasy podstawowej za pomocą `inherit` — słowo kluczowe, klasy niejawnie dziedziczy `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-109">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>


## <a name="inherited-members"></a><span data-ttu-id="e5ec3-110">Dziedziczone elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e5ec3-110">Inherited Members</span></span>
<span data-ttu-id="e5ec3-111">Jeśli klasa dziedziczy z innej klasy, metod i elementów członkowskich klasy podstawowej są dostępne użytkownikom klasy pochodnej, tak jakby były bezpośrednie elementy członkowskie klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-111">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="e5ec3-112">Wszelkie let — powiązania i parametrami konstruktora prywatne do klasy, a w związku z tym nie ma dostępu z klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-112">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="e5ec3-113">Słowo kluczowe `base` jest dostępna w klasach pochodnych i odwołuje się do wystąpienia klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-113">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="e5ec3-114">Jest on używany jak własny identyfikator.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-114">It is used like the self-identifier.</span></span>


## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="e5ec3-115">Metody wirtualne i zastąpień</span><span class="sxs-lookup"><span data-stu-id="e5ec3-115">Virtual Methods and Overrides</span></span>
<span data-ttu-id="e5ec3-116">Metody wirtualne (i właściwości) działają trochę inaczej w języku F # porównaniu z innymi językami .NET.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-116">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="e5ec3-117">Aby zadeklarować nowy wirtualny element członkowski, należy użyć `abstract` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-117">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="e5ec3-118">W tym niezależnie od tego, czy użytkownik udostępnia domyślną implementację dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-118">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="e5ec3-119">W związku z tym pełnej definicji wirtualnej metody w klasie podstawowej następujące tego wzorca:</span><span class="sxs-lookup"><span data-stu-id="e5ec3-119">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="e5ec3-120">I w klasie pochodnej przesłonięcie tej metody wirtualnej jest zgodna z tego wzorca:</span><span class="sxs-lookup"><span data-stu-id="e5ec3-120">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="e5ec3-121">W przypadku pominięcia domyślna Implementacja klasy podstawowej, klasa podstawowa staje się klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-121">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="e5ec3-122">Poniższy przykład kodu pokazuje deklaracji nowej metody wirtualnej `function1` w klasie podstawowej oraz sposób jej zastąpienie w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-122">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]
    
## <a name="constructors-and-inheritance"></a><span data-ttu-id="e5ec3-123">Konstruktory i dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="e5ec3-123">Constructors and Inheritance</span></span>
<span data-ttu-id="e5ec3-124">Konstruktor dla klasy podstawowej musi zostać wywołany w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-124">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="e5ec3-125">Argumenty dla konstruktora klasy podstawowej są wyświetlane na liście argumentów w `inherit` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-125">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="e5ec3-126">Należy określić wartości, które są używane w argumentach przekazany do konstruktora klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-126">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="e5ec3-127">Poniższy kod przedstawia klasa podstawowa i Klasa pochodna, gdzie klasy pochodnej wywołuje konstruktor klasy podstawowej w klauzuli dziedziczenia:</span><span class="sxs-lookup"><span data-stu-id="e5ec3-127">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="e5ec3-128">W przypadku wiele konstruktorów można użyć poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-128">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="e5ec3-129">Jest to pierwszy wiersz konstruktory klas pochodnych `inherit` klauzuli i pola są wyświetlane jako pola jawne, które są zadeklarowane z `val` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-129">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="e5ec3-130">Aby uzyskać więcej informacji, zobacz [pola jawne: `val` — słowo kluczowe](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="e5ec3-130">For more information, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="e5ec3-131">Alternatywy dla dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="e5ec3-131">Alternatives to Inheritance</span></span>
<span data-ttu-id="e5ec3-132">W przypadkach, gdy wymagane jest pomocnicze modyfikacja typu Rozważ użycie wyrażenia obiektu zamiast dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-132">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="e5ec3-133">Poniższy przykład przedstawia użycie wyrażenia obiektu jako alternatywę do utworzenia nowego typu pochodnego:</span><span class="sxs-lookup"><span data-stu-id="e5ec3-133">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="e5ec3-134">Aby uzyskać więcej informacji na temat wyrażenia obiektów, zobacz [wyrażenia obiektów](object-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e5ec3-134">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="e5ec3-135">Podczas tworzenia obiektu hierarchii, należy rozważyć użycie rozróżnianą Unię zamiast dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-135">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="e5ec3-136">Sumy rozłączne może również zachowanie modelu różne w różnych obiektów, które mają wspólny typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-136">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="e5ec3-137">Pojedynczy rozróżnianą Unię można często wyeliminować potrzebę szereg klas pochodnych, które są niewielkich zmian.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-137">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="e5ec3-138">Aby uzyskać informacje o rozłączne, zobacz [Suma rozłączna unie](discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="e5ec3-138">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="e5ec3-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5ec3-139">See Also</span></span>
[<span data-ttu-id="e5ec3-140">Wyrażenia obiektów</span><span class="sxs-lookup"><span data-stu-id="e5ec3-140">Object Expressions</span></span>](object-expressions.md)

[<span data-ttu-id="e5ec3-141">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="e5ec3-141">F# Language Reference</span></span>](index.md)
