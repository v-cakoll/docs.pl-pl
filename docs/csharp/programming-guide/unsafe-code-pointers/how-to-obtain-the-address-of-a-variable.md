---
title: "Porady: uzyskiwanie adresu zmiennej (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d0969f7e62864c682660f08cd4198aa4032e0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="3b886-102">Porady: uzyskiwanie adresu zmiennej (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="3b886-102">How to: Obtain the Address of a Variable (C# Programming Guide)</span></span>
<span data-ttu-id="3b886-103">Aby uzyskać adres wyrażenie jednoargumentowe, który ocenia do zmiennej stałej, użyj operator address-of:</span><span class="sxs-lookup"><span data-stu-id="3b886-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator:</span></span>  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="3b886-104">Operator address-of można zastosować tylko do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="3b886-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="3b886-105">Jeśli zmienna jest zmienną ruchome, możesz użyć [stałej instrukcji](../../../csharp/language-reference/keywords/fixed-statement.md) tymczasowo naprawić przed uzyskiwanie adresu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="3b886-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="3b886-106">Jest obowiązek upewnij się, że zmienna jest zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="3b886-106">It is your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="3b886-107">Kompilator nie będzie wystawiać komunikat o błędzie, jeśli zmienna nie jest zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="3b886-107">The compiler will not issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="3b886-108">Nie można pobrać adres stała lub wartość.</span><span class="sxs-lookup"><span data-stu-id="3b886-108">You cannot get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b886-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b886-109">Example</span></span>  
 <span data-ttu-id="3b886-110">W tym przykładzie wskaźnik do `int`, `p`i przypisanie adresu zmiennej całkowitą `number`.</span><span class="sxs-lookup"><span data-stu-id="3b886-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="3b886-111">Zmienna `number` zainicjowano wyniku przypisanie do * p.</span><span class="sxs-lookup"><span data-stu-id="3b886-111">The variable `number` is initialized as a result of the assignment to *p.</span></span> <span data-ttu-id="3b886-112">Jeśli wprowadzeniu tej instrukcji przypisania komentarz, inicjowanie zmiennej `number` zostaną usunięte, ale błąd kompilacji nie jest wystawiany.</span><span class="sxs-lookup"><span data-stu-id="3b886-112">If you make this assignment statement a comment, the initialization of the variable `number` will be removed, but no compile-time error is issued.</span></span> <span data-ttu-id="3b886-113">Zwróć uwagę na [dostęp do elementu członkowskiego](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) operator `->` do wyświetlenia adres przechowywanych we wskaźniku.</span><span class="sxs-lookup"><span data-stu-id="3b886-113">Notice the use of the [Member Access](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) operator `->` to obtain and display the address stored in the pointer.</span></span>  
  
 [!code-csharp[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3b886-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b886-114">See Also</span></span>  
 [<span data-ttu-id="3b886-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3b886-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3b886-116">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="3b886-116">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="3b886-117">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="3b886-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="3b886-118">Typy</span><span class="sxs-lookup"><span data-stu-id="3b886-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="3b886-119">unsafe</span><span class="sxs-lookup"><span data-stu-id="3b886-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="3b886-120">Fixed — instrukcja</span><span class="sxs-lookup"><span data-stu-id="3b886-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="3b886-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="3b886-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
