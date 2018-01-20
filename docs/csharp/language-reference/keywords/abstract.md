---
title: "abstract (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords: abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bd26583c42302d8ce9ba4dd22119713548111236
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="abstract-c-reference"></a><span data-ttu-id="3445e-102">abstract (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="3445e-102">abstract (C# Reference)</span></span>
<span data-ttu-id="3445e-103">`abstract` Modyfikator oznacza, że element jest modyfikowany ma implementacji brakujące lub niekompletne.</span><span class="sxs-lookup"><span data-stu-id="3445e-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="3445e-104">Modyfikator abstract można używać z klas, metod, właściwości, indeksatorów i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3445e-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="3445e-105">Użyj `abstract` modyfikatora w deklaracji klasy, aby wskazać, że klasa jest przeznaczona tylko jako klasę podstawową innych klas.</span><span class="sxs-lookup"><span data-stu-id="3445e-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes.</span></span> <span data-ttu-id="3445e-106">Elementy członkowskie oznaczony jako abstrakcyjny lub częścią klasa abstrakcyjna, musi być implementowana przez klasy, które pochodzi z klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="3445e-106">Members marked as abstract, or included in an abstract class, must be implemented by classes that derive from the abstract class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3445e-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="3445e-107">Example</span></span>  
 <span data-ttu-id="3445e-108">W tym przykładzie klasa `Square` musi zapewniać implementację elementu `Area` ponieważ dziedziczy `ShapesClass`:</span><span class="sxs-lookup"><span data-stu-id="3445e-108">In this example, the class `Square` must provide an implementation of `Area` because it derives from `ShapesClass`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_1.cs)]  
  
 <span data-ttu-id="3445e-109">Klasy abstrakcyjne są następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="3445e-109">Abstract classes have the following features:</span></span>  
  
-   <span data-ttu-id="3445e-110">Nie można utworzyć wystąpienia klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="3445e-110">An abstract class cannot be instantiated.</span></span>  
  
-   <span data-ttu-id="3445e-111">Abstrakcyjna klasa może zawierać metody abstrakcyjne i metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="3445e-111">An abstract class may contain abstract methods and accessors.</span></span>  
  
-   <span data-ttu-id="3445e-112">Nie można modyfikować klasy abstrakcyjnej jest [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md) modyfikator ponieważ przeciwną znaczenie ma dwa modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="3445e-112">It is not possible to modify an abstract class with the [sealed](../../../csharp/language-reference/keywords/sealed.md) modifier because the two modifers have opposite meanings.</span></span> <span data-ttu-id="3445e-113">`sealed` Modyfikator uniemożliwia dziedziczone przez klasy i `abstract` modyfikator wymaga klasy być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="3445e-113">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
-   <span data-ttu-id="3445e-114">Nieabstrakcyjnej klasy pochodnej z klasy abstrakcyjnej muszą zawierać rzeczywiste implementacje wszystkich dziedziczonej metody abstrakcyjne i metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="3445e-114">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="3445e-115">Użyj `abstract` modyfikatora w deklaracji metody lub właściwości, aby wskazać, że ta metoda lub właściwość nie zawiera implementacji.</span><span class="sxs-lookup"><span data-stu-id="3445e-115">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="3445e-116">Metody abstrakcyjne są następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="3445e-116">Abstract methods have the following features:</span></span>  
  
-   <span data-ttu-id="3445e-117">Metoda abstrakcyjna niejawnie jest metoda wirtualna.</span><span class="sxs-lookup"><span data-stu-id="3445e-117">An abstract method is implicitly a virtual method.</span></span>  
  
-   <span data-ttu-id="3445e-118">Deklaracje metody abstrakcyjnej są dozwolone tylko w klasie abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="3445e-118">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
-   <span data-ttu-id="3445e-119">Deklaracja metody abstrakcyjnej udostępnia nie rzeczywistego wykonania, więc nie istnieje żadne treści metody; Deklaracja metody kończy się po prostu średnikiem i nie ma żadnych nawiasy klamrowe ({}) po podpisu.</span><span class="sxs-lookup"><span data-stu-id="3445e-119">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="3445e-120">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3445e-120">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="3445e-121">Implementacja jest zapewniana przez metodę zastępującą[zastąpienia](../../../csharp/language-reference/keywords/override.md), który jest elementem członkowskim klasy nieabstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="3445e-121">The implementation is provided by an overriding method[override](../../../csharp/language-reference/keywords/override.md), which is a member of a non-abstract class.</span></span>  
  
-   <span data-ttu-id="3445e-122">Jest błędem [statycznych](../../../csharp/language-reference/keywords/static.md) lub [wirtualnego](../../../csharp/language-reference/keywords/virtual.md) Modyfikatory w deklaracji metody abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="3445e-122">It is an error to use the [static](../../../csharp/language-reference/keywords/static.md) or [virtual](../../../csharp/language-reference/keywords/virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="3445e-123">Właściwości abstrakcyjne przypominają metody abstrakcyjne, z wyjątkiem różnice w deklaracji i wywołanie składni.</span><span class="sxs-lookup"><span data-stu-id="3445e-123">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="3445e-124">Jest błędem `abstract` modyfikator na właściwość statyczna.</span><span class="sxs-lookup"><span data-stu-id="3445e-124">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="3445e-125">Właściwość abstrakcyjną dziedziczone może zostać przesłonięta w klasie pochodnej przez tym deklaracji właściwości, która używa [zastąpienia](../../../csharp/language-reference/keywords/override.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="3445e-125">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](../../../csharp/language-reference/keywords/override.md) modifier.</span></span>  
  
 <span data-ttu-id="3445e-126">Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [abstrakcyjne i zapieczętowane klasy oraz członkowie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="3445e-126">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="3445e-127">Klasa abstrakcyjna musi zapewniać implementację dla wszystkich członków interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3445e-127">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="3445e-128">Klasa abstrakcyjna, która implementuje interfejs mogą być mapowane na metody abstrakcyjne metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3445e-128">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="3445e-129">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3445e-129">For example:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="3445e-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="3445e-130">Example</span></span>  
 <span data-ttu-id="3445e-131">W tym przykładzie klasa `DerivedClass` pochodzi z klasy abstrakcyjnej `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="3445e-131">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="3445e-132">Abstrakcyjna klasa zawiera metody abstrakcyjnej `AbstractMethod`, a dwie właściwości abstrakcyjnych, `X` i `Y`.</span><span class="sxs-lookup"><span data-stu-id="3445e-132">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_3.cs)]  
  
 <span data-ttu-id="3445e-133">W poprzednim przykładzie, jeśli podjęto próbę utworzenia wystąpienia klasy abstrakcyjnej przy użyciu instrukcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3445e-133">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="3445e-134">wystąpi błąd informujący o tym, że kompilator nie można utworzyć wystąpienia klasy abstrakcyjnej "Baseclass —".</span><span class="sxs-lookup"><span data-stu-id="3445e-134">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3445e-135">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3445e-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3445e-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3445e-136">See Also</span></span>  
 [<span data-ttu-id="3445e-137">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="3445e-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3445e-138">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3445e-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3445e-139">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="3445e-139">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="3445e-140">virtual</span><span class="sxs-lookup"><span data-stu-id="3445e-140">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
 [<span data-ttu-id="3445e-141">override</span><span class="sxs-lookup"><span data-stu-id="3445e-141">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
 [<span data-ttu-id="3445e-142">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="3445e-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
