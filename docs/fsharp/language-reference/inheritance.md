---
title: Dziedziczenie (F#)
description: "Dowiedz się, jak określać dziedziczenia relacji F # za pomocą słowa kluczowego \"inherit\"."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b38ab2f6-7ba7-4839-8eff-e6bd6cfd2b2f
ms.openlocfilehash: 331c8f4e39aacd9d5e55bfbaf584f037e58d36a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="inheritance"></a><span data-ttu-id="1949f-104">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="1949f-104">Inheritance</span></span>

<span data-ttu-id="1949f-105">Dziedziczenie jest używana do modelowania relacji "jest a", lub subtyping w programowanie zorientowane obiektowo.</span><span class="sxs-lookup"><span data-stu-id="1949f-105">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>


## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="1949f-106">Określanie relacji dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="1949f-106">Specifying Inheritance Relationships</span></span>
<span data-ttu-id="1949f-107">Należy określić przy użyciu relacji dziedziczenia `inherit` — słowo kluczowe w deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="1949f-107">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="1949f-108">W poniższym przykładzie przedstawiono podstawowe syntaktycznych formularza.</span><span class="sxs-lookup"><span data-stu-id="1949f-108">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="1949f-109">Klasa może mieć co najwyżej jeden bezpośredniej klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="1949f-109">A class can have at most one direct base class.</span></span> <span data-ttu-id="1949f-110">Jeśli nie określisz klasy podstawowej za pomocą `inherit` — słowo kluczowe, klasy niejawnie dziedziczy `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="1949f-110">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>


## <a name="inherited-members"></a><span data-ttu-id="1949f-111">Dziedziczone elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1949f-111">Inherited Members</span></span>
<span data-ttu-id="1949f-112">Jeśli klasa dziedziczy z innej klasy, metod i elementów członkowskich klasy podstawowej są dostępne użytkownikom klasy pochodnej, tak jakby były bezpośrednie elementy członkowskie klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="1949f-112">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="1949f-113">Wszelkie let — powiązania i parametrami konstruktora prywatne do klasy, a w związku z tym nie ma dostępu z klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="1949f-113">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="1949f-114">Słowo kluczowe `base` jest dostępna w klasach pochodnych i odwołuje się do wystąpienia klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="1949f-114">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="1949f-115">Jest on używany jak własny identyfikator.</span><span class="sxs-lookup"><span data-stu-id="1949f-115">It is used like the self-identifier.</span></span>


## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="1949f-116">Metody wirtualne i zastąpień</span><span class="sxs-lookup"><span data-stu-id="1949f-116">Virtual Methods and Overrides</span></span>
<span data-ttu-id="1949f-117">Metody wirtualne (i właściwości) działają trochę inaczej w języku F # porównaniu z innymi językami .NET.</span><span class="sxs-lookup"><span data-stu-id="1949f-117">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="1949f-118">Aby zadeklarować nowy wirtualny element członkowski, należy użyć `abstract` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="1949f-118">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="1949f-119">W tym niezależnie od tego, czy użytkownik udostępnia domyślną implementację dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="1949f-119">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="1949f-120">W związku z tym pełnej definicji wirtualnej metody w klasie podstawowej następujące tego wzorca:</span><span class="sxs-lookup"><span data-stu-id="1949f-120">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="1949f-121">I w klasie pochodnej przesłonięcie tej metody wirtualnej jest zgodna z tego wzorca:</span><span class="sxs-lookup"><span data-stu-id="1949f-121">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="1949f-122">W przypadku pominięcia domyślna Implementacja klasy podstawowej, klasa podstawowa staje się klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="1949f-122">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="1949f-123">Poniższy przykład kodu pokazuje deklaracji nowej metody wirtualnej `function1` w klasie podstawowej oraz sposób jej zastąpienie w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="1949f-123">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]
    
## <a name="constructors-and-inheritance"></a><span data-ttu-id="1949f-124">Konstruktory i dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="1949f-124">Constructors and Inheritance</span></span>
<span data-ttu-id="1949f-125">Konstruktor dla klasy podstawowej musi zostać wywołany w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="1949f-125">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="1949f-126">Argumenty dla konstruktora klasy podstawowej są wyświetlane na liście argumentów w `inherit` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="1949f-126">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="1949f-127">Należy określić wartości, które są używane w argumentach przekazany do konstruktora klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="1949f-127">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="1949f-128">Poniższy kod przedstawia klasa podstawowa i Klasa pochodna, gdzie klasy pochodnej wywołuje konstruktor klasy podstawowej w klauzuli dziedziczenia:</span><span class="sxs-lookup"><span data-stu-id="1949f-128">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="1949f-129">W przypadku wiele konstruktorów można użyć poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="1949f-129">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="1949f-130">Jest to pierwszy wiersz konstruktory klas pochodnych `inherit` klauzuli i pola są wyświetlane jako pola jawne, które są zadeklarowane z `val` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="1949f-130">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="1949f-131">Aby uzyskać więcej informacji, zobacz [pola jawne: `val` — słowo kluczowe](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="1949f-131">For more information, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

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

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="1949f-132">Alternatywy dla dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="1949f-132">Alternatives to Inheritance</span></span>
<span data-ttu-id="1949f-133">W przypadkach, gdy wymagane jest pomocnicze modyfikacja typu Rozważ użycie wyrażenia obiektu zamiast dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="1949f-133">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="1949f-134">Poniższy przykład przedstawia użycie wyrażenia obiektu jako alternatywę do utworzenia nowego typu pochodnego:</span><span class="sxs-lookup"><span data-stu-id="1949f-134">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="1949f-135">Aby uzyskać więcej informacji na temat wyrażenia obiektów, zobacz [wyrażenia obiektów](object-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1949f-135">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="1949f-136">Podczas tworzenia obiektu hierarchii, należy rozważyć użycie rozróżnianą Unię zamiast dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="1949f-136">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="1949f-137">Sumy rozłączne może również zachowanie modelu różne w różnych obiektów, które mają wspólny typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="1949f-137">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="1949f-138">Pojedynczy rozróżnianą Unię można często wyeliminować potrzebę szereg klas pochodnych, które są niewielkich zmian.</span><span class="sxs-lookup"><span data-stu-id="1949f-138">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="1949f-139">Aby uzyskać informacje o rozłączne, zobacz [Suma rozłączna unie](discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="1949f-139">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="1949f-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1949f-140">See Also</span></span>
[<span data-ttu-id="1949f-141">Wyrażenia obiektów</span><span class="sxs-lookup"><span data-stu-id="1949f-141">Object Expressions</span></span>](object-expressions.md)

[<span data-ttu-id="1949f-142">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="1949f-142">F# Language Reference</span></span>](index.md)
