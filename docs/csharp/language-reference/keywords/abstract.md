---
title: C# odwołanie abstrakcyjne
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 547ecd9ff823f61bf3995c02959235b65a4a3979
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606143"
---
# <a name="abstract-c-reference"></a><span data-ttu-id="75310-102">abstract (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="75310-102">abstract (C# Reference)</span></span>
<span data-ttu-id="75310-103">`abstract` Modyfikator wskazuje, że modyfikowany element nie ma lub niekompletnej implementacji.</span><span class="sxs-lookup"><span data-stu-id="75310-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="75310-104">Modyfikator abstrakcyjny może być używany z klasami, metodami, właściwościami, indeksatorami i zdarzeniami.</span><span class="sxs-lookup"><span data-stu-id="75310-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="75310-105">`abstract` Użyj modyfikatora w deklaracji klasy, aby wskazać, że Klasa jest przeznaczona tylko jako klasa bazowa innych klas, ale nie jest tworzona samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="75310-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes, not instantiated on its own.</span></span> <span data-ttu-id="75310-106">Elementy członkowskie oznaczone jako abstrakcyjne muszą być zaimplementowane przez nieabstrakcyjne klasy, które pochodzą z klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="75310-106">Members marked as abstract must be implemented by non-abstract classes that derive from the abstract class.</span></span>
  
## <a name="example"></a><span data-ttu-id="75310-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="75310-107">Example</span></span>  
 <span data-ttu-id="75310-108">W tym przykładzie Klasa `Square` musi dostarczyć `GetArea` implementację, ponieważ pochodzi ona z `Shape`:</span><span class="sxs-lookup"><span data-stu-id="75310-108">In this example, the class `Square` must provide an implementation of `GetArea` because it derives from `Shape`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 <span data-ttu-id="75310-109">Klasy abstrakcyjne mają następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="75310-109">Abstract classes have the following features:</span></span>  
  
- <span data-ttu-id="75310-110">Nie można utworzyć wystąpienia klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="75310-110">An abstract class cannot be instantiated.</span></span>  
  
- <span data-ttu-id="75310-111">Klasa abstrakcyjna może zawierać metody abstrakcyjne i metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="75310-111">An abstract class may contain abstract methods and accessors.</span></span>  
  
- <span data-ttu-id="75310-112">Nie można zmodyfikować klasy abstrakcyjnej za pomocą modyfikatora [zapieczętowanego](./sealed.md) , ponieważ dwa Modyfikatory mają przeciwległe znaczenie.</span><span class="sxs-lookup"><span data-stu-id="75310-112">It is not possible to modify an abstract class with the [sealed](./sealed.md) modifier because the two modifiers have opposite meanings.</span></span> <span data-ttu-id="75310-113">Modyfikator uniemożliwia dziedziczenie klasy `abstract` , a modyfikator wymaga klasy do dziedziczenia. `sealed`</span><span class="sxs-lookup"><span data-stu-id="75310-113">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
- <span data-ttu-id="75310-114">Klasa nieabstrakcyjna pochodna klasy abstrakcyjnej musi zawierać rzeczywiste implementacje wszystkich dziedziczonych metod abstrakcyjnych i metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="75310-114">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="75310-115">`abstract` Użyj modyfikatora w deklaracji metody lub właściwości, aby wskazać, że metoda lub właściwość nie zawiera implementacji.</span><span class="sxs-lookup"><span data-stu-id="75310-115">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="75310-116">Metody abstrakcyjne mają następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="75310-116">Abstract methods have the following features:</span></span>  
  
- <span data-ttu-id="75310-117">Metoda abstrakcyjna jest niejawnie metodą wirtualną.</span><span class="sxs-lookup"><span data-stu-id="75310-117">An abstract method is implicitly a virtual method.</span></span>  
  
