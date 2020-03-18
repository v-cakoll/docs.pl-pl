---
title: streszczenie — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 96e8bbce2e67c316d5cd1cd78e3e2506dabead25
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713865"
---
# <a name="abstract-c-reference"></a><span data-ttu-id="b9574-102">abstract (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="b9574-102">abstract (C# Reference)</span></span>
<span data-ttu-id="b9574-103">Modyfikator `abstract` wskazuje, że modyfikowana rzecz ma brakjącą lub niekompletną implementację.</span><span class="sxs-lookup"><span data-stu-id="b9574-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="b9574-104">Modyfikator abstrakcyjny może służyć z klas, metody, właściwości, indeksatory i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b9574-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="b9574-105">Użyj `abstract` modyfikatora w deklaracji klasy, aby wskazać, że klasa jest przeznaczona tylko do klasy podstawowej innych klas, nie tworzone samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="b9574-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes, not instantiated on its own.</span></span> <span data-ttu-id="b9574-106">Elementy członkowskie oznaczone jako abstrakcyjne muszą być implementowane przez klasy nieabstrakcyjne, które wynikają z klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="b9574-106">Members marked as abstract must be implemented by non-abstract classes that derive from the abstract class.</span></span>
  
## <a name="example"></a><span data-ttu-id="b9574-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9574-107">Example</span></span>  
 <span data-ttu-id="b9574-108">W tym przykładzie `Square` klasa musi zapewnić `GetArea` implementację, `Shape`ponieważ pochodzi z:</span><span class="sxs-lookup"><span data-stu-id="b9574-108">In this example, the class `Square` must provide an implementation of `GetArea` because it derives from `Shape`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 <span data-ttu-id="b9574-109">Klasy abstrakcyjne mają następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="b9574-109">Abstract classes have the following features:</span></span>  
  
- <span data-ttu-id="b9574-110">Nie można utworzyć wystąpienia klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="b9574-110">An abstract class cannot be instantiated.</span></span>  
  
- <span data-ttu-id="b9574-111">Klasa abstrakcyjna może zawierać metody abstrakcyjne i akcesory.</span><span class="sxs-lookup"><span data-stu-id="b9574-111">An abstract class may contain abstract methods and accessors.</span></span>  
  
- <span data-ttu-id="b9574-112">Nie jest możliwe modyfikowanie klasy abstrakcyjnej za pomocą [modyfikatora zapieczętowanego,](./sealed.md) ponieważ dwa modyfikatory mają przeciwstawne znaczenie.</span><span class="sxs-lookup"><span data-stu-id="b9574-112">It is not possible to modify an abstract class with the [sealed](./sealed.md) modifier because the two modifiers have opposite meanings.</span></span> <span data-ttu-id="b9574-113">Modyfikator `sealed` zapobiega dziedziczenia klasy `abstract` i modyfikator wymaga klasy do dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="b9574-113">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
- <span data-ttu-id="b9574-114">Klasa nieabstrakcyjna pochodząca z klasy abstrakcyjnej musi zawierać rzeczywiste implementacje wszystkich dziedziczonych metod abstrakcyjnych i akcesorów.</span><span class="sxs-lookup"><span data-stu-id="b9574-114">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="b9574-115">Użyj `abstract` modyfikatora w deklaracji metody lub właściwości, aby wskazać, że metoda lub właściwość nie zawiera implementacji.</span><span class="sxs-lookup"><span data-stu-id="b9574-115">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="b9574-116">Metody abstrakcyjne mają następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="b9574-116">Abstract methods have the following features:</span></span>  
  
- <span data-ttu-id="b9574-117">Metoda abstrakcyjna jest niejawnie metodą wirtualną.</span><span class="sxs-lookup"><span data-stu-id="b9574-117">An abstract method is implicitly a virtual method.</span></span>  
  
