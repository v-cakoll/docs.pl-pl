---
title: Dziedziczenie
description: Dowiedz się, jak określić F# relacje dziedziczenia z użyciem słowa kluczowego "inherit".
ms.date: 05/16/2016
ms.openlocfilehash: 775ee52039caf4c4ab65f82fa21d4e536135a12a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937465"
---
# <a name="inheritance"></a><span data-ttu-id="eda0c-103">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="eda0c-103">Inheritance</span></span>

<span data-ttu-id="eda0c-104">Dziedziczenie jest używane do modelowania relacji "jest a" lub subtyping w programowanie zorientowane obiektowo.</span><span class="sxs-lookup"><span data-stu-id="eda0c-104">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>

## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="eda0c-105">Określanie relacji dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="eda0c-105">Specifying Inheritance Relationships</span></span>

<span data-ttu-id="eda0c-106">Należy określić za pomocą relacji dziedziczenia `inherit` — słowo kluczowe w deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="eda0c-106">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="eda0c-107">Podstawowe formie syntaktycznych przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="eda0c-107">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="eda0c-108">Klasa może mieć co najwyżej jedną bezpośrednią klasą bazową.</span><span class="sxs-lookup"><span data-stu-id="eda0c-108">A class can have at most one direct base class.</span></span> <span data-ttu-id="eda0c-109">Jeśli nie określisz klasę bazową przy użyciu `inherit` — słowo kluczowe, klasa dziedziczy niejawnie z `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="eda0c-109">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>

## <a name="inherited-members"></a><span data-ttu-id="eda0c-110">Dziedziczone elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="eda0c-110">Inherited Members</span></span>

<span data-ttu-id="eda0c-111">Jeśli klasa dziedziczy z innej klasy, metod i składowych klasy bazowej są dostępne dla użytkowników w klasie pochodnej, tak, jakby były one bezpośredni członkowie klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="eda0c-111">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="eda0c-112">Dowolny let — powiązania i parametry konstruktora są prywatne dla klasy i w związku z tym, nie są dostępne z klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="eda0c-112">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="eda0c-113">Słowo kluczowe `base` jest dostępna w klasach pochodnych i odnosi się do wystąpienia klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="eda0c-113">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="eda0c-114">Jest on używany, np. własny identyfikator.</span><span class="sxs-lookup"><span data-stu-id="eda0c-114">It is used like the self-identifier.</span></span>

## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="eda0c-115">Metody wirtualne i zastąpień</span><span class="sxs-lookup"><span data-stu-id="eda0c-115">Virtual Methods and Overrides</span></span>

<span data-ttu-id="eda0c-116">Metody wirtualne (i właściwości) działają trochę inaczej w F# porównaniu z innymi językami .NET.</span><span class="sxs-lookup"><span data-stu-id="eda0c-116">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="eda0c-117">Aby zadeklarować nowa wirtualna składowa, należy użyć `abstract` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="eda0c-117">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="eda0c-118">W tym niezależnie od tego, czy zapewniasz Domyślna implementacja tej metody.</span><span class="sxs-lookup"><span data-stu-id="eda0c-118">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="eda0c-119">Ten sposób kompletną definicję metody wirtualnej w klasie bazowej ze wzorcem to:</span><span class="sxs-lookup"><span data-stu-id="eda0c-119">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="eda0c-120">I w klasie pochodnej, zastąpienie tej metody wirtualnej korzysta z tego wzorca:</span><span class="sxs-lookup"><span data-stu-id="eda0c-120">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="eda0c-121">Jeżeli pominięto domyślną implementację w klasie bazowej, klasa bazowa staje się klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="eda0c-121">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="eda0c-122">Poniższy przykład kodu ilustruje deklarację nowej metody wirtualnej `function1` w klasie podstawowej oraz sposób jej zastąpienie w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="eda0c-122">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a><span data-ttu-id="eda0c-123">Konstruktory i dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="eda0c-123">Constructors and Inheritance</span></span>

<span data-ttu-id="eda0c-124">Należy wywołać konstruktora klasy podstawowej w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="eda0c-124">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="eda0c-125">Argumenty dla konstruktora klasy bazowej są wyświetlane na liście argumentów w `inherit` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="eda0c-125">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="eda0c-126">Należy określić wartości, które są używane w argumentach dostarczonego do konstruktora klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="eda0c-126">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="eda0c-127">Poniższy kod pokazuje klasa bazowa i Klasa pochodna, gdzie klasy pochodnej wywołuje konstruktora klasy bazowej w klauzuli dziedziczenia:</span><span class="sxs-lookup"><span data-stu-id="eda0c-127">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="eda0c-128">W przypadku wiele konstruktorów służy poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="eda0c-128">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="eda0c-129">Pierwszy wiersz konstruktorami klasy pochodnej jest `inherit` klauzuli i pola są wyświetlane jako jawne pola, które są zadeklarowane za pomocą `val` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="eda0c-129">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="eda0c-130">Aby uzyskać więcej informacji, zobacz [pola jawne: `val` — Słowo kluczowe](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="eda0c-130">For more information, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

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

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="eda0c-131">Alternatywy dla dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="eda0c-131">Alternatives to Inheritance</span></span>

<span data-ttu-id="eda0c-132">W przypadkach, w których wymagane jest pomocnicze modyfikacja typu należy wziąć pod uwagę przy użyciu wyrażenie obiektu jako alternatywę dla dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="eda0c-132">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="eda0c-133">Poniższy przykład ilustruje użycie wyrażenie obiektu jako alternatywę do tworzenia nowego typu pochodnego:</span><span class="sxs-lookup"><span data-stu-id="eda0c-133">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="eda0c-134">Aby uzyskać więcej informacji na temat wyrażeń obiektów, zobacz [wyrażenia obiektów](object-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="eda0c-134">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="eda0c-135">Podczas tworzenia obiektów hierarchii, należy rozważyć użycie złożenia dyskryminowanego zamiast dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="eda0c-135">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="eda0c-136">Związki dyskryminowane mogą również model zróżnicowane zachowanie różnych obiektów, które współużytkują wspólny typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="eda0c-136">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="eda0c-137">Pojedynczy złożenia dyskryminowanego można często wyeliminować potrzebę szereg klas pochodnych, które są niewielkich zmian.</span><span class="sxs-lookup"><span data-stu-id="eda0c-137">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="eda0c-138">Aby uzyskać informacji na temat związki dyskryminowane, zobacz [sumy rozłączne](discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="eda0c-138">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eda0c-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eda0c-139">See also</span></span>

- [<span data-ttu-id="eda0c-140">Wyrażenia obiektów</span><span class="sxs-lookup"><span data-stu-id="eda0c-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="eda0c-141">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="eda0c-141">F# Language Reference</span></span>](index.md)