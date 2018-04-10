---
title: private (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9cc8f86166888b47a758e200182d319c68ca6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="private-c-reference"></a><span data-ttu-id="682a4-102">private (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="682a4-102">private (C# Reference)</span></span>
<span data-ttu-id="682a4-103">`private` — Słowo kluczowe jest modyfikator dostępu elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="682a4-103">The `private` keyword is a member access modifier.</span></span> 
   
 > <span data-ttu-id="682a4-104">Ta strona zawiera `private` dostępu.</span><span class="sxs-lookup"><span data-stu-id="682a4-104">This page covers `private` access.</span></span> <span data-ttu-id="682a4-105">`private` — Słowo kluczowe jest również częścią [ `private protected` ](./private-protected.md) modyfikator dostępu.</span><span class="sxs-lookup"><span data-stu-id="682a4-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>
  
<span data-ttu-id="682a4-106">Prywatny dostęp jest najbardziej ograniczająca poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="682a4-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="682a4-107">Prywatne elementy członkowskie są dostępne tylko w treści klasy lub struktury, w której zostały zgłoszone, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="682a4-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  

 <span data-ttu-id="682a4-108">Zagnieżdżone typy w tym samym treści można także uzyskać dostęp do tych prywatne elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="682a4-108">Nested types in the same body can also access those private members.</span></span>  
  
 <span data-ttu-id="682a4-109">Jest to błąd kompilacji do odwołania prywatnego elementu członkowskiego spoza klasy lub struktury, w którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="682a4-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>  
  
 <span data-ttu-id="682a4-110">Porównanie `private` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md) i [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="682a4-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="682a4-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="682a4-111">Example</span></span>  
 <span data-ttu-id="682a4-112">W tym przykładzie `Employee` klasa zawiera dwa elementy członkowskie danych prywatnych, `name` i `salary`.</span><span class="sxs-lookup"><span data-stu-id="682a4-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="682a4-113">Jako prywatne elementy członkowskie ich nie są dostępne z wyjątkiem metodami elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="682a4-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="682a4-114">Metody publiczne o nazwie `GetName` i `Salary` są dodawane do dostęp do kontrolowanego prywatne elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="682a4-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="682a4-115">`name` Elementu członkowskiego jest dostępny na publiczną metodę i `salary` elementu członkowskiego jest dostępny i publicznej właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="682a4-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="682a4-116">(Zobacz [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md) Aby uzyskać więcej informacji.)</span><span class="sxs-lookup"><span data-stu-id="682a4-116">(See [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) for more information.)</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="682a4-117">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="682a4-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="682a4-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="682a4-118">See Also</span></span>  
 [<span data-ttu-id="682a4-119">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="682a4-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="682a4-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="682a4-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="682a4-121">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="682a4-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="682a4-122">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="682a4-122">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="682a4-123">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="682a4-123">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="682a4-124">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="682a4-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="682a4-125">publiczny</span><span class="sxs-lookup"><span data-stu-id="682a4-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="682a4-126">chronione</span><span class="sxs-lookup"><span data-stu-id="682a4-126">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="682a4-127">wewnętrzny</span><span class="sxs-lookup"><span data-stu-id="682a4-127">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
