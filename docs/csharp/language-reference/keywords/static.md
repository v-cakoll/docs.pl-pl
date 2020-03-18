---
title: modyfikator statyczny — odwołanie do języka C#
ms.date: 01/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: e7671e9db488a7b50f4ed736864d6fa8d95eef1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76744660"
---
# <a name="static-c-reference"></a><span data-ttu-id="1ed3d-102">static (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1ed3d-102">static (C# Reference)</span></span>

<span data-ttu-id="1ed3d-103">`static` Modyfikator służy do deklarowania statyczny element członkowski, który należy do samego typu, a nie do określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="1ed3d-104">Modyfikator `static` może służyć `static` do deklarowania klas.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-104">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="1ed3d-105">W klasach, interfejsów i struktur, można `static` dodać modyfikator do pól, metody, właściwości, operatory, zdarzenia i konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-105">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="1ed3d-106">Modyfikator `static` nie może być używany z indeksatorów lub finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-106">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="1ed3d-107">Aby uzyskać więcej informacji, zobacz [Klasy statyczne i elementy członkowskie klasy statycznej](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="1ed3d-107">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="1ed3d-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ed3d-108">Example</span></span>

<span data-ttu-id="1ed3d-109">Następująca klasa jest `static` zadeklarowana `static` jako i zawiera tylko metody:</span><span class="sxs-lookup"><span data-stu-id="1ed3d-109">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="1ed3d-110">Deklaracja stała lub typ `static` jest niejawnie element członkowski.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-110">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="1ed3d-111">Nie `static` można odwoływać się do elementu członkowskiego za pośrednictwem wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-111">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="1ed3d-112">Zamiast tego odwołuje się do niego za pomocą nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-112">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="1ed3d-113">Rozważmy na przykład następującą klasę:</span><span class="sxs-lookup"><span data-stu-id="1ed3d-113">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="1ed3d-114">Aby odwołać `static` `x`się do członka, należy `MyBaseC.MyStruct.x`użyć w pełni kwalifikowanej nazwy, chyba że element członkowski jest dostępny z tego samego zakresu:</span><span class="sxs-lookup"><span data-stu-id="1ed3d-114">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="1ed3d-115">Wystąpienie klasy zawiera oddzielną kopię wszystkich pól instancji klasy, istnieje tylko jedna `static` kopia każdego pola.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-115">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="1ed3d-116">Nie jest możliwe użycie [`this`](this.md) do `static` metod odwołania lub akcesorów właściwości.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-116">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="1ed3d-117">Jeśli `static` słowo kluczowe jest stosowane do klasy, wszyscy członkowie `static`klasy muszą być .</span><span class="sxs-lookup"><span data-stu-id="1ed3d-117">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="1ed3d-118">Klasy, interfejsy `static` i klasy `static` mogą mieć konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-118">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="1ed3d-119">Konstruktor `static` jest wywoływana w pewnym momencie między rozpoczęciem programu i klasy jest tworzone.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-119">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="1ed3d-120">Słowo `static` kluczowe ma bardziej ograniczone zastosowania niż w języku C++.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-120">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="1ed3d-121">Aby porównać ze słowem kluczowym C++, zobacz [Klasy magazynu (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="1ed3d-121">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="1ed3d-122">Aby `static` zademonstrować członków, należy wziąć pod uwagę klasę, która reprezentuje pracownika firmy.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-122">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="1ed3d-123">Załóżmy, że klasa zawiera metodę do zliczania pracowników i pole do przechowywania liczby pracowników.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-123">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="1ed3d-124">Zarówno metoda, jak i pole nie należą do żadnego wystąpienia pracownika.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-124">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="1ed3d-125">Zamiast tego należą do całej klasy pracowników.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-125">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="1ed3d-126">Powinny one być `static` zadeklarowane jako członkowie klasy.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-126">They should be declared as `static` members of the class.</span></span>

## <a name="example"></a><span data-ttu-id="1ed3d-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ed3d-127">Example</span></span>

<span data-ttu-id="1ed3d-128">W tym przykładzie odczytuje nazwę i identyfikator nowego pracownika, zwiększa licznik pracownika o jeden i wyświetla informacje dla nowego pracownika i nowej liczby pracowników.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-128">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="1ed3d-129">Ten program odczytuje bieżącą liczbę pracowników z klawiatury.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-129">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a><span data-ttu-id="1ed3d-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ed3d-130">Example</span></span>

<span data-ttu-id="1ed3d-131">W tym przykładzie pokazano, `static` że można `static` zainicjować pole przy użyciu innego pola, które nie zostało jeszcze zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-131">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="1ed3d-132">Wyniki będą niezdefiniowane, dopóki nie zostanie jawnie `static` przypisana wartość do pola.</span><span class="sxs-lookup"><span data-stu-id="1ed3d-132">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="1ed3d-133">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1ed3d-133">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1ed3d-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ed3d-134">See also</span></span>

- [<span data-ttu-id="1ed3d-135">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="1ed3d-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1ed3d-136">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="1ed3d-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1ed3d-137">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="1ed3d-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1ed3d-138">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="1ed3d-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="1ed3d-139">Klasy statyczne i statyczni członkowie klas</span><span class="sxs-lookup"><span data-stu-id="1ed3d-139">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
