---
title: virtual - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 883e0a7f833c15d2c1cce6b3d52d16aad01a5cd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173461"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="922c7-102">virtual (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="922c7-102">virtual (C# Reference)</span></span>

<span data-ttu-id="922c7-103">Słowo `virtual` kluczowe służy do modyfikowania metody, właściwości, indeksatora lub deklaracji zdarzenia i zezwalania na jego zastępowanie w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="922c7-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="922c7-104">Na przykład ta metoda może zostać zastąpiona przez dowolną klasę, która ją dziedziczy:</span><span class="sxs-lookup"><span data-stu-id="922c7-104">For example, this method can be overridden by any class that inherits it:</span></span>

```csharp
public virtual double Area()
{
    return x * y;
}
```

<span data-ttu-id="922c7-105">Implementacja członka wirtualnego może zostać zmieniona przez [nadrzędny element członkowski](override.md) w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="922c7-105">The implementation of a virtual member can be changed by an [overriding member](override.md) in a derived class.</span></span> <span data-ttu-id="922c7-106">Aby uzyskać więcej informacji `virtual` na temat używania słowa kluczowego, zobacz [Przechowywanie wersji za pomocą słów kluczowych Zastępowania i Nowych](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) oraz Wiedza o [tym, kiedy należy używać zastępowania i nowych słów kluczowych](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="922c7-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="922c7-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="922c7-107">Remarks</span></span>

<span data-ttu-id="922c7-108">Po wywołaniu metody wirtualnej typ czasu wykonywania obiektu jest sprawdzany pod kątem nadrzędnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="922c7-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="922c7-109">Nadrzędny element członkowski w klasie najbardziej pochodnej jest wywoływana, która może być oryginalny element członkowski, jeśli żadna klasa pochodna nie zastąpi elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="922c7-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>

<span data-ttu-id="922c7-110">Domyślnie metody nie są wirtualne.</span><span class="sxs-lookup"><span data-stu-id="922c7-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="922c7-111">Nie można zastąpić metody niewirtualnej.</span><span class="sxs-lookup"><span data-stu-id="922c7-111">You cannot override a non-virtual method.</span></span>

<span data-ttu-id="922c7-112">Modyfikatora `virtual` nie `static`można `abstract` `private`używać `override` z modyfikatorem , , lub modyfikatorami.</span><span class="sxs-lookup"><span data-stu-id="922c7-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="922c7-113">W poniższym przykładzie przedstawiono właściwość wirtualną:</span><span class="sxs-lookup"><span data-stu-id="922c7-113">The following example shows a virtual property:</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="922c7-114">Właściwości wirtualne zachowują się jak metody wirtualne, z wyjątkiem różnic w składni deklaracji i wywołania.</span><span class="sxs-lookup"><span data-stu-id="922c7-114">Virtual properties behave like virtual methods, except for the differences in declaration and invocation syntax.</span></span>

- <span data-ttu-id="922c7-115">Jest to błąd, `virtual` aby użyć modyfikatora we właściwości statycznej.</span><span class="sxs-lookup"><span data-stu-id="922c7-115">It is an error to use the `virtual` modifier on a static property.</span></span>

- <span data-ttu-id="922c7-116">Właściwość dziedziczona wirtualna może zostać zastąpiona w klasie `override` pochodnej przez uwzględnienie deklaracji właściwości, która używa modyfikatora.</span><span class="sxs-lookup"><span data-stu-id="922c7-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>

## <a name="example"></a><span data-ttu-id="922c7-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="922c7-117">Example</span></span>

<span data-ttu-id="922c7-118">W tym przykładzie `Shape` klasa zawiera dwie `x` `y`współrzędne `Area()` , i metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="922c7-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="922c7-119">Różne klasy kształtów, `Sphere` takie `Shape` jak `Circle`, `Cylinder`i dziedziczą klasę, a powierzchnia jest obliczana dla każdej liczby.</span><span class="sxs-lookup"><span data-stu-id="922c7-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="922c7-120">Każda klasa pochodna ma własną `Area()`implementację zastąpienia .</span><span class="sxs-lookup"><span data-stu-id="922c7-120">Each derived class has its own override implementation of `Area()`.</span></span>

<span data-ttu-id="922c7-121">Należy zauważyć, że `Circle` `Sphere`odziedziczone klasy , i `Cylinder` wszystkie konstruktory użytkowania, które inicjują klasę podstawową, jak pokazano w poniższej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="922c7-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

<span data-ttu-id="922c7-122">Poniższy program oblicza i wyświetla odpowiedni obszar dla każdej liczby, wywołując `Area()` odpowiednią implementację metody, zgodnie z obiektem skojarzonym z metodą.</span><span class="sxs-lookup"><span data-stu-id="922c7-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a><span data-ttu-id="922c7-123">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="922c7-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="922c7-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="922c7-124">See also</span></span>

- [<span data-ttu-id="922c7-125">Polimorfizm</span><span class="sxs-lookup"><span data-stu-id="922c7-125">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
- [<span data-ttu-id="922c7-126">Abstrakcja</span><span class="sxs-lookup"><span data-stu-id="922c7-126">abstract</span></span>](abstract.md)
- [<span data-ttu-id="922c7-127">override</span><span class="sxs-lookup"><span data-stu-id="922c7-127">override</span></span>](override.md)
- [<span data-ttu-id="922c7-128">nowy (modyfikator)</span><span class="sxs-lookup"><span data-stu-id="922c7-128">new (modifier)</span></span>](new-modifier.md)
