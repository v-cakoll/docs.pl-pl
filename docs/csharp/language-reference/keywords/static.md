---
title: modyfikator statyczny C# -odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: cbd0f6b4ef7976ccc2da2a735ccbba2bf23177e4
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422331"
---
# <a name="static-c-reference"></a><span data-ttu-id="c56e7-102">static (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c56e7-102">static (C# Reference)</span></span>

<span data-ttu-id="c56e7-103">Użyj modyfikatora `static`, aby zadeklarować statyczną składową, która należy do samego typu, a nie do określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="c56e7-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="c56e7-104">Modyfikator `static` może być używany z klasami, polami, metodami, właściwościami, operatorami, zdarzeniami i konstruktorami, ale nie można go używać z indeksatorami, finalizatorami ani typami innymi niż klasy.</span><span class="sxs-lookup"><span data-stu-id="c56e7-104">The `static` modifier can be used with classes, fields, methods, properties, operators, events, and constructors, but it cannot be used with indexers, finalizers, or types other than classes.</span></span> <span data-ttu-id="c56e7-105">Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klas](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="c56e7-105">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="c56e7-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c56e7-106">Example</span></span>

<span data-ttu-id="c56e7-107">Następująca Klasa jest zadeklarowana jako `static` i zawiera tylko metody `static`:</span><span class="sxs-lookup"><span data-stu-id="c56e7-107">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="c56e7-108">Deklaracja stałej lub typu jest niejawnie statycznym elementem członkowskim.</span><span class="sxs-lookup"><span data-stu-id="c56e7-108">A constant or type declaration is implicitly a static member.</span></span>

<span data-ttu-id="c56e7-109">Nie można odwołać się do członka statycznego za pomocą wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c56e7-109">A static member cannot be referenced through an instance.</span></span> <span data-ttu-id="c56e7-110">Zamiast tego odwołuje się do niego za pomocą nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="c56e7-110">Instead, it is referenced through the type name.</span></span> <span data-ttu-id="c56e7-111">Rozważmy na przykład następujące klasy:</span><span class="sxs-lookup"><span data-stu-id="c56e7-111">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="c56e7-112">Aby odwołać się do statycznego elementu członkowskiego `x`, użyj w pełni kwalifikowanej nazwy, `MyBaseC.MyStruct.x`, chyba że element członkowski jest dostępny z tego samego zakresu:</span><span class="sxs-lookup"><span data-stu-id="c56e7-112">To refer to the static member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="c56e7-113">Chociaż wystąpienie klasy zawiera oddzielną kopię wszystkich pól wystąpienia klasy, istnieje tylko jedna kopia każdego pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="c56e7-113">While an instance of a class contains a separate copy of all instance fields of the class, there is only one copy of each static field.</span></span>

<span data-ttu-id="c56e7-114">Nie można użyć [tej](this.md) metody do odwoływania się do metod statycznych lub dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="c56e7-114">It is not possible to use [this](this.md) to reference static methods or property accessors.</span></span>

<span data-ttu-id="c56e7-115">Jeśli `static` słowo kluczowe jest stosowane do klasy, wszystkie elementy członkowskie klasy muszą być statyczne.</span><span class="sxs-lookup"><span data-stu-id="c56e7-115">If the `static` keyword is applied to a class, all the members of the class must be static.</span></span>

<span data-ttu-id="c56e7-116">Klasy i klasy statyczne mogą mieć statyczne konstruktory.</span><span class="sxs-lookup"><span data-stu-id="c56e7-116">Classes and static classes may have static constructors.</span></span> <span data-ttu-id="c56e7-117">Konstruktory statyczne są wywoływane w pewnym momencie od momentu uruchomienia programu i wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="c56e7-117">Static constructors are called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="c56e7-118">Słowo kluczowe `static` ma więcej ograniczonych użycia niż C++w.</span><span class="sxs-lookup"><span data-stu-id="c56e7-118">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="c56e7-119">Aby porównać ze C++ słowem kluczowym, zobacz [klasyC++magazynu ()](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="c56e7-119">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="c56e7-120">Aby przedstawić statyczne elementy członkowskie, należy rozważyć klasę, która reprezentuje pracownika firmy.</span><span class="sxs-lookup"><span data-stu-id="c56e7-120">To demonstrate static members, consider a class that represents a company employee.</span></span> <span data-ttu-id="c56e7-121">Załóżmy, że Klasa zawiera metodę służącą do policzania pracowników i pola do przechowywania liczby pracowników.</span><span class="sxs-lookup"><span data-stu-id="c56e7-121">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="c56e7-122">Obie metody i pola nie należą do żadnego pracownika wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c56e7-122">Both the method and the field do not belong to any instance employee.</span></span> <span data-ttu-id="c56e7-123">Zamiast tego należy do klasy firmy.</span><span class="sxs-lookup"><span data-stu-id="c56e7-123">Instead they belong to the company class.</span></span> <span data-ttu-id="c56e7-124">W związku z tym powinny być deklarowane jako statyczne elementy członkowskie klasy.</span><span class="sxs-lookup"><span data-stu-id="c56e7-124">Therefore, they should be declared as static members of the class.</span></span>

## <a name="example"></a><span data-ttu-id="c56e7-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="c56e7-125">Example</span></span>

<span data-ttu-id="c56e7-126">Ten przykład odczytuje nazwę i identyfikator nowego pracownika, zwiększa licznik pracownika według jednego i wyświetla informacje dotyczące nowego pracownika oraz nową liczbę pracowników.</span><span class="sxs-lookup"><span data-stu-id="c56e7-126">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="c56e7-127">Dla uproszczenia ten program odczytuje bieżącą liczbę pracowników z klawiatury.</span><span class="sxs-lookup"><span data-stu-id="c56e7-127">For simplicity, this program reads the current number of employees from the keyboard.</span></span> <span data-ttu-id="c56e7-128">W prawdziwej aplikacji te informacje powinny być odczytywane z pliku.</span><span class="sxs-lookup"><span data-stu-id="c56e7-128">In a real application, this information should be read from a file.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a><span data-ttu-id="c56e7-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="c56e7-129">Example</span></span>

<span data-ttu-id="c56e7-130">Ten przykład pokazuje, że chociaż można zainicjować pole statyczne przy użyciu innego pola statycznego, które nie zostało jeszcze zadeklarowane, wyniki będą niezdefiniowane do momentu, gdy jawnie przypiszesz wartość do pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="c56e7-130">This example shows that although you can initialize a static field by using another static field not yet declared, the results will be undefined until you explicitly assign a value to the static field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="c56e7-131">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c56e7-131">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c56e7-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c56e7-132">See also</span></span>

- [<span data-ttu-id="c56e7-133">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="c56e7-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c56e7-134">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c56e7-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c56e7-135">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c56e7-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c56e7-136">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="c56e7-136">Modifiers</span></span>](index.md)
- [<span data-ttu-id="c56e7-137">Klasy statyczne i statyczne elementy członkowskie klas</span><span class="sxs-lookup"><span data-stu-id="c56e7-137">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
