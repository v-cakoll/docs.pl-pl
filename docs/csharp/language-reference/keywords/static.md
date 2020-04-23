---
title: modyfikator statyczny — odwołanie do języka C#
ms.date: 04/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: 771bcfdac4c4bf27c15da4bc374d804405317a78
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102063"
---
# <a name="static-c-reference"></a><span data-ttu-id="c9129-102">static (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c9129-102">static (C# Reference)</span></span>

<span data-ttu-id="c9129-103">Ta strona `static` zawiera słowo kluczowe modyfikatora.</span><span class="sxs-lookup"><span data-stu-id="c9129-103">This page covers the `static` modifier keyword.</span></span> <span data-ttu-id="c9129-104">Słowo `static` kluczowe jest również [`using static`](using-static.md) częścią dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="c9129-104">The `static` keyword is also part of the [`using static`](using-static.md) directive.</span></span>

<span data-ttu-id="c9129-105">Użyj `static` modyfikatora do deklarowania statycznego elementu członkowskiego, który należy do samego typu, a nie do określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="c9129-105">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="c9129-106">Modyfikator `static` może służyć `static` do deklarowania klas.</span><span class="sxs-lookup"><span data-stu-id="c9129-106">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="c9129-107">W klasach, interfejsach i strukturach można `static` dodać modyfikator do pól, metod, właściwości, operatorów, zdarzeń i konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="c9129-107">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="c9129-108">Modyfikator `static` nie może być używany z indeksatorów lub finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="c9129-108">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="c9129-109">Aby uzyskać więcej informacji, zobacz [Klasy statyczne i Elementy członkowskie klasy statycznej](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="c9129-109">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example---static-class"></a><span data-ttu-id="c9129-110">Przykład - klasa statyczna</span><span class="sxs-lookup"><span data-stu-id="c9129-110">Example - static class</span></span>

<span data-ttu-id="c9129-111">Następująca klasa jest `static` zadeklarowana `static` jako i zawiera tylko metody:</span><span class="sxs-lookup"><span data-stu-id="c9129-111">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="c9129-112">Deklaracja stała lub typ `static` jest niejawnie elementem członkowskim.</span><span class="sxs-lookup"><span data-stu-id="c9129-112">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="c9129-113">Nie `static` można odwoływać się do elementu członkowskiego za pośrednictwem wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c9129-113">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="c9129-114">Zamiast tego odwołuje się do nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="c9129-114">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="c9129-115">Rozważmy na przykład następującą klasę:</span><span class="sxs-lookup"><span data-stu-id="c9129-115">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="c9129-116">Aby odwołać `static` `x`się do elementu członkowskiego, użyj w pełni kwalifikowanej nazwy, `MyBaseC.MyStruct.x`chyba że element członkowski jest dostępny z tego samego zakresu:</span><span class="sxs-lookup"><span data-stu-id="c9129-116">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="c9129-117">Podczas gdy wystąpienie klasy zawiera oddzielną kopię wszystkich pól instancji klasy, istnieje `static` tylko jedna kopia każdego pola.</span><span class="sxs-lookup"><span data-stu-id="c9129-117">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="c9129-118">Nie można użyć [`this`](this.md) do odwoływania się `static` do metod lub akcesorów właściwości.</span><span class="sxs-lookup"><span data-stu-id="c9129-118">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="c9129-119">Jeśli `static` słowo kluczowe jest stosowane do klasy, wszyscy członkowie `static`klasy muszą być .</span><span class="sxs-lookup"><span data-stu-id="c9129-119">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="c9129-120">Klasy, interfejsy `static` i klasy `static` mogą mieć konstruktory.</span><span class="sxs-lookup"><span data-stu-id="c9129-120">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="c9129-121">Konstruktor `static` jest wywoływany w pewnym momencie między uruchomieniem programu i wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="c9129-121">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="c9129-122">Słowo `static` kluczowe ma bardziej ograniczone zastosowania niż w języku C++.</span><span class="sxs-lookup"><span data-stu-id="c9129-122">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="c9129-123">Aby porównać je ze słowem kluczowym C++, zobacz [Klasy magazynu (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="c9129-123">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="c9129-124">Aby `static` zademonstrować członków, należy wziąć pod uwagę klasę, która reprezentuje pracownika firmy.</span><span class="sxs-lookup"><span data-stu-id="c9129-124">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="c9129-125">Załóżmy, że klasa zawiera metodę liczenia pracowników i pole do przechowywania liczby pracowników.</span><span class="sxs-lookup"><span data-stu-id="c9129-125">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="c9129-126">Zarówno metoda, jak i pole nie należą do żadnego wystąpienia pracownika.</span><span class="sxs-lookup"><span data-stu-id="c9129-126">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="c9129-127">Zamiast tego należą do klasy pracowników jako całości.</span><span class="sxs-lookup"><span data-stu-id="c9129-127">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="c9129-128">Powinny one być `static` zadeklarowane jako członkowie klasy.</span><span class="sxs-lookup"><span data-stu-id="c9129-128">They should be declared as `static` members of the class.</span></span>

## <a name="example---static-field-and-method"></a><span data-ttu-id="c9129-129">Przykład — pole statyczne i metoda</span><span class="sxs-lookup"><span data-stu-id="c9129-129">Example - static field and method</span></span>

<span data-ttu-id="c9129-130">W tym przykładzie odczytuje nazwę i identyfikator nowego pracownika, zwiększa licznik pracownika o jeden i wyświetla informacje dla nowego pracownika i nową liczbę pracowników.</span><span class="sxs-lookup"><span data-stu-id="c9129-130">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="c9129-131">Ten program odczytuje bieżącą liczbę pracowników z klawiatury.</span><span class="sxs-lookup"><span data-stu-id="c9129-131">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a><span data-ttu-id="c9129-132">Przykład - inicjowanie statyczne</span><span class="sxs-lookup"><span data-stu-id="c9129-132">Example - static initialization</span></span>

<span data-ttu-id="c9129-133">W tym przykładzie pokazano, `static` że można `static` zainicjować pole przy użyciu innego pola, które nie zostało jeszcze zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="c9129-133">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="c9129-134">Wyniki będą niezdefiniowane, dopóki nie zostanie `static` jawnie przypisana wartość do pola.</span><span class="sxs-lookup"><span data-stu-id="c9129-134">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="c9129-135">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c9129-135">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c9129-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9129-136">See also</span></span>

- [<span data-ttu-id="c9129-137">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="c9129-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c9129-138">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="c9129-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c9129-139">C# Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="c9129-139">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c9129-140">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="c9129-140">Modifiers</span></span>](index.md)
- [<span data-ttu-id="c9129-141">przy użyciu dyrektywy statycznej</span><span class="sxs-lookup"><span data-stu-id="c9129-141">using static directive</span></span>](using-static.md)
- [<span data-ttu-id="c9129-142">Klasy statyczne i statyczni członkowie klas</span><span class="sxs-lookup"><span data-stu-id="c9129-142">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
