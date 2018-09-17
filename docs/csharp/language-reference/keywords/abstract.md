---
title: abstract (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: d0a51afe61e75b750ed8bf336ca4636cb58dfbba
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45742248"
---
# <a name="abstract-c-reference"></a><span data-ttu-id="22f3b-102">abstract (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="22f3b-102">abstract (C# Reference)</span></span>
<span data-ttu-id="22f3b-103">`abstract` Modyfikator oznacza, że rzecz modyfikowanego ma implementacji brakujące lub niekompletne.</span><span class="sxs-lookup"><span data-stu-id="22f3b-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="22f3b-104">Abstrakcyjna modyfikatora można używać z klas, metod, właściwości, indeksatorów i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="22f3b-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="22f3b-105">Użyj `abstract` modyfikatora w deklaracji klasy, aby wskazać, że klasa jest przeznaczona do użycia wyłącznie jako klasa bazowa innych klas.</span><span class="sxs-lookup"><span data-stu-id="22f3b-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes.</span></span> <span data-ttu-id="22f3b-106">Elementy członkowskie oznaczony jako abstrakcyjny lub zawarte w klasie abstrakcyjnej, muszą być zaimplementowane przez klasy, które pochodzą z klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="22f3b-106">Members marked as abstract, or included in an abstract class, must be implemented by classes that derive from the abstract class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22f3b-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="22f3b-107">Example</span></span>  
 <span data-ttu-id="22f3b-108">W tym przykładzie klasa `Square` musi dostarczać implementację `Area` ponieważ dziedziczy `ShapesClass`:</span><span class="sxs-lookup"><span data-stu-id="22f3b-108">In this example, the class `Square` must provide an implementation of `Area` because it derives from `ShapesClass`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 <span data-ttu-id="22f3b-109">Klasy abstrakcyjne oferują następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="22f3b-109">Abstract classes have the following features:</span></span>  
  
-   <span data-ttu-id="22f3b-110">Nie można utworzyć wystąpienia klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="22f3b-110">An abstract class cannot be instantiated.</span></span>  
  
-   <span data-ttu-id="22f3b-111">Klasa abstrakcyjna może zawierać metody abstrakcyjne i metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="22f3b-111">An abstract class may contain abstract methods and accessors.</span></span>  
  
-   <span data-ttu-id="22f3b-112">Nie można modyfikować klasy abstrakcyjnej jest [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md) modyfikator ponieważ dwie modyfikatorów mają znaczenie odwrotną.</span><span class="sxs-lookup"><span data-stu-id="22f3b-112">It is not possible to modify an abstract class with the [sealed](../../../csharp/language-reference/keywords/sealed.md) modifier because the two modifers have opposite meanings.</span></span> <span data-ttu-id="22f3b-113">`sealed` Modyfikator zapobiega są dziedziczone przez klasy i `abstract` modyfikator wymaga klasy dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="22f3b-113">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
-   <span data-ttu-id="22f3b-114">Nieabstrakcyjnej klasy pochodnej z klasy abstrakcyjnej muszą zawierać rzeczywistej implementacji wszystkie odziedziczone metody abstrakcyjne i metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="22f3b-114">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="22f3b-115">Użyj `abstract` modyfikatora w deklaracji metody lub właściwości w celu wskazania, że metoda lub właściwość nie zawiera implementacji.</span><span class="sxs-lookup"><span data-stu-id="22f3b-115">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="22f3b-116">Metody abstrakcyjne oferują następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="22f3b-116">Abstract methods have the following features:</span></span>  
  
-   <span data-ttu-id="22f3b-117">Metoda abstrakcyjna jest niejawnie metodę wirtualną.</span><span class="sxs-lookup"><span data-stu-id="22f3b-117">An abstract method is implicitly a virtual method.</span></span>  
  
-   <span data-ttu-id="22f3b-118">Deklaracje metody abstrakcyjne są dozwolone tylko w klas abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="22f3b-118">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
-   <span data-ttu-id="22f3b-119">Ponieważ deklaracja metody abstrakcyjnej zapewnia nie rzeczywiste wdrożenie, jest nie treści metody; Deklaracja metody po prostu kończy się średnikiem wiąże się nie nawiasów klamrowych ({}) po podpis.</span><span class="sxs-lookup"><span data-stu-id="22f3b-119">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="22f3b-120">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="22f3b-120">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="22f3b-121">Implementacja znajduje się za pomocą metody [zastąpienia](../../../csharp/language-reference/keywords/override.md), który jest członkiem klasy nieabstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="22f3b-121">The implementation is provided by a method [override](../../../csharp/language-reference/keywords/override.md), which is a member of a non-abstract class.</span></span>  
  
-   <span data-ttu-id="22f3b-122">Jest to błąd, aby użyć [statyczne](../../../csharp/language-reference/keywords/static.md) lub [wirtualnego](../../../csharp/language-reference/keywords/virtual.md) Modyfikatory w deklaracji metody abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="22f3b-122">It is an error to use the [static](../../../csharp/language-reference/keywords/static.md) or [virtual](../../../csharp/language-reference/keywords/virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="22f3b-123">Właściwości abstrakcyjne zachowują się jak metody abstrakcyjne, z wyjątkiem różnic w składni deklaracji i wywoływania.</span><span class="sxs-lookup"><span data-stu-id="22f3b-123">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="22f3b-124">Jest to błąd, aby użyć `abstract` modyfikator na właściwość statyczna.</span><span class="sxs-lookup"><span data-stu-id="22f3b-124">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="22f3b-125">To właściwość dziedziczona abstrakcyjna może zostać przesłonięta w klasie pochodnej przez tym deklaracja właściwości, która używa [zastąpienia](../../../csharp/language-reference/keywords/override.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="22f3b-125">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](../../../csharp/language-reference/keywords/override.md) modifier.</span></span>  
  
 <span data-ttu-id="22f3b-126">Aby uzyskać więcej informacji na temat klasy abstrakcyjne, zobacz [abstrakcyjnych i zapieczętowanych klas i składowych klasy](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="22f3b-126">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="22f3b-127">Klasa abstrakcyjna należy podać implementacja dla wszystkich członków interfejsu.</span><span class="sxs-lookup"><span data-stu-id="22f3b-127">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="22f3b-128">Klasa abstrakcyjna, która implementuje interfejs może mapować metod interfejsu do metody abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="22f3b-128">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="22f3b-129">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="22f3b-129">For example:</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a><span data-ttu-id="22f3b-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="22f3b-130">Example</span></span>  
 <span data-ttu-id="22f3b-131">W tym przykładzie klasa `DerivedClass` pochodzi z klasy abstrakcyjnej `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="22f3b-131">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="22f3b-132">Abstrakcyjna klasa zawiera metody abstrakcyjnej, `AbstractMethod`, a dwie właściwości abstrakcyjnych, `X` i `Y`.</span><span class="sxs-lookup"><span data-stu-id="22f3b-132">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 <span data-ttu-id="22f3b-133">W poprzednim przykładzie, jeśli użytkownik podejmie próbę utworzenia wystąpienia klasy abstrakcyjnej, przy użyciu instrukcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="22f3b-133">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="22f3b-134">Otrzymasz błąd informujący o tym, że kompilator nie można utworzyć wystąpienia klasy abstrakcyjnej "BaseClass".</span><span class="sxs-lookup"><span data-stu-id="22f3b-134">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="22f3b-135">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="22f3b-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="22f3b-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22f3b-136">See Also</span></span>  

- [<span data-ttu-id="22f3b-137">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="22f3b-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="22f3b-138">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="22f3b-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="22f3b-139">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="22f3b-139">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="22f3b-140">virtual</span><span class="sxs-lookup"><span data-stu-id="22f3b-140">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
- [<span data-ttu-id="22f3b-141">override</span><span class="sxs-lookup"><span data-stu-id="22f3b-141">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
- [<span data-ttu-id="22f3b-142">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="22f3b-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
