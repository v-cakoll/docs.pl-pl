---
title: Class — słowo kluczowe (odwołanie w C#)
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 52ca30fe29025e637005b95ebc14fce8f320e8f4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423942"
---
# <a name="class-c-reference"></a><span data-ttu-id="efde4-102">class (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="efde4-102">class (C# Reference)</span></span>

<span data-ttu-id="efde4-103">Klasy są deklarowane przy użyciu słowa kluczowego `class`, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="efde4-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="efde4-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="efde4-104">Remarks</span></span>

<span data-ttu-id="efde4-105">Tylko pojedyncze dziedziczenie jest dozwolone w języku C#.</span><span class="sxs-lookup"><span data-stu-id="efde4-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="efde4-106">Innymi słowy klasy mogą dziedziczyć implementację tylko jedną klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="efde4-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="efde4-107">Jednak klasa może implementować więcej niż jednego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="efde4-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="efde4-108">W poniższej tabeli przedstawiono przykłady dziedziczenia klas oraz implementacji interfejsu:</span><span class="sxs-lookup"><span data-stu-id="efde4-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="efde4-109">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="efde4-109">Inheritance</span></span>|<span data-ttu-id="efde4-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="efde4-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="efde4-111">Brak</span><span class="sxs-lookup"><span data-stu-id="efde4-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="efde4-112">Single</span><span class="sxs-lookup"><span data-stu-id="efde4-112">Single</span></span>|`class DerivedClass: BaseClass { }`|
|<span data-ttu-id="efde4-113">Brak, implementuje dwa interfejsy</span><span class="sxs-lookup"><span data-stu-id="efde4-113">None, implements two interfaces</span></span>|`class ImplClass: IFace1, IFace2 { }`|
|<span data-ttu-id="efde4-114">Pojedyncze, implementuje jednego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="efde4-114">Single, implements one interface</span></span>|`class ImplDerivedClass: BaseClass, IFace1 { }`|

<span data-ttu-id="efde4-115">Klasy, Zadeklaruj bezpośrednio z poziomu obszaru nazw, nie są zagnieżdżone w innych klas, które mogą być albo [publicznych](../../../csharp/language-reference/keywords/public.md) lub [wewnętrzny](../../../csharp/language-reference/keywords/internal.md).</span><span class="sxs-lookup"><span data-stu-id="efde4-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](../../../csharp/language-reference/keywords/public.md) or [internal](../../../csharp/language-reference/keywords/internal.md).</span></span> <span data-ttu-id="efde4-116">Klasy są `internal` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="efde4-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="efde4-117">Składowych klasy, łącznie z klas zagnieżdżonych, może być [publicznych](../../../csharp/language-reference/keywords/public.md), `protected internal`, [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [prywatnej](../../../csharp/language-reference/keywords/private.md), lub `private protected`.</span><span class="sxs-lookup"><span data-stu-id="efde4-117">Class members, including nested classes, can be [public](../../../csharp/language-reference/keywords/public.md), `protected internal`, [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [private](../../../csharp/language-reference/keywords/private.md), or `private protected`.</span></span> <span data-ttu-id="efde4-118">Elementy członkowskie są [prywatnej](../../../csharp/language-reference/keywords/private.md) domyślnie.</span><span class="sxs-lookup"><span data-stu-id="efde4-118">Members are [private](../../../csharp/language-reference/keywords/private.md) by default.</span></span>

<span data-ttu-id="efde4-119">Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md). </span><span class="sxs-lookup"><span data-stu-id="efde4-119">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="efde4-120">Można zadeklarować klasy ogólne, które mają parametry typu.</span><span class="sxs-lookup"><span data-stu-id="efde4-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="efde4-121">Aby uzyskać więcej informacji, zobacz [klas ogólnych](../../../csharp/programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="efde4-121">For more information, see [Generic Classes](../../../csharp/programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="efde4-122">Klasa może zawierać deklaracje następujące elementy członkowskie:</span><span class="sxs-lookup"><span data-stu-id="efde4-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="efde4-123">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="efde4-123">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="efde4-124">Stałe</span><span class="sxs-lookup"><span data-stu-id="efde4-124">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="efde4-125">Pola</span><span class="sxs-lookup"><span data-stu-id="efde4-125">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="efde4-126">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="efde4-126">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="efde4-127">Metody</span><span class="sxs-lookup"><span data-stu-id="efde4-127">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="efde4-128">Właściwości</span><span class="sxs-lookup"><span data-stu-id="efde4-128">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="efde4-129">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="efde4-129">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)

- [<span data-ttu-id="efde4-130">Operatory</span><span class="sxs-lookup"><span data-stu-id="efde4-130">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)

- [<span data-ttu-id="efde4-131">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="efde4-131">Events</span></span>](../../../csharp/programming-guide/events/index.md)

- [<span data-ttu-id="efde4-132">Delegaci</span><span class="sxs-lookup"><span data-stu-id="efde4-132">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)

- [<span data-ttu-id="efde4-133">Klasy</span><span class="sxs-lookup"><span data-stu-id="efde4-133">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="efde4-134">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="efde4-134">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)

- [<span data-ttu-id="efde4-135">Struktury</span><span class="sxs-lookup"><span data-stu-id="efde4-135">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)

- [<span data-ttu-id="efde4-136">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="efde4-136">Enumerations</span></span>](../../../csharp/programming-guide/enumeration-types.md)

## <a name="example"></a><span data-ttu-id="efde4-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="efde4-137">Example</span></span>

<span data-ttu-id="efde4-138">Poniższy przykład pokazuje deklarującego pola klasy, konstruktory i metody.</span><span class="sxs-lookup"><span data-stu-id="efde4-138">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="efde4-139">Ilustruje też tworzenia wystąpienia obiektu i drukowanie danych wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="efde4-139">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="efde4-140">W tym przykładzie dwie klasy są deklarowane.</span><span class="sxs-lookup"><span data-stu-id="efde4-140">In this example, two classes are declared.</span></span> <span data-ttu-id="efde4-141">Pierwsza klasa `Child`, zawiera dwa pola prywatne (`name` i `age`), dwa konstruktory publiczne i jedną metodę publiczną.</span><span class="sxs-lookup"><span data-stu-id="efde4-141">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="efde4-142">Druga klasa, `StringTest`, będącą `Main`.</span><span class="sxs-lookup"><span data-stu-id="efde4-142">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="efde4-143">Komentarze</span><span class="sxs-lookup"><span data-stu-id="efde4-143">Comments</span></span>

<span data-ttu-id="efde4-144">Należy zauważyć, że w poprzednim przykładzie pola prywatne (`name` i `age`) jest możliwy tylko za pośrednictwem publicznej metody `Child` klasy.</span><span class="sxs-lookup"><span data-stu-id="efde4-144">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="efde4-145">Na przykład nie można drukować nazwy elementu podrzędnego z `Main` metody, przy użyciu instrukcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="efde4-145">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="efde4-146">Uzyskiwanie dostępu do prywatnych składowych `Child` z `Main` byłoby możliwe w tylko jeśli `Main` zostały składową klasy.</span><span class="sxs-lookup"><span data-stu-id="efde4-146">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="efde4-147">Typy zadeklarowane wewnątrz klasy bez domyślnie modyfikator dostępu `private`, więc nadal będzie składowe danych, w tym przykładzie `private` usunięcie słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="efde4-147">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="efde4-148">Na koniec Zwróć uwagę, że dla obiektów utworzonych za pomocą konstruktora domyślnego (`child3`), wiek, pole zostało zainicjowane do zera, domyślnie.</span><span class="sxs-lookup"><span data-stu-id="efde4-148">Finally, notice that for the object created using the default constructor (`child3`), the age field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="efde4-149">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="efde4-149">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="efde4-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efde4-150">See also</span></span>

- [<span data-ttu-id="efde4-151">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="efde4-151">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="efde4-152">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="efde4-152">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="efde4-153">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="efde4-153">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="efde4-154">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="efde4-154">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)
