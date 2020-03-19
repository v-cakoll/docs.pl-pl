---
title: Dziedziczenie
description: Dowiedz się, jak określić relacje dziedziczenia F# przy użyciu słowa kluczowego "dziedziczyć".
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400289"
---
# <a name="inheritance"></a><span data-ttu-id="7648a-103">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="7648a-103">Inheritance</span></span>

<span data-ttu-id="7648a-104">Dziedziczenie służy do modelowania relacji "is-a" lub podtypowania w programowaniu obiektowym.</span><span class="sxs-lookup"><span data-stu-id="7648a-104">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>

## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="7648a-105">Określanie relacji dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="7648a-105">Specifying Inheritance Relationships</span></span>

<span data-ttu-id="7648a-106">Relacje dziedziczenia można `inherit` określić przy użyciu słowa kluczowego w deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="7648a-106">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="7648a-107">Podstawowy formularz syntaktyczny jest pokazany w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7648a-107">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="7648a-108">Klasa może mieć co najwyżej jedną bezpośrednią klasę podstawową.</span><span class="sxs-lookup"><span data-stu-id="7648a-108">A class can have at most one direct base class.</span></span> <span data-ttu-id="7648a-109">Jeśli klasa podstawowa nie zostanie `inherit` określona przy użyciu słowa kluczowego, klasa niejawnie dziedziczy po pliku `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="7648a-109">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>

## <a name="inherited-members"></a><span data-ttu-id="7648a-110">Dziedziczone elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7648a-110">Inherited Members</span></span>

<span data-ttu-id="7648a-111">Jeśli klasa dziedziczy z innej klasy, metody i elementy członkowskie klasy podstawowej są dostępne dla użytkowników klasy pochodnej, tak jakby byli bezpośrednimi członkami klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7648a-111">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="7648a-112">Wszelkie let powiązania i parametry konstruktora są prywatne do klasy i w związku z tym nie można uzyskać dostępu z klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="7648a-112">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="7648a-113">Słowo `base` kluczowe jest dostępne w klasach pochodnych i odwołuje się do wystąpienia klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="7648a-113">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="7648a-114">Jest on używany jako własny identyfikator.</span><span class="sxs-lookup"><span data-stu-id="7648a-114">It is used like the self-identifier.</span></span>

## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="7648a-115">Metody wirtualne i zastępowanie</span><span class="sxs-lookup"><span data-stu-id="7648a-115">Virtual Methods and Overrides</span></span>

<span data-ttu-id="7648a-116">Metody wirtualne (i właściwości) działają nieco inaczej w języku F# w porównaniu z innymi językami .NET.</span><span class="sxs-lookup"><span data-stu-id="7648a-116">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="7648a-117">Aby zadeklarować nowego wirtualnego `abstract` członka, użyj słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="7648a-117">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="7648a-118">Można to zrobić niezależnie od tego, czy należy podać implementację domyślną dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="7648a-118">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="7648a-119">W związku z tym pełna definicja metody wirtualnej w klasie podstawowej następuje następujący po zwzorzec:</span><span class="sxs-lookup"><span data-stu-id="7648a-119">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="7648a-120">W klasie pochodnej zastąpienie tej metody wirtualnej następuje po tym wzorcu:</span><span class="sxs-lookup"><span data-stu-id="7648a-120">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="7648a-121">Jeśli pominiesz domyślną implementację w klasie podstawowej, klasa podstawowa staje się klasą abstrakcyjną.</span><span class="sxs-lookup"><span data-stu-id="7648a-121">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="7648a-122">Poniższy przykład kodu ilustruje deklarację `function1` nowej metody wirtualnej w klasie podstawowej i jak zastąpić ją w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7648a-122">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a><span data-ttu-id="7648a-123">Konstruktorzy i dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="7648a-123">Constructors and Inheritance</span></span>

<span data-ttu-id="7648a-124">Konstruktor klasy podstawowej musi być wywoływana w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7648a-124">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="7648a-125">Argumenty dla konstruktora klasy podstawowej `inherit` są wyświetlane na liście argumentów w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7648a-125">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="7648a-126">Wartości, które są używane musi być określona na podstawie argumentów dostarczonych do konstruktora klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7648a-126">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="7648a-127">Poniższy kod przedstawia klasę podstawową i klasę pochodną, gdzie klasa pochodna wywołuje konstruktora klasy podstawowej w klauzuli dziedziczenia:</span><span class="sxs-lookup"><span data-stu-id="7648a-127">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="7648a-128">W przypadku wielu konstruktorów można użyć następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="7648a-128">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="7648a-129">Pierwszy wiersz konstruktorów klasy pochodnej `inherit` jest klauzula, a pola są wyświetlane `val` jako jawne pola, które są zadeklarowane za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="7648a-129">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="7648a-130">Aby uzyskać więcej informacji, zobacz [Pola jawne: `val` Słowo kluczowe](./members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="7648a-130">For more information, see [Explicit Fields: The `val` Keyword](./members/explicit-fields-the-val-keyword.md).</span></span>

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

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="7648a-131">Alternatywy dla dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="7648a-131">Alternatives to Inheritance</span></span>

<span data-ttu-id="7648a-132">W przypadkach, gdy wymagana jest niewielka modyfikacja typu, należy rozważyć użycie wyrażenia obiektu jako alternatywy dla dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="7648a-132">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="7648a-133">W poniższym przykładzie przedstawiono użycie wyrażenia obiektu jako alternatywy dla tworzenia nowego typu pochodnego:</span><span class="sxs-lookup"><span data-stu-id="7648a-133">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="7648a-134">Aby uzyskać więcej informacji o wyrażeniach obiektów, zobacz [Wyrażenia obiektów](object-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="7648a-134">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="7648a-135">Podczas tworzenia hierarchii obiektów należy rozważyć użycie unii dyskryminowanej zamiast dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="7648a-135">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="7648a-136">Dyskryminowane związki mogą również modelować zróżnicowane zachowanie różnych obiektów, które mają wspólny typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="7648a-136">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="7648a-137">Pojedyncza unia dyskryminowana może często wyeliminować potrzebę wielu klas pochodnych, które są mniejszymi zmianami siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="7648a-137">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="7648a-138">Aby uzyskać informacje na temat związków dyskryminowanych, zobacz [Związki dyskryminowane](discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="7648a-138">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7648a-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7648a-139">See also</span></span>

- [<span data-ttu-id="7648a-140">Wyrażenia obiektów</span><span class="sxs-lookup"><span data-stu-id="7648a-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="7648a-141">Odwołanie do języka F#</span><span class="sxs-lookup"><span data-stu-id="7648a-141">F# Language Reference</span></span>](index.md)