- <span data-ttu-id="75310-118">Deklaracje metody abstrakcyjnej są dozwolone tylko w klasach abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="75310-118">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
- <span data-ttu-id="75310-119">Ponieważ Deklaracja metody abstrakcyjnej nie zapewnia rzeczywistej implementacji, nie istnieje treść metody; Deklaracja metody po prostu kończyć się średnikiem i nie ma nawiasów klamrowych ({}) po podpisie.</span><span class="sxs-lookup"><span data-stu-id="75310-119">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="75310-120">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="75310-120">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="75310-121">Implementacja jest dostarczana przez przesłonięcie metody, która jest elementem członkowskim klasy nieabstrakcyjnej. [](./override.md)</span><span class="sxs-lookup"><span data-stu-id="75310-121">The implementation is provided by a method [override](./override.md), which is a member of a non-abstract class.</span></span>  
  
- <span data-ttu-id="75310-122">Wystąpił błąd podczas używania modyfikatorów [static](./static.md) lub [Virtual](./virtual.md) w deklaracji metody abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="75310-122">It is an error to use the [static](./static.md) or [virtual](./virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="75310-123">Właściwości abstrakcyjne zachowują się jak metody abstrakcyjne, z wyjątkiem różnic w składni deklaracji i wywołania.</span><span class="sxs-lookup"><span data-stu-id="75310-123">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
- <span data-ttu-id="75310-124">Wystąpił błąd podczas używania `abstract` modyfikatora dla właściwości statycznej.</span><span class="sxs-lookup"><span data-stu-id="75310-124">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
- <span data-ttu-id="75310-125">Abstrakcyjna dziedziczona właściwość może zostać przesłonięta w klasie pochodnej przez dołączenie deklaracji właściwości, [](./override.md) która używa modyfikatora przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="75310-125">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](./override.md) modifier.</span></span>  
  
 <span data-ttu-id="75310-126">Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [klasy abstrakcyjne i zapieczętowane oraz składowe klas](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="75310-126">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="75310-127">Klasa abstrakcyjna musi zapewniać implementację dla wszystkich elementów członkowskich interfejsu.</span><span class="sxs-lookup"><span data-stu-id="75310-127">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="75310-128">Klasa abstrakcyjna implementująca interfejs może mapować metody interfejsu na metody abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="75310-128">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="75310-129">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="75310-129">For example:</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a><span data-ttu-id="75310-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="75310-130">Example</span></span>  
 <span data-ttu-id="75310-131">W tym przykładzie Klasa `DerivedClass` pochodzi od klasy `BaseClass`abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="75310-131">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="75310-132">Klasa abstrakcyjna zawiera metodę `AbstractMethod`abstrakcyjną, i dwie `X` właściwości abstrakcyjne oraz `Y`.</span><span class="sxs-lookup"><span data-stu-id="75310-132">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 <span data-ttu-id="75310-133">W poprzednim przykładzie, jeśli spróbujesz utworzyć wystąpienie klasy abstrakcyjnej przy użyciu instrukcji podobnej do:</span><span class="sxs-lookup"><span data-stu-id="75310-133">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="75310-134">Zostanie wyświetlony komunikat o błędzie informujący, że kompilator nie może utworzyć wystąpienia klasy abstrakcyjnej "BaseClass".</span><span class="sxs-lookup"><span data-stu-id="75310-134">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="75310-135">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="75310-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="75310-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75310-136">See also</span></span>

- [<span data-ttu-id="75310-137">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="75310-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="75310-138">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="75310-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="75310-139">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="75310-139">Modifiers</span></span>](./modifiers.md)
- [<span data-ttu-id="75310-140">virtual</span><span class="sxs-lookup"><span data-stu-id="75310-140">virtual</span></span>](./virtual.md)
- [<span data-ttu-id="75310-141">override</span><span class="sxs-lookup"><span data-stu-id="75310-141">override</span></span>](./override.md)
- [<span data-ttu-id="75310-142">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="75310-142">C# Keywords</span></span>](./index.md)
