---
title: wirtualny - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 0a6eb7bfcd598eb54b4b0cc5661d219367da2238
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237392"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="6a8b4-102">virtual (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6a8b4-102">virtual (C# Reference)</span></span>
<span data-ttu-id="6a8b4-103">`virtual` Słowo kluczowe jest używane do modyfikowania deklaracji metody, właściwości, indeksatora lub zdarzenia i umożliwia jej zastąpienie w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="6a8b4-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="6a8b4-104">Na przykład tej metody może zostać przesłonięta przez wszystkie klasy, która dziedziczy on:</span><span class="sxs-lookup"><span data-stu-id="6a8b4-104">For example, this method can be overridden by any class that inherits it:</span></span>  
  
```csharp  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 <span data-ttu-id="6a8b4-105">Implementacja członka wirtualnego mogą zostać zmienione przez [zastępującej składowej](../../../csharp/language-reference/keywords/override.md) w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="6a8b4-105">The implementation of a virtual member can be changed by an [overriding member](../../../csharp/language-reference/keywords/override.md) in a derived class.</span></span> <span data-ttu-id="6a8b4-106">Aby uzyskać więcej informacji o sposobie używania `virtual` — słowo kluczowe, zobacz [przechowywanie wersji przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) i [, wiedząc, gdy Użyj zastępowania i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="6a8b4-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a8b4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a8b4-107">Remarks</span></span>  
 <span data-ttu-id="6a8b4-108">Po wywołaniu metody wirtualnej typu run-time obiektu jest sprawdzane pod kątem zastępującej składowej.</span><span class="sxs-lookup"><span data-stu-id="6a8b4-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="6a8b4-109">Zastępującej składowej w klasie najbardziej pochodnej jest wywoływana, który może być oryginalnego elementu członkowskiego, jeśli nie Klasa pochodna przesłoniła elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="6a8b4-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>  
  
 <span data-ttu-id="6a8b4-110">Domyślnie metody są inne niż wirtualny.</span><span class="sxs-lookup"><span data-stu-id="6a8b4-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="6a8b4-111">Nie można zastąpić metody niewirtualnej.</span><span class="sxs-lookup"><span data-stu-id="6a8b4-111">You cannot override a non-virtual method.</span></span>  
  
 <span data-ttu-id="6a8b4-112">Nie można użyć `virtual` modyfikator z `static`, `abstract`, `private`, lub `override` modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="6a8b4-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="6a8b4-113">Właściwość wirtualną można znaleźć w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="6a8b4-113">The following example shows a virtual property:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 <span data-ttu-id="6a8b4-114">Właściwości wirtualne zachowują się jak metody abstrakcyjne, z wyjątkiem różnic w składni deklaracji i wywoływania.</span><span class="sxs-lookup"><span data-stu-id="6a8b4-114">Virtual properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="6a8b4-115">Jest to błąd, aby użyć `virtual` modyfikator na właściwość statyczna.</span><span class="sxs-lookup"><span data-stu-id="6a8b4-115">It is an error to use the `virtual` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="6a8b4-116">Wirtualne właściwość dziedziczona może zostać przesłonięta w klasie pochodnej przez tym deklaracja właściwości, która używa `override` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="6a8b4-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a8b4-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="6a8b4-117">Example</span></span>  
 <span data-ttu-id="6a8b4-118">W tym przykładzie `Shape` klasa zawiera dwie współrzędne `x`, `y`i `Area()` metodę wirtualną.</span><span class="sxs-lookup"><span data-stu-id="6a8b4-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="6a8b4-119">Klasy innego kształtu, takie jak `Circle`, `Cylinder`, i `Sphere` dziedziczą `Shape` klasy i obszar powierzchni jest obliczana dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="6a8b4-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="6a8b4-120">Każda klasa pochodna ma własną implementację zastąpienie `Area()`.</span><span class="sxs-lookup"><span data-stu-id="6a8b4-120">Each derived class has its own override implementation of `Area()`.</span></span>  
  
 <span data-ttu-id="6a8b4-121">Należy zauważyć, że klasy dziedziczone `Circle`, `Sphere`, i `Cylinder` używają konstruktorów, które inicjowania klasy bazowej, jak pokazano w poniższej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="6a8b4-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>  
  
```csharp  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 <span data-ttu-id="6a8b4-122">Następujący program oblicza i wyświetla odpowiedni obszar dla każdego elementu przez wywołanie odpowiedniej implementacji `Area()` metodę, zgodnie z obiektu, który jest skojarzony z metodą.</span><span class="sxs-lookup"><span data-stu-id="6a8b4-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6a8b4-123">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6a8b4-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6a8b4-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a8b4-124">See Also</span></span>

- [<span data-ttu-id="6a8b4-125">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6a8b4-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="6a8b4-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6a8b4-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6a8b4-127">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="6a8b4-127">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="6a8b4-128">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6a8b4-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="6a8b4-129">Polimorfizm</span><span class="sxs-lookup"><span data-stu-id="6a8b4-129">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
- [<span data-ttu-id="6a8b4-130">abstract</span><span class="sxs-lookup"><span data-stu-id="6a8b4-130">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
- [<span data-ttu-id="6a8b4-131">override</span><span class="sxs-lookup"><span data-stu-id="6a8b4-131">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
- [<span data-ttu-id="6a8b4-132">new</span><span class="sxs-lookup"><span data-stu-id="6a8b4-132">new</span></span>](../../../csharp/language-reference/keywords/new.md)
