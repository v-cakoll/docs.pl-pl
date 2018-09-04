---
title: static (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: db12ef80752bba913e6792ccb38f598a664efb0b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508288"
---
# <a name="static-c-reference"></a><span data-ttu-id="5fdb2-102">static (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5fdb2-102">static (C# Reference)</span></span>
<span data-ttu-id="5fdb2-103">Użyj `static` modyfikator, aby zadeklarować statyczną składową, która należy do samego typu, a nie do określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="5fdb2-104">`static` Modyfikator mogą być używane z klasy, pola, metody, właściwości, operatory, zdarzenia i konstruktory, ale nie można używać z indeksatorów, finalizatory lub typów innych niż klasy.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-104">The `static` modifier can be used with classes, fields, methods, properties, operators, events, and constructors, but it cannot be used with indexers, finalizers, or types other than classes.</span></span> <span data-ttu-id="5fdb2-105">Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="5fdb2-105">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fdb2-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fdb2-106">Example</span></span>  
 <span data-ttu-id="5fdb2-107">Następujące klasy jest zadeklarowana jako `static` i zawiera tylko `static` metody:</span><span class="sxs-lookup"><span data-stu-id="5fdb2-107">The following class is declared as `static` and contains only `static` methods:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]  
  
 <span data-ttu-id="5fdb2-108">Deklaracja stałej lub typu jest niejawnie statyczny element członkowski.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-108">A constant or type declaration is implicitly a static member.</span></span>  
  
 <span data-ttu-id="5fdb2-109">Statyczny element członkowski nie może być przywoływany przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-109">A static member cannot be referenced through an instance.</span></span> <span data-ttu-id="5fdb2-110">Zamiast tego jest przywoływany przez nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-110">Instead, it is referenced through the type name.</span></span> <span data-ttu-id="5fdb2-111">Na przykład rozważmy następujące klasy:</span><span class="sxs-lookup"><span data-stu-id="5fdb2-111">For example, consider the following class:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]  
  
 <span data-ttu-id="5fdb2-112">Aby odwołać się do statycznej składowej `x`, użyj w pełni kwalifikowanej nazwy `MyBaseC.MyStruct.x`, chyba że składowych jest możliwy z tym samym zakresie:</span><span class="sxs-lookup"><span data-stu-id="5fdb2-112">To refer to the static member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 <span data-ttu-id="5fdb2-113">Chociaż wystąpienia klasy zawiera osobną kopię wszystkie pola wystąpienia klasy, ma tylko jedną kopię każdego pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-113">While an instance of a class contains a separate copy of all instance fields of the class, there is only one copy of each static field.</span></span>  
  
 <span data-ttu-id="5fdb2-114">Nie jest możliwe użycie [to](../../../csharp/language-reference/keywords/this.md) można odwoływać się do metody statyczne lub właściwość metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-114">It is not possible to use [this](../../../csharp/language-reference/keywords/this.md) to reference static methods or property accessors.</span></span>  
  
 <span data-ttu-id="5fdb2-115">Jeśli `static` — słowo kluczowe jest stosowany do klasy, wszystkie elementy członkowskie klasy muszą być statyczne.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-115">If the `static` keyword is applied to a class, all the members of the class must be static.</span></span>  
  
 <span data-ttu-id="5fdb2-116">Klasy i klas statycznych mogą mieć konstruktorów statycznych.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-116">Classes and static classes may have static constructors.</span></span> <span data-ttu-id="5fdb2-117">Konstruktory statyczne są nazywane w pewnym momencie między po uruchomieniu programu i tworzenia wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-117">Static constructors are called at some point between when the program starts and the class is instantiated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fdb2-118">`static` — Słowo kluczowe podlega większym ograniczeniom niż w języku C++.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-118">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="5fdb2-119">Aby porównać ze słowem kluczowym C++, zobacz [klasy magazynu (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="5fdb2-119">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>
  
 <span data-ttu-id="5fdb2-120">Aby zademonstrować statyczne elementy członkowskie, należy wziąć pod uwagę klasa, która reprezentuje pracowników firmy.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-120">To demonstrate static members, consider a class that represents a company employee.</span></span> <span data-ttu-id="5fdb2-121">Załóżmy, że klasa zawiera metodę, aby liczba pracowników i pola, do przechowywania liczby pracowników.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-121">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="5fdb2-122">Pola i metody nie należą do dowolnego wystąpienia pracownika.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-122">Both the method and the field do not belong to any instance employee.</span></span> <span data-ttu-id="5fdb2-123">Zamiast tego należą do klasy firmy.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-123">Instead they belong to the company class.</span></span> <span data-ttu-id="5fdb2-124">W związku z tym powinny zostać zadeklarowane jako statyczne elementy członkowskie klasy.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-124">Therefore, they should be declared as static members of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fdb2-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fdb2-125">Example</span></span>  
 <span data-ttu-id="5fdb2-126">W tym przykładzie odczytuje nazwy i Identyfikatora nowych pracowników, zwiększa licznik pracowników za pomocą jednej i wyświetla informacje o nowych pracowników i liczba nowych pracowników.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-126">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="5fdb2-127">Dla uproszczenia ten program odczytuje bieżąca liczba pracowników przy użyciu klawiatury.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-127">For simplicity, this program reads the current number of employees from the keyboard.</span></span> <span data-ttu-id="5fdb2-128">W rzeczywistej aplikacji należy przeczytać te informacje z pliku.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-128">In a real application, this information should be read from a file.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="5fdb2-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fdb2-129">Example</span></span>  
 <span data-ttu-id="5fdb2-130">Ten przykład pokazuje, że mimo że można zainicjować pole statyczne za pomocą innego pola statyczne niezgłoszonych, wyniki będą niezdefiniowane aż jawnie przypisać wartości do pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="5fdb2-130">This example shows that although you can initialize a static field by using another static field not yet declared, the results will be undefined until you explicitly assign a value to the static field.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="5fdb2-131">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5fdb2-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5fdb2-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5fdb2-132">See Also</span></span>

- [<span data-ttu-id="5fdb2-133">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5fdb2-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="5fdb2-134">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5fdb2-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="5fdb2-135">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="5fdb2-135">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="5fdb2-136">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="5fdb2-136">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="5fdb2-137">Klasy statyczne i statyczne elementy członkowskie klas</span><span class="sxs-lookup"><span data-stu-id="5fdb2-137">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
