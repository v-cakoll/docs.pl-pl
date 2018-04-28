---
title: Klasy abstrakcyjne (F#)
description: 'Więcej informacji na temat języka F # klas abstrakcyjnych, które pozostaw niektóre lub wszystkie elementy członkowskie niezaimplementowane i reprezentują często używane funkcje zestaw typów obiektów.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 0d7ca996de89c44a5cfb9197c1b515741a2303df
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="abstract-classes"></a><span data-ttu-id="2f004-103">Klasy abstrakcyjne</span><span class="sxs-lookup"><span data-stu-id="2f004-103">Abstract Classes</span></span>

<span data-ttu-id="2f004-104">*Klasy abstrakcyjne* klas, które opuszczają niektóre lub wszystkie elementy członkowskie niezaimplementowane, dzięki czemu można podać implementacji klasy pochodne.</span><span class="sxs-lookup"><span data-stu-id="2f004-104">*Abstract classes* are classes that leave some or all members unimplemented, so that implementations can be provided by derived classes.</span></span>

## <a name="syntax"></a><span data-ttu-id="2f004-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f004-105">Syntax</span></span>

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a><span data-ttu-id="2f004-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f004-106">Remarks</span></span>
<span data-ttu-id="2f004-107">W programowanie zorientowane obiektowo klasy abstrakcyjnej jest używany jako klasa podstawowa hierarchii i reprezentuje często używane funkcje zestaw typów obiektów.</span><span class="sxs-lookup"><span data-stu-id="2f004-107">In object-oriented programming, an abstract class is used as a base class of a hierarchy, and represents common functionality of a diverse set of object types.</span></span> <span data-ttu-id="2f004-108">Jak nazwa "abstract" wskazuje, klas abstrakcyjnych często nie odpowiada bezpośrednio na konkretnych obiektów w domenie problem.</span><span class="sxs-lookup"><span data-stu-id="2f004-108">As the name "abstract" implies, abstract classes often do not correspond directly onto concrete entities in the problem domain.</span></span> <span data-ttu-id="2f004-109">Jednak reprezentują, co wiele różnych obiektów konkretnych mają wspólną.</span><span class="sxs-lookup"><span data-stu-id="2f004-109">However, they do represent what many different concrete entities have in common.</span></span>

<span data-ttu-id="2f004-110">Klasy abstrakcyjne muszą mieć `AbstractClass` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2f004-110">Abstract classes must have the `AbstractClass` attribute.</span></span> <span data-ttu-id="2f004-111">Można mieć zaimplementowany i niezaimplementowane elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="2f004-111">They can have implemented and unimplemented members.</span></span> <span data-ttu-id="2f004-112">Użycie warunku *abstrakcyjny* po zastosowaniu do klasy jest taka sama jak w innych językach .NET; jednak użycie terminu *abstrakcyjny* po zastosowaniu do metody (i właściwości) jest nieco inne w języku F # z jego Użyj innych języków platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="2f004-112">The use of the term *abstract* when applied to a class is the same as in other .NET languages; however, the use of the term *abstract* when applied to methods (and properties) is a little different in F# from its use in other .NET languages.</span></span> <span data-ttu-id="2f004-113">W języku F #, gdy metoda jest oznaczona atrybutem `abstract` — słowo kluczowe, to oznacza, że element członkowski ma wpis, znany jako *miejsca wysyłania wirtualnego*, w tabeli wewnętrznej funkcji wirtualnych dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="2f004-113">In F#, when a method is marked with the `abstract` keyword, this indicates that a member has an entry, known as a *virtual dispatch slot*, in the internal table of virtual functions for that type.</span></span> <span data-ttu-id="2f004-114">Innymi słowy, metoda jest wirtualny, mimo że `virtual` — słowo kluczowe nie jest używany w języku F #.</span><span class="sxs-lookup"><span data-stu-id="2f004-114">In other words, the method is virtual, although the `virtual` keyword is not used in the F# language.</span></span> <span data-ttu-id="2f004-115">Słowo kluczowe `abstract` jest używane w metodach wirtualnych niezależnie od tego, czy metoda jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="2f004-115">The keyword `abstract` is used on virtual methods regardless of whether the method is implemented.</span></span> <span data-ttu-id="2f004-116">Deklaracja miejsca wysyłania wirtualnego jest oddzielony od definicji metody dla tego gniazda wysyłania.</span><span class="sxs-lookup"><span data-stu-id="2f004-116">The declaration of a virtual dispatch slot is separate from the definition of a method for that dispatch slot.</span></span> <span data-ttu-id="2f004-117">W związku z tym F # odpowiednikiem metody wirtualnej deklaracji i definicji w innym języku .NET jest kombinacją zarówno w deklaracji metody abstrakcyjnej, jak i w oddzielnych definicji, przy użyciu jednej `default` — słowo kluczowe lub `override` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="2f004-117">Therefore, the F# equivalent of a virtual method declaration and definition in another .NET language is a combination of both an abstract method declaration and a separate definition, with either the `default` keyword or the `override` keyword.</span></span> <span data-ttu-id="2f004-118">Aby uzyskać dodatkowe informacje i przykłady, zobacz [metody](members/methods.md).</span><span class="sxs-lookup"><span data-stu-id="2f004-118">For more information and examples, see [Methods](members/methods.md).</span></span>

<span data-ttu-id="2f004-119">Klasa jest traktowany jako abstract, tylko wtedy, gdy istnieją metody abstrakcyjne, które są zadeklarowane, ale nie zdefiniowano.</span><span class="sxs-lookup"><span data-stu-id="2f004-119">A class is considered abstract only if there are abstract methods that are declared but not defined.</span></span> <span data-ttu-id="2f004-120">W związku z tym klas, które mają metody abstrakcyjne nie są zawsze abstrakcyjnej klasy.</span><span class="sxs-lookup"><span data-stu-id="2f004-120">Therefore, classes that have abstract methods are not necessarily abstract classes.</span></span> <span data-ttu-id="2f004-121">Jeśli klasa ma niezdefiniowane metody abstrakcyjne, nie używaj **AbstractClass** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2f004-121">Unless a class has undefined abstract methods, do not use the **AbstractClass** attribute.</span></span>

<span data-ttu-id="2f004-122">W poprzednich składni *modyfikator dostępności* może być `public`, `private` lub `internal`.</span><span class="sxs-lookup"><span data-stu-id="2f004-122">In the previous syntax, *accessibility-modifier* can be `public`, `private` or `internal`.</span></span> <span data-ttu-id="2f004-123">Aby uzyskać więcej informacji, zobacz [kontroli dostępu](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="2f004-123">For more information, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="2f004-124">Podobnie jak w przypadku innych typów klas abstrakcyjnych może mieć klasy podstawowej i jeden lub więcej podstawowych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="2f004-124">As with other types, abstract classes can have a base class and one or more base interfaces.</span></span> <span data-ttu-id="2f004-125">Każdej klasy podstawowej lub interfejsu jest wyświetlany w osobnym wierszu razem z `inherit` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="2f004-125">Each base class or interface appears on a separate line together with the `inherit` keyword.</span></span>

<span data-ttu-id="2f004-126">Definicja typu klasy abstrakcyjnej mogą zawierać członków całkowicie zdefiniowane, ale może również zawierać abstrakcyjne elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="2f004-126">The type definition of an abstract class can contain fully defined members, but it can also contain abstract members.</span></span> <span data-ttu-id="2f004-127">Składnia abstrakcyjne elementy członkowskie jest wyświetlany osobno w poprzednim składni.</span><span class="sxs-lookup"><span data-stu-id="2f004-127">The syntax for abstract members is shown separately in the previous syntax.</span></span> <span data-ttu-id="2f004-128">W tej składni *podpis typu* elementu członkowskiego jest listę zawierającą parametr typy w kolejności i zwracane typy rozdzielone `->` tokeny i/lub `*` tokeny odpowiednio dla typu curried i spójnej kolekcji Parametry.</span><span class="sxs-lookup"><span data-stu-id="2f004-128">In this syntax, the *type signature* of a member is a list that contains the parameter types in order and the return types, separated by `->` tokens and/or `*` tokens as appropriate for curried and tupled parameters.</span></span> <span data-ttu-id="2f004-129">Składnia podpisów typ abstrakcyjny element członkowski jest taka sama jak używane w plikach sygnatury i wyświetlanego przez funkcję IntelliSense w edytorze kodu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f004-129">The syntax for abstract member type signatures is the same as that used in signature files and that shown by IntelliSense in the Visual Studio Code Editor.</span></span>

<span data-ttu-id="2f004-130">Poniższy kod ilustruje kształtu, które ma dwa nieabstrakcyjnej klasy pochodne, kwadratowych i okrąg klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="2f004-130">The following code illustrates an abstract class Shape, which has two non-abstract derived classes, Square and Circle.</span></span> <span data-ttu-id="2f004-131">W przykładzie dotyczące używania klas abstrakcyjnych, metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="2f004-131">The example shows how to use abstract classes, methods, and properties.</span></span> <span data-ttu-id="2f004-132">W tym przykładzie klasa ogólna kształtu reprezentuje typowe elementy okręgu konkretnych jednostek i kwadratowe.</span><span class="sxs-lookup"><span data-stu-id="2f004-132">In the example, the abstract class Shape represents the common elements of the concrete entities circle and square.</span></span> <span data-ttu-id="2f004-133">Wspólne funkcje wszystkich kształtów (w dwuwymiarowa współrzędnych) zamiast tego zostają wyodrębnione limit do klasy kształtu: pozycji na siatki, kąt obrotu i właściwości powierzchni i obwodu.</span><span class="sxs-lookup"><span data-stu-id="2f004-133">The common features of all shapes (in a two-dimensional coordinate system) are abstracted out into the Shape class: the position on the grid, an angle of rotation, and the area and perimeter properties.</span></span> <span data-ttu-id="2f004-134">Te można przesłonić, z wyjątkiem pozycji, działanie, którego nie można zmienić poszczególnych kształtów.</span><span class="sxs-lookup"><span data-stu-id="2f004-134">These can be overridden, except for position, the behavior of which individual shapes cannot change.</span></span>

<span data-ttu-id="2f004-135">Można zastąpić metody obrotu, jak klasy koło, która jest obracanie niezmiennej ze względu na jego symetrycznego.</span><span class="sxs-lookup"><span data-stu-id="2f004-135">The rotation method can be overridden, as in the Circle class, which is rotation invariant because of its symmetry.</span></span> <span data-ttu-id="2f004-136">Dlatego w klasie koło metody obrotu zastępuje metodę, która nie działa.</span><span class="sxs-lookup"><span data-stu-id="2f004-136">So in the Circle class, the rotation method is replaced by a method that does nothing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

<span data-ttu-id="2f004-137">**Dane wyjściowe:**</span><span class="sxs-lookup"><span data-stu-id="2f004-137">**Output:**</span></span>

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a><span data-ttu-id="2f004-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f004-138">See Also</span></span>
[<span data-ttu-id="2f004-139">Klasy</span><span class="sxs-lookup"><span data-stu-id="2f004-139">Classes</span></span>](classes.md)

[<span data-ttu-id="2f004-140">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2f004-140">Members</span></span>](members/index.md)

[<span data-ttu-id="2f004-141">Metody</span><span class="sxs-lookup"><span data-stu-id="2f004-141">Methods</span></span>](members/methods.md)

[<span data-ttu-id="2f004-142">Właściwości</span><span class="sxs-lookup"><span data-stu-id="2f004-142">Properties</span></span>](members/Properties.md)
