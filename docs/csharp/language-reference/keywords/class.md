---
title: Class — słowo C# kluczowe-odwołanie
ms.custom: seodec18
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 0c4fc9645e43f23e340804b46bbe8a5faa19525d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922390"
---
# <a name="class-c-reference"></a><span data-ttu-id="03963-102">class (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="03963-102">class (C# Reference)</span></span>

<span data-ttu-id="03963-103">Klasy są deklarowane za pomocą `class`słowa kluczowego, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="03963-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="03963-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03963-104">Remarks</span></span>

<span data-ttu-id="03963-105">W programie C#można używać tylko jednego dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="03963-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="03963-106">Innymi słowy, Klasa może dziedziczyć implementację tylko z jednej klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="03963-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="03963-107">Jednak Klasa może zaimplementować więcej niż jeden interfejs.</span><span class="sxs-lookup"><span data-stu-id="03963-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="03963-108">W poniższej tabeli przedstawiono przykłady dziedziczenia klas i implementacji interfejsu:</span><span class="sxs-lookup"><span data-stu-id="03963-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="03963-109">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="03963-109">Inheritance</span></span>|<span data-ttu-id="03963-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="03963-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="03963-111">Brak</span><span class="sxs-lookup"><span data-stu-id="03963-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="03963-112">Single</span><span class="sxs-lookup"><span data-stu-id="03963-112">Single</span></span>|`class DerivedClass: BaseClass { }`|
|<span data-ttu-id="03963-113">Brak, implementuje dwa interfejsy</span><span class="sxs-lookup"><span data-stu-id="03963-113">None, implements two interfaces</span></span>|`class ImplClass: IFace1, IFace2 { }`|
|<span data-ttu-id="03963-114">Single, implementuje jeden interfejs</span><span class="sxs-lookup"><span data-stu-id="03963-114">Single, implements one interface</span></span>|`class ImplDerivedClass: BaseClass, IFace1 { }`|

<span data-ttu-id="03963-115">Klasy zadeklarowane bezpośrednio w przestrzeni nazw, a nie zagnieżdżone w innych klasach, mogą być [publiczne](./public.md) lub [wewnętrzne](./internal.md).</span><span class="sxs-lookup"><span data-stu-id="03963-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](./public.md) or [internal](./internal.md).</span></span> <span data-ttu-id="03963-116">Klasy są `internal` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="03963-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="03963-117">Elementy członkowskie klasy, w tym klasy zagnieżdżone, mogą być [publiczne](public.md), [chronione wewnętrznie](protected-internal.md), [chronione](protected.md), [wewnętrzne](internal.md), [prywatne](private.md)i [prywatne](private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="03963-117">Class members, including nested classes, can be [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md), or [private protected](private-protected.md).</span></span> <span data-ttu-id="03963-118">Elementy członkowskie `private` są domyślnie.</span><span class="sxs-lookup"><span data-stu-id="03963-118">Members are `private` by default.</span></span>

<span data-ttu-id="03963-119">Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="03963-119">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="03963-120">Można zadeklarować klasy ogólne z parametrami typu.</span><span class="sxs-lookup"><span data-stu-id="03963-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="03963-121">Aby uzyskać więcej informacji, zobacz [klasy ogólne](../../programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="03963-121">For more information, see [Generic Classes](../../programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="03963-122">Klasa może zawierać deklaracje następujących elementów członkowskich:</span><span class="sxs-lookup"><span data-stu-id="03963-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="03963-123">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="03963-123">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="03963-124">Stałe</span><span class="sxs-lookup"><span data-stu-id="03963-124">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="03963-125">Pola</span><span class="sxs-lookup"><span data-stu-id="03963-125">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="03963-126">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="03963-126">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="03963-127">Metody</span><span class="sxs-lookup"><span data-stu-id="03963-127">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="03963-128">Właściwości</span><span class="sxs-lookup"><span data-stu-id="03963-128">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="03963-129">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="03963-129">Indexers</span></span>](../../programming-guide/indexers/index.md)

