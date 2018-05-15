---
title: Ograniczenia dotyczące używania poziomów ułatwień dostępu (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: bbe358822e885e5ddaba4cb9d982e89cefe1921e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="e1657-102">Ograniczenia dotyczące używania poziomów ułatwień dostępu (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="e1657-102">Restrictions on Using Accessibility Levels (C# Reference)</span></span>
<span data-ttu-id="e1657-103">Po określeniu typu w deklaracji, sprawdź, czy poziom dostępności typu zależy od poziomu dostępności elementu członkowskiego lub innego typu.</span><span class="sxs-lookup"><span data-stu-id="e1657-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="e1657-104">Na przykład musi być co najmniej jako dostępne jako klasa pochodna bezpośredniej klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="e1657-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="e1657-105">Następujące deklaracje spowodować błąd kompilatora, ponieważ klasa podstawowa `BaseClass` jest mniej dostępny niż `MyClass`:</span><span class="sxs-lookup"><span data-stu-id="e1657-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>  
  
```  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 <span data-ttu-id="e1657-106">W poniższej tabeli przedstawiono ograniczenia dotyczące poziomów ułatwień dostępu zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="e1657-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>  
  
|<span data-ttu-id="e1657-107">Kontekst</span><span class="sxs-lookup"><span data-stu-id="e1657-107">Context</span></span>|<span data-ttu-id="e1657-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1657-108">Remarks</span></span>|  
|-------------|-------------|  
|[<span data-ttu-id="e1657-109">Klasy</span><span class="sxs-lookup"><span data-stu-id="e1657-109">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="e1657-110">Bezpośrednia klasa podstawowa typu klasy musi być co najmniej jako dostępny jako samego typu klasy.</span><span class="sxs-lookup"><span data-stu-id="e1657-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|  
|[<span data-ttu-id="e1657-111">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="e1657-111">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)|<span data-ttu-id="e1657-112">Jawne interfejsy podstawowego typu interfejsu muszą być co najmniej jako dostępne jako samego typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e1657-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|  
|[<span data-ttu-id="e1657-113">Delegaci</span><span class="sxs-lookup"><span data-stu-id="e1657-113">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)|<span data-ttu-id="e1657-114">Zwracany typ i typy parametrów typu delegata musi być co najmniej jako dostępny jako sam typ delegata.</span><span class="sxs-lookup"><span data-stu-id="e1657-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|  
|[<span data-ttu-id="e1657-115">Stałe</span><span class="sxs-lookup"><span data-stu-id="e1657-115">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="e1657-116">Typ stałej musi być co najmniej dostępny jako stałej sam.</span><span class="sxs-lookup"><span data-stu-id="e1657-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|  
|[<span data-ttu-id="e1657-117">Pola</span><span class="sxs-lookup"><span data-stu-id="e1657-117">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="e1657-118">Typ pola muszą być co najmniej jako dostępne jako samego pola.</span><span class="sxs-lookup"><span data-stu-id="e1657-118">The type of a field must be at least as accessible as the field itself.</span></span>|  
|[<span data-ttu-id="e1657-119">Metody</span><span class="sxs-lookup"><span data-stu-id="e1657-119">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="e1657-120">Zwracany typ i typy parametrów, metody muszą być co najmniej jako dostępne jako tej metody.</span><span class="sxs-lookup"><span data-stu-id="e1657-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|  
|[<span data-ttu-id="e1657-121">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e1657-121">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="e1657-122">Typ właściwości musi być co najmniej dostępny jako samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="e1657-122">The type of a property must be at least as accessible as the property itself.</span></span>|  
|[<span data-ttu-id="e1657-123">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e1657-123">Events</span></span>](../../../csharp/programming-guide/events/index.md)|<span data-ttu-id="e1657-124">Typ zdarzenia musi być co najmniej dostępny jako samym zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="e1657-124">The type of an event must be at least as accessible as the event itself.</span></span>|  
|[<span data-ttu-id="e1657-125">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="e1657-125">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)|<span data-ttu-id="e1657-126">Typy typu i parametru indeksatora muszą być co najmniej jako dostępne jako indeksatora samej siebie.</span><span class="sxs-lookup"><span data-stu-id="e1657-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|  
|[<span data-ttu-id="e1657-127">Operatory</span><span class="sxs-lookup"><span data-stu-id="e1657-127">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|<span data-ttu-id="e1657-128">Zwracany typ i typy parametrów operatora musi być co najmniej jako dostępny jako operator samej siebie.</span><span class="sxs-lookup"><span data-stu-id="e1657-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|  
|[<span data-ttu-id="e1657-129">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="e1657-129">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="e1657-130">Typy parametrów konstruktora musi być co najmniej jako dostępny, co konstruktor samej siebie.</span><span class="sxs-lookup"><span data-stu-id="e1657-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e1657-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1657-131">Example</span></span>  
 <span data-ttu-id="e1657-132">Poniższy przykład zawiera błędne deklaracje różnych typów.</span><span class="sxs-lookup"><span data-stu-id="e1657-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="e1657-133">Komentarz po każdej deklaracji wskazuje błąd kompilatora oczekiwanego.</span><span class="sxs-lookup"><span data-stu-id="e1657-133">The comment following each declaration indicates the expected compiler error.</span></span>  
  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="e1657-134">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e1657-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e1657-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1657-135">See Also</span></span>  
 [<span data-ttu-id="e1657-136">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="e1657-136">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e1657-137">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e1657-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e1657-138">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="e1657-138">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e1657-139">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="e1657-139">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="e1657-140">Domena dostępności</span><span class="sxs-lookup"><span data-stu-id="e1657-140">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [<span data-ttu-id="e1657-141">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="e1657-141">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="e1657-142">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="e1657-142">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="e1657-143">public</span><span class="sxs-lookup"><span data-stu-id="e1657-143">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="e1657-144">private</span><span class="sxs-lookup"><span data-stu-id="e1657-144">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="e1657-145">protected</span><span class="sxs-lookup"><span data-stu-id="e1657-145">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="e1657-146">internal</span><span class="sxs-lookup"><span data-stu-id="e1657-146">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
