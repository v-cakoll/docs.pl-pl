---
title: "Ograniczenia dotyczące używania poziomów ułatwień dostępu (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 44d065429f67d717d7c50e3877294eadd462a99d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="220b6-102">Ograniczenia dotyczące używania poziomów ułatwień dostępu (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="220b6-102">Restrictions on Using Accessibility Levels (C# Reference)</span></span>
<span data-ttu-id="220b6-103">Po określeniu typu w deklaracji, sprawdź, czy poziom dostępności typu zależy od poziomu dostępności elementu członkowskiego lub innego typu.</span><span class="sxs-lookup"><span data-stu-id="220b6-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="220b6-104">Na przykład musi być co najmniej jako dostępne jako klasa pochodna bezpośredniej klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="220b6-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="220b6-105">Następujące deklaracje spowodować błąd kompilatora, ponieważ klasa podstawowa `BaseClass` jest mniej dostępny niż `MyClass`:</span><span class="sxs-lookup"><span data-stu-id="220b6-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>  
  
```  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 <span data-ttu-id="220b6-106">W poniższej tabeli przedstawiono ograniczenia dotyczące poziomów ułatwień dostępu zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="220b6-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>  
  
|<span data-ttu-id="220b6-107">Kontekst</span><span class="sxs-lookup"><span data-stu-id="220b6-107">Context</span></span>|<span data-ttu-id="220b6-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="220b6-108">Remarks</span></span>|  
|-------------|-------------|  
|[<span data-ttu-id="220b6-109">Klasy</span><span class="sxs-lookup"><span data-stu-id="220b6-109">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="220b6-110">Bezpośrednia klasa podstawowa typu klasy musi być co najmniej jako dostępny jako samego typu klasy.</span><span class="sxs-lookup"><span data-stu-id="220b6-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|  
|[<span data-ttu-id="220b6-111">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="220b6-111">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)|<span data-ttu-id="220b6-112">Jawne interfejsy podstawowego typu interfejsu muszą być co najmniej jako dostępne jako samego typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="220b6-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|  
|[<span data-ttu-id="220b6-113">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="220b6-113">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)|<span data-ttu-id="220b6-114">Zwracany typ i typy parametrów typu delegata musi być co najmniej jako dostępny jako sam typ delegata.</span><span class="sxs-lookup"><span data-stu-id="220b6-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|  
|[<span data-ttu-id="220b6-115">Stałe</span><span class="sxs-lookup"><span data-stu-id="220b6-115">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="220b6-116">Typ stałej musi być co najmniej dostępny jako stałej sam.</span><span class="sxs-lookup"><span data-stu-id="220b6-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|  
|[<span data-ttu-id="220b6-117">Pola</span><span class="sxs-lookup"><span data-stu-id="220b6-117">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="220b6-118">Typ pola muszą być co najmniej jako dostępne jako samego pola.</span><span class="sxs-lookup"><span data-stu-id="220b6-118">The type of a field must be at least as accessible as the field itself.</span></span>|  
|[<span data-ttu-id="220b6-119">Metody</span><span class="sxs-lookup"><span data-stu-id="220b6-119">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="220b6-120">Zwracany typ i typy parametrów, metody muszą być co najmniej jako dostępne jako tej metody.</span><span class="sxs-lookup"><span data-stu-id="220b6-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|  
|[<span data-ttu-id="220b6-121">Właściwości</span><span class="sxs-lookup"><span data-stu-id="220b6-121">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="220b6-122">Typ właściwości musi być co najmniej dostępny jako samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="220b6-122">The type of a property must be at least as accessible as the property itself.</span></span>|  
|[<span data-ttu-id="220b6-123">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="220b6-123">Events</span></span>](../../../csharp/programming-guide/events/index.md)|<span data-ttu-id="220b6-124">Typ zdarzenia musi być co najmniej dostępny jako samym zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="220b6-124">The type of an event must be at least as accessible as the event itself.</span></span>|  
|[<span data-ttu-id="220b6-125">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="220b6-125">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)|<span data-ttu-id="220b6-126">Typy typu i parametru indeksatora muszą być co najmniej jako dostępne jako indeksatora samej siebie.</span><span class="sxs-lookup"><span data-stu-id="220b6-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|  
|[<span data-ttu-id="220b6-127">Operatory</span><span class="sxs-lookup"><span data-stu-id="220b6-127">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|<span data-ttu-id="220b6-128">Zwracany typ i typy parametrów operatora musi być co najmniej jako dostępny jako operator samej siebie.</span><span class="sxs-lookup"><span data-stu-id="220b6-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|  
|[<span data-ttu-id="220b6-129">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="220b6-129">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="220b6-130">Typy parametrów konstruktora musi być co najmniej jako dostępny, co konstruktor samej siebie.</span><span class="sxs-lookup"><span data-stu-id="220b6-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="220b6-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="220b6-131">Example</span></span>  
 <span data-ttu-id="220b6-132">Poniższy przykład zawiera błędne deklaracje różnych typów.</span><span class="sxs-lookup"><span data-stu-id="220b6-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="220b6-133">Komentarz po każdej deklaracji wskazuje błąd kompilatora oczekiwanego.</span><span class="sxs-lookup"><span data-stu-id="220b6-133">The comment following each declaration indicates the expected compiler error.</span></span>  
  
```  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="220b6-134">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="220b6-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="220b6-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="220b6-135">See Also</span></span>  
 [<span data-ttu-id="220b6-136">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="220b6-136">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="220b6-137">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="220b6-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="220b6-138">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="220b6-138">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="220b6-139">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="220b6-139">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="220b6-140">Domena dostępności</span><span class="sxs-lookup"><span data-stu-id="220b6-140">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [<span data-ttu-id="220b6-141">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="220b6-141">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="220b6-142">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="220b6-142">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="220b6-143">publiczny</span><span class="sxs-lookup"><span data-stu-id="220b6-143">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="220b6-144">prywatne</span><span class="sxs-lookup"><span data-stu-id="220b6-144">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="220b6-145">chronione</span><span class="sxs-lookup"><span data-stu-id="220b6-145">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="220b6-146">wewnętrzny</span><span class="sxs-lookup"><span data-stu-id="220b6-146">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
