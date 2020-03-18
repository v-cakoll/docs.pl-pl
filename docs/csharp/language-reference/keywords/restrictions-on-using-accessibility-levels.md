---
title: Ograniczenia dotyczące korzystania z poziomów ułatwień dostępu — odwołanie do języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 48ab765db7c839ed0dd14df5e6b30f5bd6c0d29b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173539"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="45e63-102">Ograniczenia dotyczące korzystania z poziomów ułatwień dostępu (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="45e63-102">Restrictions on using accessibility levels (C# Reference)</span></span>

<span data-ttu-id="45e63-103">Po określeniu typu w deklaracji, sprawdź, czy poziom ułatwień dostępu typu zależy od poziomu ułatwień dostępu elementu członkowskiego lub innego typu.</span><span class="sxs-lookup"><span data-stu-id="45e63-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="45e63-104">Na przykład klasa podstawowa bezpośrednia musi być co najmniej tak samo dostępna jak klasa pochodna.</span><span class="sxs-lookup"><span data-stu-id="45e63-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="45e63-105">Następujące deklaracje powodują błąd kompilatora, ponieważ klasa `BaseClass` podstawowa jest mniej dostępna niż: `MyClass`</span><span class="sxs-lookup"><span data-stu-id="45e63-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

<span data-ttu-id="45e63-106">W poniższej tabeli podsumowano ograniczenia dotyczące zadeklarowanych poziomów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="45e63-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>

