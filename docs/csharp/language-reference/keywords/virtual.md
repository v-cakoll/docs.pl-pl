---
title: C# odwołanie wirtualne
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 586e50818fc8ceaad5ca1925c0636b31015d81d4
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925373"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="71d4c-102">virtual (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="71d4c-102">virtual (C# Reference)</span></span>

<span data-ttu-id="71d4c-103">`virtual` Słowo kluczowe jest używane do modyfikacji deklaracji metody, właściwości, indeksatora lub zdarzenia i umożliwia jej zastąpienie w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="71d4c-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="71d4c-104">Na przykład ta metoda może zostać przesłonięta przez dowolną klasę, która ją dziedziczy:</span><span class="sxs-lookup"><span data-stu-id="71d4c-104">For example, this method can be overridden by any class that inherits it:</span></span>

```csharp
public virtual double Area() 
{
    return x * y;
}
```

<span data-ttu-id="71d4c-105">Implementację wirtualnego elementu członkowskiego można zmienić przez [zastępujący element członkowski](override.md) w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="71d4c-105">The implementation of a virtual member can be changed by an [overriding member](override.md) in a derived class.</span></span> <span data-ttu-id="71d4c-106">Aby uzyskać więcej informacji na temat sposobu używania `virtual` słowa kluczowego, zobacz [przechowywanie wersji z przesłonięciami i nowymi słowami kluczowymi](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) i [wiedzą, kiedy używać przesłonięć i nowych słów kluczowych](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="71d4c-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="71d4c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71d4c-107">Remarks</span></span>

<span data-ttu-id="71d4c-108">Gdy wywoływana jest metoda wirtualna, typ czasu wykonywania obiektu jest sprawdzany dla elementu członkowskiego, który jest zastępujący.</span><span class="sxs-lookup"><span data-stu-id="71d4c-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="71d4c-109">Nadrzędny element członkowski w najbardziej pochodnej klasie jest wywoływany, który może być pierwotną składową, jeśli żadna Klasa pochodna nie przesłoni elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="71d4c-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>

<span data-ttu-id="71d4c-110">Domyślnie metody nie są wirtualne.</span><span class="sxs-lookup"><span data-stu-id="71d4c-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="71d4c-111">Nie można zastąpić metody innej niż wirtualna.</span><span class="sxs-lookup"><span data-stu-id="71d4c-111">You cannot override a non-virtual method.</span></span>

<span data-ttu-id="71d4c-112">Nie `virtual` można użyć modyfikatora `abstract` `static`z modyfikatorami, `private`,, `override` lub.</span><span class="sxs-lookup"><span data-stu-id="71d4c-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="71d4c-113">W poniższym przykładzie przedstawiono Właściwość wirtualną:</span><span class="sxs-lookup"><span data-stu-id="71d4c-113">The following example shows a virtual property:</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="71d4c-114">Właściwości wirtualne zachowują się jak metody abstrakcyjne, z wyjątkiem różnic w składni deklaracji i wywołania.</span><span class="sxs-lookup"><span data-stu-id="71d4c-114">Virtual properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>

- <span data-ttu-id="71d4c-115">Wystąpił błąd podczas używania `virtual` modyfikatora dla właściwości statycznej.</span><span class="sxs-lookup"><span data-stu-id="71d4c-115">It is an error to use the `virtual` modifier on a static property.</span></span>

- <span data-ttu-id="71d4c-116">Wirtualną Właściwość dziedziczoną można zastąpić w klasie pochodnej przez dołączenie deklaracji właściwości, która używa `override` modyfikatora.</span><span class="sxs-lookup"><span data-stu-id="71d4c-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>

## <a name="example"></a><span data-ttu-id="71d4c-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="71d4c-117">Example</span></span>

<span data-ttu-id="71d4c-118">W tym przykładzie `Shape` Klasa zawiera dwie współrzędne `x`, `y`i `Area()` metodę wirtualną.</span><span class="sxs-lookup"><span data-stu-id="71d4c-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="71d4c-119">Różne klasy kształtu, takie `Circle`jak `Cylinder`, i `Sphere` dziedziczą `Shape` klasę, a obszar powierzchni jest obliczany dla każdego rysunku.</span><span class="sxs-lookup"><span data-stu-id="71d4c-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="71d4c-120">Każda klasa pochodna ma własną implementację `Area()`zastępującą.</span><span class="sxs-lookup"><span data-stu-id="71d4c-120">Each derived class has its own override implementation of `Area()`.</span></span>

<span data-ttu-id="71d4c-121">Zwróć uwagę, że dziedziczone `Circle`klasy `Sphere`, i `Cylinder` wszystkie używają konstruktorów, które inicjują klasę bazową, jak pokazano w poniższej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="71d4c-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

<span data-ttu-id="71d4c-122">Poniższy program oblicza i wyświetla odpowiedni obszar dla każdego rysunku przez wywoływanie odpowiedniej implementacji `Area()` metody, zgodnie z obiektem, który jest skojarzony z metodą.</span><span class="sxs-lookup"><span data-stu-id="71d4c-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a><span data-ttu-id="71d4c-123">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="71d4c-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="71d4c-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71d4c-124">See also</span></span>

- [<span data-ttu-id="71d4c-125">Polimorfizm</span><span class="sxs-lookup"><span data-stu-id="71d4c-125">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
- [<span data-ttu-id="71d4c-126">abstract</span><span class="sxs-lookup"><span data-stu-id="71d4c-126">abstract</span></span>](abstract.md)
- [<span data-ttu-id="71d4c-127">override</span><span class="sxs-lookup"><span data-stu-id="71d4c-127">override</span></span>](override.md)
- [<span data-ttu-id="71d4c-128">New (modyfikator)</span><span class="sxs-lookup"><span data-stu-id="71d4c-128">new (modifier)</span></span>](new-modifier.md)
