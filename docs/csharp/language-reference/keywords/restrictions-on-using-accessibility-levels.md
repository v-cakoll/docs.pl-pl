---
title: Ograniczenia dotyczące używania poziomów ułatwień dostępu (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 2bcf2b12d1aa1488e6d3e46f5b37ac9535b138dd
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2018
ms.locfileid: "47058282"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="792a9-102">Ograniczenia dotyczące używania poziomów ułatwień dostępu (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="792a9-102">Restrictions on using accessibility levels (C# Reference)</span></span>

<span data-ttu-id="792a9-103">Po określeniu typu w deklaracji, sprawdź, czy poziom dostępności tego typu jest zależne od poziomu dostępności elementu członkowskiego lub innego typu.</span><span class="sxs-lookup"><span data-stu-id="792a9-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="792a9-104">Na przykład bezpośredniej klasy podstawowej musi być co najmniej tak samo dostępna jak klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="792a9-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="792a9-105">Następujące deklaracje spowodują błąd kompilatora, ponieważ klasa bazowa `BaseClass` jest mniej dostępny niż `MyClass`:</span><span class="sxs-lookup"><span data-stu-id="792a9-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

<span data-ttu-id="792a9-106">W poniższej tabeli podsumowano ograniczenia dotyczące poziomów deklarowana dostępność metody.</span><span class="sxs-lookup"><span data-stu-id="792a9-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>

|<span data-ttu-id="792a9-107">Kontekst</span><span class="sxs-lookup"><span data-stu-id="792a9-107">Context</span></span>|<span data-ttu-id="792a9-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="792a9-108">Remarks</span></span>|
|-------------|-------------|
|[<span data-ttu-id="792a9-109">Klasy</span><span class="sxs-lookup"><span data-stu-id="792a9-109">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="792a9-110">Bezpośrednie klasy bazowej typu klasy musi być co najmniej tak samo dostępna jak samego typu klasy.</span><span class="sxs-lookup"><span data-stu-id="792a9-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|
|[<span data-ttu-id="792a9-111">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="792a9-111">Interfaces</span></span>](../../programming-guide/interfaces/index.md)|<span data-ttu-id="792a9-112">Jawne interfejsy podstawowe typu interfejsu, musi być co najmniej tak samo dostępna jak samego typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="792a9-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|
|[<span data-ttu-id="792a9-113">Delegaci</span><span class="sxs-lookup"><span data-stu-id="792a9-113">Delegates</span></span>](../../programming-guide/delegates/index.md)|<span data-ttu-id="792a9-114">Typ zwracany i typy parametrów typu delegowanego musi być co najmniej tak samo dostępna jak samego typu delegata.</span><span class="sxs-lookup"><span data-stu-id="792a9-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|
|[<span data-ttu-id="792a9-115">Stałe</span><span class="sxs-lookup"><span data-stu-id="792a9-115">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="792a9-116">Typ stałej musi być co najmniej tak samo dostępna jak stała się.</span><span class="sxs-lookup"><span data-stu-id="792a9-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|
|[<span data-ttu-id="792a9-117">Pola</span><span class="sxs-lookup"><span data-stu-id="792a9-117">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="792a9-118">Typ pola musi być co najmniej tak samo dostępna jak samo pole.</span><span class="sxs-lookup"><span data-stu-id="792a9-118">The type of a field must be at least as accessible as the field itself.</span></span>|
|[<span data-ttu-id="792a9-119">Metody</span><span class="sxs-lookup"><span data-stu-id="792a9-119">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="792a9-120">Typ zwracany i typy parametrów metody muszą być co najmniej tak samo dostępna jak sama metoda.</span><span class="sxs-lookup"><span data-stu-id="792a9-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|
|[<span data-ttu-id="792a9-121">Właściwości</span><span class="sxs-lookup"><span data-stu-id="792a9-121">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="792a9-122">Typ właściwości musi być co najmniej tak samo dostępna jak samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="792a9-122">The type of a property must be at least as accessible as the property itself.</span></span>|
|[<span data-ttu-id="792a9-123">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="792a9-123">Events</span></span>](../../programming-guide/events/index.md)|<span data-ttu-id="792a9-124">Typ zdarzenia musi być co najmniej tak samo dostępna jak samego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="792a9-124">The type of an event must be at least as accessible as the event itself.</span></span>|
|[<span data-ttu-id="792a9-125">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="792a9-125">Indexers</span></span>](../../programming-guide/indexers/index.md)|<span data-ttu-id="792a9-126">Typ i parametrów typów indeksatora musi być co najmniej tak samo dostępna jak indeksatora, sam.</span><span class="sxs-lookup"><span data-stu-id="792a9-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|
|[<span data-ttu-id="792a9-127">Operatory</span><span class="sxs-lookup"><span data-stu-id="792a9-127">Operators</span></span>](../../programming-guide/statements-expressions-operators/operators.md)|<span data-ttu-id="792a9-128">Typ zwracany i typy parametrów operatora musi być co najmniej tak samo dostępna jak operator sam.</span><span class="sxs-lookup"><span data-stu-id="792a9-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|
|[<span data-ttu-id="792a9-129">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="792a9-129">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="792a9-130">Typy parametrów konstruktora musi być co najmniej tak samo dostępna jak sam Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="792a9-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|

## <a name="example"></a><span data-ttu-id="792a9-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="792a9-131">Example</span></span>

<span data-ttu-id="792a9-132">Poniższy przykład zawiera błędne deklaracje różnych typów.</span><span class="sxs-lookup"><span data-stu-id="792a9-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="792a9-133">Komentarz po każdym deklaracji wskazuje błąd kompilatora oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="792a9-133">The comment following each declaration indicates the expected compiler error.</span></span>

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

## <a name="c-language-specification"></a><span data-ttu-id="792a9-134">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="792a9-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="792a9-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="792a9-135">See also</span></span>

- [<span data-ttu-id="792a9-136">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="792a9-136">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="792a9-137">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="792a9-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="792a9-138">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="792a9-138">C# Keywords</span></span>](../../language-reference/keywords/index.md)
- [<span data-ttu-id="792a9-139">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="792a9-139">Access Modifiers</span></span>](../../language-reference/keywords/access-modifiers.md)
- [<span data-ttu-id="792a9-140">Domena dostępności</span><span class="sxs-lookup"><span data-stu-id="792a9-140">Accessibility Domain</span></span>](../../language-reference/keywords/accessibility-domain.md)
- [<span data-ttu-id="792a9-141">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="792a9-141">Accessibility Levels</span></span>](../../language-reference/keywords/accessibility-levels.md)
- [<span data-ttu-id="792a9-142">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="792a9-142">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="792a9-143">public</span><span class="sxs-lookup"><span data-stu-id="792a9-143">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="792a9-144">private</span><span class="sxs-lookup"><span data-stu-id="792a9-144">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="792a9-145">protected</span><span class="sxs-lookup"><span data-stu-id="792a9-145">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="792a9-146">internal</span><span class="sxs-lookup"><span data-stu-id="792a9-146">internal</span></span>](../../language-reference/keywords/internal.md)