|<span data-ttu-id="45e63-107">Kontekst</span><span class="sxs-lookup"><span data-stu-id="45e63-107">Context</span></span>|<span data-ttu-id="45e63-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45e63-108">Remarks</span></span>|
|-------------|-------------|
|[<span data-ttu-id="45e63-109">Klasy</span><span class="sxs-lookup"><span data-stu-id="45e63-109">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="45e63-110">Bezpośrednia klasa podstawowa typu klasy musi być co najmniej tak samo dostępna jak sam typ klasy.</span><span class="sxs-lookup"><span data-stu-id="45e63-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|
|[<span data-ttu-id="45e63-111">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="45e63-111">Interfaces</span></span>](../../programming-guide/interfaces/index.md)|<span data-ttu-id="45e63-112">Jawne interfejsy podstawowe typu interfejsu muszą być co najmniej tak samo dostępne, jak sam typ interfejsu.</span><span class="sxs-lookup"><span data-stu-id="45e63-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|
|[<span data-ttu-id="45e63-113">Delegaty</span><span class="sxs-lookup"><span data-stu-id="45e63-113">Delegates</span></span>](../../programming-guide/delegates/index.md)|<span data-ttu-id="45e63-114">Typ zwracany i typy parametrów typu delegata muszą być co najmniej tak samo dostępne, jak sam typ delegata.</span><span class="sxs-lookup"><span data-stu-id="45e63-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|
|[<span data-ttu-id="45e63-115">Stałe</span><span class="sxs-lookup"><span data-stu-id="45e63-115">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="45e63-116">Typ stałej musi być co najmniej tak samo dostępny jak sama stała.</span><span class="sxs-lookup"><span data-stu-id="45e63-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|
|[<span data-ttu-id="45e63-117">Pola</span><span class="sxs-lookup"><span data-stu-id="45e63-117">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="45e63-118">Typ pola musi być co najmniej tak samo dostępny jak samo pole.</span><span class="sxs-lookup"><span data-stu-id="45e63-118">The type of a field must be at least as accessible as the field itself.</span></span>|
|[<span data-ttu-id="45e63-119">Metody</span><span class="sxs-lookup"><span data-stu-id="45e63-119">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="45e63-120">Typ zwracany i typy parametrów metody muszą być co najmniej tak samo dostępne jak sama metoda.</span><span class="sxs-lookup"><span data-stu-id="45e63-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|
|[<span data-ttu-id="45e63-121">Właściwości</span><span class="sxs-lookup"><span data-stu-id="45e63-121">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="45e63-122">Typ właściwości musi być co najmniej tak samo dostępny jak sama właściwość.</span><span class="sxs-lookup"><span data-stu-id="45e63-122">The type of a property must be at least as accessible as the property itself.</span></span>|
|[<span data-ttu-id="45e63-123">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="45e63-123">Events</span></span>](../../programming-guide/events/index.md)|<span data-ttu-id="45e63-124">Typ zdarzenia musi być co najmniej tak samo dostępne, jak samo zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="45e63-124">The type of an event must be at least as accessible as the event itself.</span></span>|
|<span data-ttu-id="45e63-125">[Indexers](../../programming-guide/indexers/index.md) (Indeksatory)</span><span class="sxs-lookup"><span data-stu-id="45e63-125">[Indexers](../../programming-guide/indexers/index.md)</span></span>|<span data-ttu-id="45e63-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span><span class="sxs-lookup"><span data-stu-id="45e63-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|
|[<span data-ttu-id="45e63-127">Operatory</span><span class="sxs-lookup"><span data-stu-id="45e63-127">Operators</span></span>](../operators/index.md)|<span data-ttu-id="45e63-128">Typ zwracany i typy parametrów operatora muszą być co najmniej tak samo dostępne jak sam operator.</span><span class="sxs-lookup"><span data-stu-id="45e63-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|
|[<span data-ttu-id="45e63-129">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="45e63-129">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="45e63-130">Typy parametrów konstruktora musi być co najmniej tak samo dostępne jak sam konstruktor.</span><span class="sxs-lookup"><span data-stu-id="45e63-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|

## <a name="example"></a><span data-ttu-id="45e63-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="45e63-131">Example</span></span>

<span data-ttu-id="45e63-132">Poniższy przykład zawiera błędne deklaracje różnych typów.</span><span class="sxs-lookup"><span data-stu-id="45e63-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="45e63-133">Komentarz po każdej deklaracji wskazuje oczekiwany błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="45e63-133">The comment following each declaration indicates the expected compiler error.</span></span>

```csharp
// Restrictions on Using Accessibility Levels
// CS0052 expected as well as CS0053, CS0056, and CS0057
// To make the program work, change access level of both class B
// and MyPrivateMethod() to public.

using System;

// A delegate:
delegate int MyDelegate();

class B
{
    // A private method:
    static int MyPrivateMethod()
    {
        return 0;
    }
}

public class A
{
    // Error: The type B is less accessible than the field A.myField.
    public B myField = new B();

    // Error: The type B is less accessible
    // than the constant A.myConst.
    public readonly B myConst = new B();

    public B MyMethod()
    {
        // Error: The type B is less accessible
        // than the method A.MyMethod.
        return new B();
    }

    // Error: The type B is less accessible than the property A.MyProp
    public B MyProp
    {
        set
        {
        }
    }

    MyDelegate d = new MyDelegate(B.MyPrivateMethod);
    // Even when B is declared public, you still get the error:
    // "The parameter B.MyPrivateMethod is not accessible due to
    // protection level."

    public static B operator +(A m1, B m2)
    {
        // Error: The type B is less accessible
        // than the operator A.operator +(A,B)
        return new B();
    }

    static void Main()
    {
        Console.Write("Compiled successfully");
    }
}
```

## <a name="c-language-specification"></a><span data-ttu-id="45e63-134">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="45e63-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="45e63-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45e63-135">See also</span></span>

- [<span data-ttu-id="45e63-136">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="45e63-136">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="45e63-137">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="45e63-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="45e63-138">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="45e63-138">C# Keywords</span></span>](../../language-reference/keywords/index.md)
- [<span data-ttu-id="45e63-139">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="45e63-139">Access Modifiers</span></span>](../../language-reference/keywords/access-modifiers.md)
- [<span data-ttu-id="45e63-140">Domena dostępności</span><span class="sxs-lookup"><span data-stu-id="45e63-140">Accessibility Domain</span></span>](../../language-reference/keywords/accessibility-domain.md)
- [<span data-ttu-id="45e63-141">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="45e63-141">Accessibility Levels</span></span>](../../language-reference/keywords/accessibility-levels.md)
- [<span data-ttu-id="45e63-142">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="45e63-142">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="45e63-143">Publicznego</span><span class="sxs-lookup"><span data-stu-id="45e63-143">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="45e63-144">Prywatny</span><span class="sxs-lookup"><span data-stu-id="45e63-144">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="45e63-145">protected</span><span class="sxs-lookup"><span data-stu-id="45e63-145">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="45e63-146">Wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="45e63-146">internal</span></span>](../../language-reference/keywords/internal.md)
