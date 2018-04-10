---
title: static (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c47f4a19843039c27ef9f1602581d1004fb8fd76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="static-c-reference"></a><span data-ttu-id="f30af-102">static (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f30af-102">static (C# Reference)</span></span>
<span data-ttu-id="f30af-103">Użyj `static` modyfikator Aby zadeklarować statyczny element członkowski, który należy do samego typu, a nie z określonym obiektem.</span><span class="sxs-lookup"><span data-stu-id="f30af-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="f30af-104">`static` Modyfikatora można używać z klasami, pola, metody, właściwości, operatory, zdarzeń i konstruktorów, ale nie można użyć z indeksatorów, finalizatory lub typu innego niż klasy.</span><span class="sxs-lookup"><span data-stu-id="f30af-104">The `static` modifier can be used with classes, fields, methods, properties, operators, events, and constructors, but it cannot be used with indexers, finalizers, or types other than classes.</span></span> <span data-ttu-id="f30af-105">Aby uzyskać więcej informacji, zobacz [klasy statyczne i statycznych elementów członkowskich klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="f30af-105">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f30af-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="f30af-106">Example</span></span>  
 <span data-ttu-id="f30af-107">Następujące klasy jest zadeklarowany jako `static` i zawiera tylko `static` metod:</span><span class="sxs-lookup"><span data-stu-id="f30af-107">The following class is declared as `static` and contains only `static` methods:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]  
  
 <span data-ttu-id="f30af-108">Deklaracja stałej lub typu jest niejawnie statycznego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="f30af-108">A constant or type declaration is implicitly a static member.</span></span>  
  
 <span data-ttu-id="f30af-109">Statyczny element członkowski nie można odwoływać się za pomocą wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f30af-109">A static member cannot be referenced through an instance.</span></span> <span data-ttu-id="f30af-110">Zamiast tego odwołuje się do za pomocą nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="f30af-110">Instead, it is referenced through the type name.</span></span> <span data-ttu-id="f30af-111">Rozważmy na przykład następującej klasy:</span><span class="sxs-lookup"><span data-stu-id="f30af-111">For example, consider the following class:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]  
  
 <span data-ttu-id="f30af-112">Aby odwołać się do statycznego elementu członkowskiego `x`, użyj w pełni kwalifikowanej nazwy, `MyBaseC.MyStruct.x`, chyba że jest dostępny z tym samym zakresie:</span><span class="sxs-lookup"><span data-stu-id="f30af-112">To refer to the static member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 <span data-ttu-id="f30af-113">Gdy wystąpienie klasy zawiera osobną kopię wszystkie pola wystąpienia klasy, istnieje tylko jedna kopia każdego pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="f30af-113">While an instance of a class contains a separate copy of all instance fields of the class, there is only one copy of each static field.</span></span>  
  
 <span data-ttu-id="f30af-114">Nie jest możliwe użycie [to](../../../csharp/language-reference/keywords/this.md) do odwołania statycznej metody lub właściwości metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="f30af-114">It is not possible to use [this](../../../csharp/language-reference/keywords/this.md) to reference static methods or property accessors.</span></span>  
  
 <span data-ttu-id="f30af-115">Jeśli `static` — słowo kluczowe jest stosowane do klasy, wszystkie elementy członkowskie klasy musi być statyczna.</span><span class="sxs-lookup"><span data-stu-id="f30af-115">If the `static` keyword is applied to a class, all the members of the class must be static.</span></span>  
  
 <span data-ttu-id="f30af-116">Klasy i klasy statyczne mogą mieć konstruktorów statycznych.</span><span class="sxs-lookup"><span data-stu-id="f30af-116">Classes and static classes may have static constructors.</span></span> <span data-ttu-id="f30af-117">Konstruktory statyczne są nazywane w pewnym momencie między podczas uruchamiania programu i tworzenia wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="f30af-117">Static constructors are called at some point between when the program starts and the class is instantiated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f30af-118">`static` — Słowo kluczowe więcej ma ograniczoną użycia niż w języku C++.</span><span class="sxs-lookup"><span data-stu-id="f30af-118">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="f30af-119">Aby porównać ze słowem kluczowym języka C++, zobacz [klasy magazynu (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="f30af-119">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>
  
 <span data-ttu-id="f30af-120">Aby zademonstrować statycznych elementów członkowskich, należy wziąć pod uwagę klasa, która reprezentuje pracowników firmy.</span><span class="sxs-lookup"><span data-stu-id="f30af-120">To demonstrate static members, consider a class that represents a company employee.</span></span> <span data-ttu-id="f30af-121">Załóżmy, że klasa zawiera metody liczba pracowników i pola do przechowywania liczba pracowników.</span><span class="sxs-lookup"><span data-stu-id="f30af-121">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="f30af-122">Zarówno metoda, jak i pole nie należą do dowolnego wystąpienia pracownika.</span><span class="sxs-lookup"><span data-stu-id="f30af-122">Both the method and the field do not belong to any instance employee.</span></span> <span data-ttu-id="f30af-123">Zamiast tego należą do klasy firmy.</span><span class="sxs-lookup"><span data-stu-id="f30af-123">Instead they belong to the company class.</span></span> <span data-ttu-id="f30af-124">W związku z tym powinny zostać zadeklarowane jako statyczne elementy członkowskie klasy.</span><span class="sxs-lookup"><span data-stu-id="f30af-124">Therefore, they should be declared as static members of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f30af-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="f30af-125">Example</span></span>  
 <span data-ttu-id="f30af-126">W tym przykładzie odczytuje nazwę i identyfikator nowego pracownika, zwiększa licznik pracowników przez jedną i wyświetla informacje o nowych pracowników i nowa liczba pracowników.</span><span class="sxs-lookup"><span data-stu-id="f30af-126">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="f30af-127">Dla uproszczenia ten program odczytuje bieżącą liczbę pracowników z klawiatury.</span><span class="sxs-lookup"><span data-stu-id="f30af-127">For simplicity, this program reads the current number of employees from the keyboard.</span></span> <span data-ttu-id="f30af-128">W rzeczywistej aplikacji należy przeczytać te informacje z pliku.</span><span class="sxs-lookup"><span data-stu-id="f30af-128">In a real application, this information should be read from a file.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="f30af-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="f30af-129">Example</span></span>  
 <span data-ttu-id="f30af-130">Ten przykład przedstawia, że chociaż pola statycznego można zainicjować za pomocą innego pola statycznego niezgłoszonych, wyniki będą Niezdefiniowany dopóki jawnie przypisać wartości do pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="f30af-130">This example shows that although you can initialize a static field by using another static field not yet declared, the results will be undefined until you explicitly assign a value to the static field.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f30af-131">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f30af-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f30af-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f30af-132">See Also</span></span>  
 [<span data-ttu-id="f30af-133">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="f30af-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f30af-134">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f30af-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f30af-135">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="f30af-135">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f30af-136">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="f30af-136">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="f30af-137">Klasy statyczne i statyczni członkowie klas</span><span class="sxs-lookup"><span data-stu-id="f30af-137">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
