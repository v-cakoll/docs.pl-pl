---
title: class — słowo kluczowe — odwołanie do języka C#
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 500160d3bc9280b866e5f5ba24c5edc623e752c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673098"
---
# <a name="class-c-reference"></a><span data-ttu-id="54552-102">class (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="54552-102">class (C# Reference)</span></span>

<span data-ttu-id="54552-103">Klasy są deklarowane `class`przy użyciu słowa kluczowego , jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="54552-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="54552-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54552-104">Remarks</span></span>

<span data-ttu-id="54552-105">Tylko pojedyncze dziedziczenie jest dozwolone w języku C#.</span><span class="sxs-lookup"><span data-stu-id="54552-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="54552-106">Innymi słowy klasy można dziedziczyć implementacji tylko z jednej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="54552-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="54552-107">Jednak klasa może zaimplementować więcej niż jeden interfejs.</span><span class="sxs-lookup"><span data-stu-id="54552-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="54552-108">W poniższej tabeli przedstawiono przykłady dziedziczenia klas i implementacji interfejsu:</span><span class="sxs-lookup"><span data-stu-id="54552-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="54552-109">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="54552-109">Inheritance</span></span>|<span data-ttu-id="54552-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="54552-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="54552-111">Brak</span><span class="sxs-lookup"><span data-stu-id="54552-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="54552-112">Single</span><span class="sxs-lookup"><span data-stu-id="54552-112">Single</span></span>|`class DerivedClass : BaseClass { }`|
|<span data-ttu-id="54552-113">Brak, implementuje dwa interfejsy</span><span class="sxs-lookup"><span data-stu-id="54552-113">None, implements two interfaces</span></span>|`class ImplClass : IFace1, IFace2 { }`|
|<span data-ttu-id="54552-114">Pojedynczy, implementuje jeden interfejs</span><span class="sxs-lookup"><span data-stu-id="54552-114">Single, implements one interface</span></span>|`class ImplDerivedClass : BaseClass, IFace1 { }`|

<span data-ttu-id="54552-115">Klasy, które deklarujesz bezpośrednio w obszarze nazw, nie zagnieżdżonych w innych klasach, mogą być [publiczne](./public.md) lub [wewnętrzne.](./internal.md)</span><span class="sxs-lookup"><span data-stu-id="54552-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](./public.md) or [internal](./internal.md).</span></span> <span data-ttu-id="54552-116">Klasy `internal` są domyślnie.</span><span class="sxs-lookup"><span data-stu-id="54552-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="54552-117">Członkowie klasy, w tym klasy zagnieżdżone, mogą być [publiczne,](public.md) [chronione wewnętrzne,](protected-internal.md) [chronione,](protected.md) [wewnętrzne,](internal.md) [prywatne](private.md)lub [prywatne chronione.](private-protected.md)</span><span class="sxs-lookup"><span data-stu-id="54552-117">Class members, including nested classes, can be [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md), or [private protected](private-protected.md).</span></span> <span data-ttu-id="54552-118">Członkowie `private` są domyślnie.</span><span class="sxs-lookup"><span data-stu-id="54552-118">Members are `private` by default.</span></span>

<span data-ttu-id="54552-119">Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="54552-119">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="54552-120">Można zadeklarować klas ogólnych, które mają parametry typu.</span><span class="sxs-lookup"><span data-stu-id="54552-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="54552-121">Aby uzyskać więcej informacji, zobacz [Klasy ogólne](../../programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="54552-121">For more information, see [Generic Classes](../../programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="54552-122">Klasa może zawierać deklaracje następujących elementów członkowskich:</span><span class="sxs-lookup"><span data-stu-id="54552-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="54552-123">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="54552-123">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="54552-124">Stałe</span><span class="sxs-lookup"><span data-stu-id="54552-124">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="54552-125">Pola</span><span class="sxs-lookup"><span data-stu-id="54552-125">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="54552-126">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="54552-126">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="54552-127">Metody</span><span class="sxs-lookup"><span data-stu-id="54552-127">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="54552-128">Właściwości</span><span class="sxs-lookup"><span data-stu-id="54552-128">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)

