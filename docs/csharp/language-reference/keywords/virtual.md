---
title: virtual (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: af5b7e3efdc98910ebbe7e061eba250cbe2d0c50
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207352"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="387cb-102">virtual (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="387cb-102">virtual (C# Reference)</span></span>
<span data-ttu-id="387cb-103">`virtual` — Słowo kluczowe służy do modyfikowania deklaracji — metoda, właściwość, indeksator lub zdarzenie i zezwalają na zastąpienia w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="387cb-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="387cb-104">Na przykład tej metody może zostać przesłonięta przez wszystkie klasy, która dziedziczy on:</span><span class="sxs-lookup"><span data-stu-id="387cb-104">For example, this method can be overridden by any class that inherits it:</span></span>  
  
```csharp  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 <span data-ttu-id="387cb-105">Implementacja elementu członkowskiego wirtualnego może zostać zmieniona przez [zastępowanie elementu członkowskiego](../../../csharp/language-reference/keywords/override.md) w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="387cb-105">The implementation of a virtual member can be changed by an [overriding member](../../../csharp/language-reference/keywords/override.md) in a derived class.</span></span> <span data-ttu-id="387cb-106">Aby uzyskać więcej informacji o sposobie używania `virtual` — słowo kluczowe, zobacz [przechowywanie wersji przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) i [wiedząc, gdy Użyj zastępowania i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="387cb-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="387cb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="387cb-107">Remarks</span></span>  
 <span data-ttu-id="387cb-108">Po wywołaniu metody wirtualnej typ środowiska wykonawczego obiektu jest sprawdzany pod kątem zastępowanie elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="387cb-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="387cb-109">Zastępowanie elementu członkowskiego w klasie pochodnej najbardziej nosi nazwę, która może być oryginalnego elementu członkowskiego, jeśli nie Klasa pochodna przesłoniła element członkowski.</span><span class="sxs-lookup"><span data-stu-id="387cb-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>  
  
 <span data-ttu-id="387cb-110">Domyślnie są niewirtualną metody.</span><span class="sxs-lookup"><span data-stu-id="387cb-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="387cb-111">Nie można zastąpić metody niewirtualnej.</span><span class="sxs-lookup"><span data-stu-id="387cb-111">You cannot override a non-virtual method.</span></span>  
  
 <span data-ttu-id="387cb-112">Nie można użyć `virtual` modyfikator z `static`, `abstract`, `private`, lub `override` modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="387cb-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="387cb-113">W poniższym przykładzie przedstawiono właściwości wirtualnych:</span><span class="sxs-lookup"><span data-stu-id="387cb-113">The following example shows a virtual property:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 <span data-ttu-id="387cb-114">Właściwości wirtualnych przypominają metody abstrakcyjne, z wyjątkiem różnice w deklaracji i wywołanie składni.</span><span class="sxs-lookup"><span data-stu-id="387cb-114">Virtual properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="387cb-115">Jest błędem `virtual` modyfikator na właściwość statyczna.</span><span class="sxs-lookup"><span data-stu-id="387cb-115">It is an error to use the `virtual` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="387cb-116">Wirtualne właściwość dziedziczona może zostać przesłonięta w klasie pochodnej przez tym deklaracji właściwości, która używa `override` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="387cb-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="387cb-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="387cb-117">Example</span></span>  
 <span data-ttu-id="387cb-118">W tym przykładzie `Shape` klasa zawiera dwie współrzędne `x`, `y`i `Area()` metoda wirtualna.</span><span class="sxs-lookup"><span data-stu-id="387cb-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="387cb-119">Kształt różnych klas takich jak `Circle`, `Cylinder`, i `Sphere` dziedziczą `Shape` klasy i powierzchni jest obliczana dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="387cb-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="387cb-120">Każda klasa pochodna ma własną implementację przesłonięcia `Area()`.</span><span class="sxs-lookup"><span data-stu-id="387cb-120">Each derived class has its own override implementation of `Area()`.</span></span>  
  
 <span data-ttu-id="387cb-121">Zwróć uwagę, że klasy dziedziczone `Circle`, `Sphere`, i `Cylinder` używają konstruktorów zainicjować klasy podstawowej, jak pokazano w poniższych deklaracji.</span><span class="sxs-lookup"><span data-stu-id="387cb-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>  
  
```csharp  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 <span data-ttu-id="387cb-122">Następujący program oblicza i wyświetla odpowiedniego obszaru dla każdego elementu za pomocą odpowiedniej implementacji `Area()` metody zgodnie z obiektu, który jest skojarzony z metodą.</span><span class="sxs-lookup"><span data-stu-id="387cb-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="387cb-123">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="387cb-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="387cb-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="387cb-124">See Also</span></span>  
 [<span data-ttu-id="387cb-125">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="387cb-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="387cb-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="387cb-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="387cb-127">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="387cb-127">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="387cb-128">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="387cb-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="387cb-129">Polimorfizm</span><span class="sxs-lookup"><span data-stu-id="387cb-129">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [<span data-ttu-id="387cb-130">abstract</span><span class="sxs-lookup"><span data-stu-id="387cb-130">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
 [<span data-ttu-id="387cb-131">override</span><span class="sxs-lookup"><span data-stu-id="387cb-131">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
 [<span data-ttu-id="387cb-132">new</span><span class="sxs-lookup"><span data-stu-id="387cb-132">new</span></span>](../../../csharp/language-reference/keywords/new.md)
