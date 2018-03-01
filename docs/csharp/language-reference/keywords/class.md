---
title: "class (odwołanie w C#)"
ms.date: 07/18/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ae4b019ee88b6f331a76c750ab94fc76a3343adb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="class-c-reference"></a><span data-ttu-id="9e4e9-102">class (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9e4e9-102">class (C# Reference)</span></span>

<span data-ttu-id="9e4e9-103">Klasy są zadeklarowane za pomocą słowa kluczowego `class`, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9e4e9-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates 
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="9e4e9-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e4e9-104">Remarks</span></span>
<span data-ttu-id="9e4e9-105">Tylko pojedyncze dziedziczenie jest dozwolone w języku C#.</span><span class="sxs-lookup"><span data-stu-id="9e4e9-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="9e4e9-106">Innymi słowy klasy mogą dziedziczyć implementacji tylko jedną klasę podstawową.</span><span class="sxs-lookup"><span data-stu-id="9e4e9-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="9e4e9-107">Jednak klasy można zaimplementować więcej niż jeden interfejs.</span><span class="sxs-lookup"><span data-stu-id="9e4e9-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="9e4e9-108">W poniższej tabeli przedstawiono przykłady dziedziczenia klas i implementacji interfejsu:</span><span class="sxs-lookup"><span data-stu-id="9e4e9-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="9e4e9-109">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="9e4e9-109">Inheritance</span></span>|<span data-ttu-id="9e4e9-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="9e4e9-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="9e4e9-111">Brak</span><span class="sxs-lookup"><span data-stu-id="9e4e9-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="9e4e9-112">Single</span><span class="sxs-lookup"><span data-stu-id="9e4e9-112">Single</span></span>|`class DerivedClass: BaseClass { }`|
|<span data-ttu-id="9e4e9-113">Brak, implementuje dwa interfejsy</span><span class="sxs-lookup"><span data-stu-id="9e4e9-113">None, implements two interfaces</span></span>|`class ImplClass: IFace1, IFace2 { }`|
|<span data-ttu-id="9e4e9-114">Jeden implementuje jeden interfejs.</span><span class="sxs-lookup"><span data-stu-id="9e4e9-114">Single, implements one interface</span></span>|`class ImplDerivedClass: BaseClass, IFace1 { }`|

<span data-ttu-id="9e4e9-115">Klasy, które deklaruje bezpośrednio z poziomu obszaru nazw, nie są zagnieżdżone w innych klas mogą być [publicznego](../../../csharp/language-reference/keywords/public.md) lub [wewnętrzny](../../../csharp/language-reference/keywords/internal.md).</span><span class="sxs-lookup"><span data-stu-id="9e4e9-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](../../../csharp/language-reference/keywords/public.md) or [internal](../../../csharp/language-reference/keywords/internal.md).</span></span> <span data-ttu-id="9e4e9-116">Występują następujące klasy `internal` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="9e4e9-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="9e4e9-117">Elementów członkowskich klasy, w tym zagnieżdżonych klas, może być [publicznego](../../../csharp/language-reference/keywords/public.md), `protected internal`, [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [prywatnej](../../../csharp/language-reference/keywords/private.md), lub `private protected`.</span><span class="sxs-lookup"><span data-stu-id="9e4e9-117">Class members, including nested classes, can be [public](../../../csharp/language-reference/keywords/public.md), `protected internal`, [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [private](../../../csharp/language-reference/keywords/private.md), or `private protected`.</span></span> <span data-ttu-id="9e4e9-118">Elementy członkowskie są [prywatnej](../../../csharp/language-reference/keywords/private.md) domyślnie.</span><span class="sxs-lookup"><span data-stu-id="9e4e9-118">Members are [private](../../../csharp/language-reference/keywords/private.md) by default.</span></span>

<span data-ttu-id="9e4e9-119">Aby uzyskać więcej informacji, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="9e4e9-119">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="9e4e9-120">Można zadeklarować klas ogólnych, które mają parametry typu.</span><span class="sxs-lookup"><span data-stu-id="9e4e9-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="9e4e9-121">Aby uzyskać więcej informacji, zobacz [klas rodzajowych](../../../csharp/programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="9e4e9-121">For more information, see [Generic Classes](../../../csharp/programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="9e4e9-122">Klasa może zawierać deklaracje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="9e4e9-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="9e4e9-123">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="9e4e9-123">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="9e4e9-124">Stałe</span><span class="sxs-lookup"><span data-stu-id="9e4e9-124">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="9e4e9-125">Pola</span><span class="sxs-lookup"><span data-stu-id="9e4e9-125">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="9e4e9-126">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="9e4e9-126">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="9e4e9-127">Metody</span><span class="sxs-lookup"><span data-stu-id="9e4e9-127">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="9e4e9-128">Właściwości</span><span class="sxs-lookup"><span data-stu-id="9e4e9-128">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="9e4e9-129">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="9e4e9-129">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)

- [<span data-ttu-id="9e4e9-130">Operatory</span><span class="sxs-lookup"><span data-stu-id="9e4e9-130">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)

- [<span data-ttu-id="9e4e9-131">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="9e4e9-131">Events</span></span>](../../../csharp/programming-guide/events/index.md)

- [<span data-ttu-id="9e4e9-132">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="9e4e9-132">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)

- [<span data-ttu-id="9e4e9-133">Klasy</span><span class="sxs-lookup"><span data-stu-id="9e4e9-133">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="9e4e9-134">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="9e4e9-134">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)

- [<span data-ttu-id="9e4e9-135">Struktury</span><span class="sxs-lookup"><span data-stu-id="9e4e9-135">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)

## <a name="example"></a><span data-ttu-id="9e4e9-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="9e4e9-136">Example</span></span>
<span data-ttu-id="9e4e9-137">W poniższym przykładzie pokazano deklarujący pola klasy konstruktory i metody.</span><span class="sxs-lookup"><span data-stu-id="9e4e9-137">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="9e4e9-138">Przedstawiono również podczas tworzenia wystąpienia obiektu i drukowanie danych wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9e4e9-138">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="9e4e9-139">W tym przykładzie są deklarowane jako dwóch klas.</span><span class="sxs-lookup"><span data-stu-id="9e4e9-139">In this example, two classes are declared.</span></span> <span data-ttu-id="9e4e9-140">To pierwsza klasa `Child`, zawiera dwa pola prywatne (`name` i `age`), dwa konstruktory publiczne i jeden publiczny metody.</span><span class="sxs-lookup"><span data-stu-id="9e4e9-140">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="9e4e9-141">Klasa sekundę `StringTest`, zawiera `Main`.</span><span class="sxs-lookup"><span data-stu-id="9e4e9-141">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/class_1.cs)]

## <a name="comments"></a><span data-ttu-id="9e4e9-142">Komentarze</span><span class="sxs-lookup"><span data-stu-id="9e4e9-142">Comments</span></span>
<span data-ttu-id="9e4e9-143">Zwróć uwagę, że w poprzednim przykładzie pól prywatnych (`name` i `age`) jest możliwy tylko za pośrednictwem publicznej metody `Child` klasy.</span><span class="sxs-lookup"><span data-stu-id="9e4e9-143">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="9e4e9-144">Na przykład nazwa tego elementu podrzędnego, nie można drukować z `Main` metodę, przy użyciu instrukcji następująco:</span><span class="sxs-lookup"><span data-stu-id="9e4e9-144">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="9e4e9-145">Uzyskiwanie dostępu do członków prywatnych `Child` z `Main` byłoby możliwe w tylko jeśli `Main` zostały elementu członkowskiego klasy.</span><span class="sxs-lookup"><span data-stu-id="9e4e9-145">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="9e4e9-146">Typy zadeklarowane wewnątrz klasy bez domyślnego modyfikator dostępu do `private`, więc elementy członkowskie danych, w tym przykładzie nadal będzie `private` usunięcie słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="9e4e9-146">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="9e4e9-147">Na koniec należy zauważyć, że dla obiektu, który został utworzony za pomocą konstruktora domyślnego (`child3`), wieku pole zostało zainicjowane do zera domyślnie.</span><span class="sxs-lookup"><span data-stu-id="9e4e9-147">Finally, notice that for the object created using the default constructor (`child3`), the age field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9e4e9-148">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9e4e9-148">C# Language Specification</span></span>
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9e4e9-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e4e9-149">See Also</span></span>
 [<span data-ttu-id="9e4e9-150">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="9e4e9-150">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9e4e9-151">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9e4e9-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9e4e9-152">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9e4e9-152">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9e4e9-153">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="9e4e9-153">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)