- <span data-ttu-id="b9574-118">Deklaracje metody abstrakcyjne są dozwolone tylko w klasach abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="b9574-118">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
- <span data-ttu-id="b9574-119">Ponieważ deklaracja metody abstrakcyjnej nie zapewnia rzeczywistej implementacji, nie ma treści metody; deklaracja metody po prostu kończy się średnikiem i nie ma żadnych nawiasów klamrowych ({ }) po podpisie.</span><span class="sxs-lookup"><span data-stu-id="b9574-119">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="b9574-120">Przykład:</span><span class="sxs-lookup"><span data-stu-id="b9574-120">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="b9574-121">Implementacja jest dostarczana przez [override](./override.md)metody , który jest członkiem klasy nieabstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="b9574-121">The implementation is provided by a method [override](./override.md), which is a member of a non-abstract class.</span></span>  
  
- <span data-ttu-id="b9574-122">Jest to błąd, aby użyć modyfikatorów [statycznych](./static.md) lub [wirtualnych](./virtual.md) w deklaracji metody abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="b9574-122">It is an error to use the [static](./static.md) or [virtual](./virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="b9574-123">Właściwości abstrakcyjne zachowują się jak metody abstrakcyjne, z wyjątkiem różnic w składni deklaracji i wywołania.</span><span class="sxs-lookup"><span data-stu-id="b9574-123">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
- <span data-ttu-id="b9574-124">Jest to błąd, `abstract` aby użyć modyfikatora we właściwości statycznej.</span><span class="sxs-lookup"><span data-stu-id="b9574-124">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
- <span data-ttu-id="b9574-125">Właściwość dziedziczona abstrakcyjne mogą być zastąpione w klasie pochodnej, dołączając deklarację właściwości, która używa modyfikatora [zastępowania.](./override.md)</span><span class="sxs-lookup"><span data-stu-id="b9574-125">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](./override.md) modifier.</span></span>  
  
 <span data-ttu-id="b9574-126">Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [Klasy abstrakcyjne i zapieczętowane oraz Elementy członkowskie klasy](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="b9574-126">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="b9574-127">Klasa abstrakcyjna musi zapewnić implementację dla wszystkich elementów członkowskich interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b9574-127">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="b9574-128">Klasa abstrakcyjna, która implementuje interfejs może mapować metody interfejsu na metody abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="b9574-128">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="b9574-129">Przykład:</span><span class="sxs-lookup"><span data-stu-id="b9574-129">For example:</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a><span data-ttu-id="b9574-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9574-130">Example</span></span>  
 <span data-ttu-id="b9574-131">W tym przykładzie `DerivedClass` klasa pochodzi z klasy `BaseClass`abstrakcyjnej .</span><span class="sxs-lookup"><span data-stu-id="b9574-131">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="b9574-132">Klasa abstrakcyjna zawiera metodę `AbstractMethod`abstrakcyjną i dwie `X` `Y`właściwości abstrakcyjne i .</span><span class="sxs-lookup"><span data-stu-id="b9574-132">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 <span data-ttu-id="b9574-133">W poprzednim przykładzie, jeśli spróbujesz utworzyć wystąpienia klasy abstrakcyjnej przy użyciu instrukcji w stylu:</span><span class="sxs-lookup"><span data-stu-id="b9574-133">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="b9574-134">Pojawi się błąd mówiący, że kompilator nie może utworzyć wystąpienia klasy abstrakcyjnej "BaseClass".</span><span class="sxs-lookup"><span data-stu-id="b9574-134">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b9574-135">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b9574-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b9574-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9574-136">See also</span></span>

- [<span data-ttu-id="b9574-137">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="b9574-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b9574-138">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="b9574-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b9574-139">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="b9574-139">Modifiers</span></span>](index.md)
- [<span data-ttu-id="b9574-140">virtual</span><span class="sxs-lookup"><span data-stu-id="b9574-140">virtual</span></span>](./virtual.md)
- [<span data-ttu-id="b9574-141">override</span><span class="sxs-lookup"><span data-stu-id="b9574-141">override</span></span>](./override.md)
- [<span data-ttu-id="b9574-142">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="b9574-142">C# Keywords</span></span>](./index.md)
