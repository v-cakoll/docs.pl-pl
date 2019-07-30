---
title: Dziedziczenie
description: Dowiedz się, F# jak określić relacje dziedziczenia przy użyciu słowa kluczowego "inherit".
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627669"
---
# <a name="inheritance"></a><span data-ttu-id="380f6-103">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="380f6-103">Inheritance</span></span>

<span data-ttu-id="380f6-104">Dziedziczenie służy do modelowania relacji "is-a" lub podpisywania w programowaniu zorientowanym obiektowo.</span><span class="sxs-lookup"><span data-stu-id="380f6-104">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>

## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="380f6-105">Określanie relacji dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="380f6-105">Specifying Inheritance Relationships</span></span>

<span data-ttu-id="380f6-106">Relacje dziedziczenia można określić za pomocą `inherit` słowa kluczowego w deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="380f6-106">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="380f6-107">W poniższym przykładzie przedstawiono podstawową formę składni.</span><span class="sxs-lookup"><span data-stu-id="380f6-107">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="380f6-108">Klasa może mieć co najwyżej jedną bezpośrednią klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="380f6-108">A class can have at most one direct base class.</span></span> <span data-ttu-id="380f6-109">Jeśli nie określisz klasy bazowej przy użyciu `inherit` słowa kluczowego, Klasa niejawnie dziedziczy z. `System.Object`</span><span class="sxs-lookup"><span data-stu-id="380f6-109">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>

## <a name="inherited-members"></a><span data-ttu-id="380f6-110">Dziedziczone elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="380f6-110">Inherited Members</span></span>

<span data-ttu-id="380f6-111">Jeśli klasa dziedziczy z innej klasy, metody i składowe klasy bazowej są dostępne dla użytkowników klasy pochodnej, tak jakby były bezpośrednimi elementami członkowskimi klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="380f6-111">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="380f6-112">Wszystkie powiązania let i konstruktory są prywatne z klasą, w związku z czym nie można uzyskać do nich dostępu z klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="380f6-112">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="380f6-113">Słowo kluczowe `base` jest dostępne w klasach pochodnych i odwołuje się do wystąpienia klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="380f6-113">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="380f6-114">Jest on używany jako identyfikator samoobsługi.</span><span class="sxs-lookup"><span data-stu-id="380f6-114">It is used like the self-identifier.</span></span>

## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="380f6-115">Metody wirtualne i zastąpienia</span><span class="sxs-lookup"><span data-stu-id="380f6-115">Virtual Methods and Overrides</span></span>

<span data-ttu-id="380f6-116">Metody wirtualne (i właściwości) działają nieco inaczej w F# porównaniu z innymi językami .NET.</span><span class="sxs-lookup"><span data-stu-id="380f6-116">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="380f6-117">Aby zadeklarować nową wirtualną składową, należy użyć `abstract` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="380f6-117">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="380f6-118">Należy to zrobić niezależnie od tego, czy podajesz domyślną implementację dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="380f6-118">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="380f6-119">W rezultacie pełna definicja metody wirtualnej w klasie podstawowej jest zgodna z tym wzorcem:</span><span class="sxs-lookup"><span data-stu-id="380f6-119">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="380f6-120">I w klasie pochodnej przesłonięcie tej metody wirtualnej następuje po tym wzorcu:</span><span class="sxs-lookup"><span data-stu-id="380f6-120">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="380f6-121">Jeśli pominięto implementację domyślną w klasie bazowej, Klasa bazowa zostanie klasą abstrakcyjną.</span><span class="sxs-lookup"><span data-stu-id="380f6-121">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="380f6-122">Poniższy przykład kodu ilustruje deklarację nowej metody `function1` wirtualnej w klasie bazowej i jak zastąpić ją w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="380f6-122">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a><span data-ttu-id="380f6-123">Konstruktory i dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="380f6-123">Constructors and Inheritance</span></span>

<span data-ttu-id="380f6-124">Konstruktor klasy bazowej musi być wywołany w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="380f6-124">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="380f6-125">Argumenty konstruktora klasy bazowej pojawiają się na liście argumentów w `inherit` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="380f6-125">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="380f6-126">Wartości, które są używane, muszą być określone na podstawie argumentów dostarczonych do konstruktora klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="380f6-126">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="380f6-127">Poniższy kod przedstawia klasę bazową i klasę pochodną, gdzie Klasa pochodna wywołuje konstruktora klasy bazowej w klauzuli inherit:</span><span class="sxs-lookup"><span data-stu-id="380f6-127">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="380f6-128">W przypadku wielu konstruktorów można użyć poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="380f6-128">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="380f6-129">Pierwszym wierszem konstruktorów klas pochodnych jest `inherit` klauzula, a pola są wyświetlane jako jawne pola, które są zadeklarowane `val` za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="380f6-129">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="380f6-130">Aby uzyskać więcej informacji, [Zobacz pola jawne: `val` Słowo kluczowe](./members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="380f6-130">For more information, see [Explicit Fields: The `val` Keyword](./members/explicit-fields-the-val-keyword.md).</span></span>

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

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="380f6-131">Alternatywy do dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="380f6-131">Alternatives to Inheritance</span></span>

<span data-ttu-id="380f6-132">W przypadkach, gdy wymagana jest drobna modyfikacja typu, rozważ użycie wyrażenia obiektu jako alternatywy dla dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="380f6-132">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="380f6-133">Poniższy przykład ilustruje użycie wyrażenia obiektu jako alternatywę do tworzenia nowego typu pochodnego:</span><span class="sxs-lookup"><span data-stu-id="380f6-133">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="380f6-134">Aby uzyskać więcej informacji na temat wyrażeń obiektów, zobacz [wyrażenia obiektów](object-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="380f6-134">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="380f6-135">Podczas tworzenia hierarchii obiektów należy rozważyć użycie Unii rozłącznych zamiast dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="380f6-135">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="380f6-136">Związki rozłączne mogą również modelować różne zachowania różnych obiektów, które współużytkują wspólny typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="380f6-136">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="380f6-137">Pojedyncza Unia rozłączna może często wyeliminować konieczność stosowania szeregu klas pochodnych, które są niewielkimi zmianami.</span><span class="sxs-lookup"><span data-stu-id="380f6-137">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="380f6-138">Aby uzyskać informacje na temat związków rozłącznych, zobacz [związki](discriminated-unions.md)rozłączne.</span><span class="sxs-lookup"><span data-stu-id="380f6-138">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="380f6-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="380f6-139">See also</span></span>

- [<span data-ttu-id="380f6-140">Wyrażenia obiektów</span><span class="sxs-lookup"><span data-stu-id="380f6-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="380f6-141">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="380f6-141">F# Language Reference</span></span>](index.md)
