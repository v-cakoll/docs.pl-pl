---
title: modyfikator statyczny C# -odwołanie
ms.date: 01/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: e7671e9db488a7b50f4ed736864d6fa8d95eef1a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744660"
---
# <a name="static-c-reference"></a><span data-ttu-id="1ca72-102">static (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1ca72-102">static (C# Reference)</span></span>

<span data-ttu-id="1ca72-103">Użyj modyfikatora `static`, aby zadeklarować statyczną składową, która należy do samego typu, a nie do określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1ca72-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="1ca72-104">Modyfikator `static` może służyć do deklarowania klas `static`.</span><span class="sxs-lookup"><span data-stu-id="1ca72-104">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="1ca72-105">W klasach, interfejsach i strukturach można dodać modyfikator `static` do pól, metod, właściwości, operatorów, zdarzeń i konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="1ca72-105">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="1ca72-106">Modyfikator `static` nie może być używany z indeksatorami lub finalizatorami.</span><span class="sxs-lookup"><span data-stu-id="1ca72-106">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="1ca72-107">Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klas](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="1ca72-107">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="1ca72-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ca72-108">Example</span></span>

<span data-ttu-id="1ca72-109">Następująca Klasa jest zadeklarowana jako `static` i zawiera tylko metody `static`:</span><span class="sxs-lookup"><span data-stu-id="1ca72-109">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="1ca72-110">Deklaracja stałej lub typu jest niejawnie elementem członkowskim `static`.</span><span class="sxs-lookup"><span data-stu-id="1ca72-110">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="1ca72-111">Nie można odwołać się do elementu członkowskiego `static` za pomocą wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1ca72-111">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="1ca72-112">Zamiast tego jest przywoływany przez nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="1ca72-112">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="1ca72-113">Rozważmy na przykład następujące klasy:</span><span class="sxs-lookup"><span data-stu-id="1ca72-113">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="1ca72-114">Aby odwołać się do `x`składowej `static`, użyj w pełni kwalifikowanej nazwy `MyBaseC.MyStruct.x`, chyba że element członkowski jest dostępny z tego samego zakresu:</span><span class="sxs-lookup"><span data-stu-id="1ca72-114">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="1ca72-115">Chociaż wystąpienie klasy zawiera oddzielną kopię wszystkich pól wystąpienia klasy, istnieje tylko jedna kopia każdego pola `static`.</span><span class="sxs-lookup"><span data-stu-id="1ca72-115">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="1ca72-116">Nie jest możliwe używanie [`this`](this.md) do odwoływania się do `static` metod lub metody dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="1ca72-116">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="1ca72-117">Jeśli `static` słowo kluczowe jest stosowane do klasy, wszystkie elementy członkowskie klasy muszą być `static`.</span><span class="sxs-lookup"><span data-stu-id="1ca72-117">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="1ca72-118">Klasy, interfejsy i klasy `static` mogą mieć `static` konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="1ca72-118">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="1ca72-119">Konstruktor `static` jest wywoływany w pewnym momencie od momentu uruchomienia programu i wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="1ca72-119">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="1ca72-120">Słowo kluczowe `static` ma więcej ograniczonych użycia niż C++w.</span><span class="sxs-lookup"><span data-stu-id="1ca72-120">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="1ca72-121">Aby porównać ze C++ słowem kluczowym, zobacz [klasyC++magazynu ()](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="1ca72-121">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="1ca72-122">Aby wykazać składowe `static`, należy rozważyć klasę, która reprezentuje pracownika firmy.</span><span class="sxs-lookup"><span data-stu-id="1ca72-122">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="1ca72-123">Załóżmy, że Klasa zawiera metodę służącą do policzania pracowników i pola do przechowywania liczby pracowników.</span><span class="sxs-lookup"><span data-stu-id="1ca72-123">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="1ca72-124">Zarówno Metoda, jak i pole nie należy do żadnego wystąpienia jednego pracownika.</span><span class="sxs-lookup"><span data-stu-id="1ca72-124">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="1ca72-125">Zamiast tego należą do klasy pracowników jako całości.</span><span class="sxs-lookup"><span data-stu-id="1ca72-125">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="1ca72-126">Powinny być deklarowane jako `static` składowe klasy.</span><span class="sxs-lookup"><span data-stu-id="1ca72-126">They should be declared as `static` members of the class.</span></span>

## <a name="example"></a><span data-ttu-id="1ca72-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ca72-127">Example</span></span>

<span data-ttu-id="1ca72-128">Ten przykład odczytuje nazwę i identyfikator nowego pracownika, zwiększa licznik pracownika według jednego i wyświetla informacje dotyczące nowego pracownika oraz nową liczbę pracowników.</span><span class="sxs-lookup"><span data-stu-id="1ca72-128">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="1ca72-129">Ten program odczytuje bieżącą liczbę pracowników z klawiatury.</span><span class="sxs-lookup"><span data-stu-id="1ca72-129">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a><span data-ttu-id="1ca72-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ca72-130">Example</span></span>

<span data-ttu-id="1ca72-131">Ten przykład pokazuje, że można zainicjować pole `static` przy użyciu innego pola `static`, które nie zostało jeszcze zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="1ca72-131">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="1ca72-132">Wyniki będą niezdefiniowane, dopóki nie zostanie jawnie przypisana wartość do pola `static`.</span><span class="sxs-lookup"><span data-stu-id="1ca72-132">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="1ca72-133">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1ca72-133">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1ca72-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ca72-134">See also</span></span>

- [<span data-ttu-id="1ca72-135">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="1ca72-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1ca72-136">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1ca72-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1ca72-137">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="1ca72-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1ca72-138">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="1ca72-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="1ca72-139">Klasy statyczne i statyczne elementy członkowskie klas</span><span class="sxs-lookup"><span data-stu-id="1ca72-139">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
