---
title: Modyfikator statyczny - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: 90b043fa13f1737db81518151daaeceabf930c5c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239160"
---
# <a name="static-c-reference"></a><span data-ttu-id="5472c-102">static (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5472c-102">static (C# Reference)</span></span>

<span data-ttu-id="5472c-103">Użyj `static` modyfikator, aby zadeklarować statyczną składową, która należy do samego typu, a nie do określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5472c-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="5472c-104">`static` Modyfikator mogą być używane z klasy, pola, metody, właściwości, operatory, zdarzenia i konstruktory, ale nie można używać z indeksatorów, finalizatory lub typów innych niż klasy.</span><span class="sxs-lookup"><span data-stu-id="5472c-104">The `static` modifier can be used with classes, fields, methods, properties, operators, events, and constructors, but it cannot be used with indexers, finalizers, or types other than classes.</span></span> <span data-ttu-id="5472c-105">Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klasy](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="5472c-105">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="5472c-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5472c-106">Example</span></span>

<span data-ttu-id="5472c-107">Następujące klasy jest zadeklarowana jako `static` i zawiera tylko `static` metody:</span><span class="sxs-lookup"><span data-stu-id="5472c-107">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="5472c-108">Deklaracja stałej lub typu jest niejawnie statyczny element członkowski.</span><span class="sxs-lookup"><span data-stu-id="5472c-108">A constant or type declaration is implicitly a static member.</span></span>

<span data-ttu-id="5472c-109">Statyczny element członkowski nie może być przywoływany przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="5472c-109">A static member cannot be referenced through an instance.</span></span> <span data-ttu-id="5472c-110">Zamiast tego jest przywoływany przez nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="5472c-110">Instead, it is referenced through the type name.</span></span> <span data-ttu-id="5472c-111">Na przykład rozważmy następujące klasy:</span><span class="sxs-lookup"><span data-stu-id="5472c-111">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="5472c-112">Aby odwołać się do statycznej składowej `x`, użyj w pełni kwalifikowanej nazwy `MyBaseC.MyStruct.x`, chyba że składowych jest możliwy z tym samym zakresie:</span><span class="sxs-lookup"><span data-stu-id="5472c-112">To refer to the static member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="5472c-113">Chociaż wystąpienia klasy zawiera osobną kopię wszystkie pola wystąpienia klasy, ma tylko jedną kopię każdego pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="5472c-113">While an instance of a class contains a separate copy of all instance fields of the class, there is only one copy of each static field.</span></span>

<span data-ttu-id="5472c-114">Nie jest możliwe użycie [to](this.md) można odwoływać się do metody statyczne lub właściwość metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="5472c-114">It is not possible to use [this](this.md) to reference static methods or property accessors.</span></span>

<span data-ttu-id="5472c-115">Jeśli `static` — słowo kluczowe jest stosowany do klasy, wszystkie elementy członkowskie klasy muszą być statyczne.</span><span class="sxs-lookup"><span data-stu-id="5472c-115">If the `static` keyword is applied to a class, all the members of the class must be static.</span></span>

<span data-ttu-id="5472c-116">Klasy i klas statycznych mogą mieć konstruktorów statycznych.</span><span class="sxs-lookup"><span data-stu-id="5472c-116">Classes and static classes may have static constructors.</span></span> <span data-ttu-id="5472c-117">Konstruktory statyczne są nazywane w pewnym momencie między po uruchomieniu programu i tworzenia wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="5472c-117">Static constructors are called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="5472c-118">`static` — Słowo kluczowe podlega większym ograniczeniom niż w języku C++.</span><span class="sxs-lookup"><span data-stu-id="5472c-118">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="5472c-119">Aby porównać ze słowem kluczowym C++, zobacz [klasy magazynu (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="5472c-119">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="5472c-120">Aby zademonstrować statyczne elementy członkowskie, należy wziąć pod uwagę klasa, która reprezentuje pracowników firmy.</span><span class="sxs-lookup"><span data-stu-id="5472c-120">To demonstrate static members, consider a class that represents a company employee.</span></span> <span data-ttu-id="5472c-121">Załóżmy, że klasa zawiera metodę, aby liczba pracowników i pola, do przechowywania liczby pracowników.</span><span class="sxs-lookup"><span data-stu-id="5472c-121">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="5472c-122">Pola i metody nie należą do dowolnego wystąpienia pracownika.</span><span class="sxs-lookup"><span data-stu-id="5472c-122">Both the method and the field do not belong to any instance employee.</span></span> <span data-ttu-id="5472c-123">Zamiast tego należą do klasy firmy.</span><span class="sxs-lookup"><span data-stu-id="5472c-123">Instead they belong to the company class.</span></span> <span data-ttu-id="5472c-124">W związku z tym powinny zostać zadeklarowane jako statyczne elementy członkowskie klasy.</span><span class="sxs-lookup"><span data-stu-id="5472c-124">Therefore, they should be declared as static members of the class.</span></span>

## <a name="example"></a><span data-ttu-id="5472c-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="5472c-125">Example</span></span>

<span data-ttu-id="5472c-126">W tym przykładzie odczytuje nazwy i Identyfikatora nowych pracowników, zwiększa licznik pracowników za pomocą jednej i wyświetla informacje o nowych pracowników i liczba nowych pracowników.</span><span class="sxs-lookup"><span data-stu-id="5472c-126">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="5472c-127">Dla uproszczenia ten program odczytuje bieżąca liczba pracowników przy użyciu klawiatury.</span><span class="sxs-lookup"><span data-stu-id="5472c-127">For simplicity, this program reads the current number of employees from the keyboard.</span></span> <span data-ttu-id="5472c-128">W rzeczywistej aplikacji należy przeczytać te informacje z pliku.</span><span class="sxs-lookup"><span data-stu-id="5472c-128">In a real application, this information should be read from a file.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a><span data-ttu-id="5472c-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="5472c-129">Example</span></span>

<span data-ttu-id="5472c-130">Ten przykład pokazuje, że mimo że można zainicjować pole statyczne za pomocą innego pola statyczne niezgłoszonych, wyniki będą niezdefiniowane aż jawnie przypisać wartości do pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="5472c-130">This example shows that although you can initialize a static field by using another static field not yet declared, the results will be undefined until you explicitly assign a value to the static field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="5472c-131">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5472c-131">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5472c-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5472c-132">See also</span></span>

- [<span data-ttu-id="5472c-133">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5472c-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5472c-134">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5472c-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5472c-135">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="5472c-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5472c-136">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="5472c-136">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="5472c-137">Klasy statyczne i statyczne elementy członkowskie klas</span><span class="sxs-lookup"><span data-stu-id="5472c-137">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)