- <span data-ttu-id="54552-129">[Indexers](../../programming-guide/indexers/index.md) (Indeksatory)</span><span class="sxs-lookup"><span data-stu-id="54552-129">[Indexers](../../programming-guide/indexers/index.md)</span></span>

- [<span data-ttu-id="54552-130">Operatory</span><span class="sxs-lookup"><span data-stu-id="54552-130">Operators</span></span>](../operators/index.md)

- [<span data-ttu-id="54552-131">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="54552-131">Events</span></span>](../../programming-guide/events/index.md)

- [<span data-ttu-id="54552-132">Delegaty</span><span class="sxs-lookup"><span data-stu-id="54552-132">Delegates</span></span>](../../programming-guide/delegates/index.md)

- [<span data-ttu-id="54552-133">Klasy</span><span class="sxs-lookup"><span data-stu-id="54552-133">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="54552-134">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="54552-134">Interfaces</span></span>](../../programming-guide/interfaces/index.md)

- [<span data-ttu-id="54552-135">Typy konstrukcji</span><span class="sxs-lookup"><span data-stu-id="54552-135">Structure types</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="54552-136">Typy wyliczania</span><span class="sxs-lookup"><span data-stu-id="54552-136">Enumeration types</span></span>](../builtin-types/enum.md)

## <a name="example"></a><span data-ttu-id="54552-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="54552-137">Example</span></span>

<span data-ttu-id="54552-138">W poniższym przykładzie przedstawiono deklarowanie pól klas, konstruktorów i metod.</span><span class="sxs-lookup"><span data-stu-id="54552-138">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="54552-139">Pokazuje również wystąpienia obiektów i drukowanie danych wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="54552-139">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="54552-140">W tym przykładzie dwie klasy są zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="54552-140">In this example, two classes are declared.</span></span> <span data-ttu-id="54552-141">Pierwsza klasa `Child`, zawiera dwa`name` pola `age`prywatne ( i ), dwa konstruktory publiczne i jedną metodę publiczną.</span><span class="sxs-lookup"><span data-stu-id="54552-141">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="54552-142">Druga klasa, `StringTest`jest używana `Main`do zawierania .</span><span class="sxs-lookup"><span data-stu-id="54552-142">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="54552-143">Komentarze</span><span class="sxs-lookup"><span data-stu-id="54552-143">Comments</span></span>

<span data-ttu-id="54552-144">Należy zauważyć, że w poprzednim`name` `age`przykładzie pola prywatne ( i ) `Child` są dostępne tylko za pośrednictwem metody publicznej klasy.</span><span class="sxs-lookup"><span data-stu-id="54552-144">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="54552-145">Na przykład nie można wydrukować imienia i `Main` nazwiska dziecka z metody, używając instrukcji w stylu:</span><span class="sxs-lookup"><span data-stu-id="54552-145">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="54552-146">Dostęp do prywatnych `Child` `Main` członków from byłoby możliwe tylko wtedy, `Main` gdy były członkami klasy.</span><span class="sxs-lookup"><span data-stu-id="54552-146">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="54552-147">Typy zadeklarowane wewnątrz klasy bez modyfikatora dostępu domyślnie `private`, `private` więc elementy członkowskie danych w tym przykładzie będzie nadal, jeśli słowo kluczowe zostały usunięte.</span><span class="sxs-lookup"><span data-stu-id="54552-147">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="54552-148">Na koniec należy zauważyć, że dla obiektu utworzonego przy użyciu konstruktora bezparametrów (`child3`), `age` pole zostało zainicjowane domyślnie do zera.</span><span class="sxs-lookup"><span data-stu-id="54552-148">Finally, notice that for the object created using the parameterless constructor (`child3`), the `age` field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="54552-149">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="54552-149">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="54552-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54552-150">See also</span></span>

- [<span data-ttu-id="54552-151">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="54552-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="54552-152">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="54552-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="54552-153">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="54552-153">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="54552-154">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="54552-154">Reference Types</span></span>](./reference-types.md)