- [<span data-ttu-id="03963-130">Operatory</span><span class="sxs-lookup"><span data-stu-id="03963-130">Operators</span></span>](../operators/index.md)

- [<span data-ttu-id="03963-131">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="03963-131">Events</span></span>](../../programming-guide/events/index.md)

- [<span data-ttu-id="03963-132">Delegaty</span><span class="sxs-lookup"><span data-stu-id="03963-132">Delegates</span></span>](../../programming-guide/delegates/index.md)

- [<span data-ttu-id="03963-133">Klasy</span><span class="sxs-lookup"><span data-stu-id="03963-133">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="03963-134">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="03963-134">Interfaces</span></span>](../../programming-guide/interfaces/index.md)

- [<span data-ttu-id="03963-135">Struktury</span><span class="sxs-lookup"><span data-stu-id="03963-135">Structs</span></span>](../../programming-guide/classes-and-structs/structs.md)

- [<span data-ttu-id="03963-136">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="03963-136">Enumerations</span></span>](../../programming-guide/enumeration-types.md)

## <a name="example"></a><span data-ttu-id="03963-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="03963-137">Example</span></span>

<span data-ttu-id="03963-138">Poniższy przykład demonstruje deklarowanie pól klasy, konstruktorów i metod.</span><span class="sxs-lookup"><span data-stu-id="03963-138">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="03963-139">Ilustruje także tworzenie wystąpień obiektów i drukowanie danych wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="03963-139">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="03963-140">W tym przykładzie zadeklarowane są dwie klasy.</span><span class="sxs-lookup"><span data-stu-id="03963-140">In this example, two classes are declared.</span></span> <span data-ttu-id="03963-141">Pierwsza klasa, `Child`, zawiera dwa prywatne pola (`name` i `age`), dwa konstruktory publiczne i jedną metodę publiczną.</span><span class="sxs-lookup"><span data-stu-id="03963-141">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="03963-142">Druga klasa, `StringTest`,,, jest używana do `Main`przechowywania.</span><span class="sxs-lookup"><span data-stu-id="03963-142">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="03963-143">Komentarze</span><span class="sxs-lookup"><span data-stu-id="03963-143">Comments</span></span>

<span data-ttu-id="03963-144">Zwróć uwagę, że w poprzednim przykładzie pola prywatne (`name` i `age`) można uzyskać dostęp tylko za pomocą metody `Child` publicznej klasy.</span><span class="sxs-lookup"><span data-stu-id="03963-144">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="03963-145">Na przykład nie można wydrukować nazwy elementu podrzędnego z `Main` metody przy użyciu instrukcji podobnej do następujących:</span><span class="sxs-lookup"><span data-stu-id="03963-145">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="03963-146">Uzyskiwanie dostępu do `Child` prywatnych `Main` elementów członkowskich z programu byłoby `Main` możliwe tylko wtedy, gdy należały do klasy.</span><span class="sxs-lookup"><span data-stu-id="03963-146">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="03963-147">Typy zadeklarowane wewnątrz klasy bez modyfikatora dostępu domyślnie do `private`, dlatego elementy członkowskie danych w tym przykładzie `private` nadal byłyby, jeśli słowo kluczowe zostało usunięte.</span><span class="sxs-lookup"><span data-stu-id="03963-147">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="03963-148">Na koniec należy zauważyć, że dla obiektu utworzonego przy użyciu konstruktora bez parametrów`child3`() `age` pole zostało domyślnie zainicjowane do zera.</span><span class="sxs-lookup"><span data-stu-id="03963-148">Finally, notice that for the object created using the parameterless constructor (`child3`), the `age` field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="03963-149">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="03963-149">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="03963-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03963-150">See also</span></span>

- [<span data-ttu-id="03963-151">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="03963-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="03963-152">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="03963-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="03963-153">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="03963-153">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="03963-154">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="03963-154">Reference Types</span></span>](./reference-types.md)
