---
title: 'Porady: uzyskiwanie adresu zmiennej (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 63a49490effb8b7d365492e8518b7558ec03a705
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="12bda-102">Porady: uzyskiwanie adresu zmiennej (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="12bda-102">How to: Obtain the Address of a Variable (C# Programming Guide)</span></span>
<span data-ttu-id="12bda-103">Aby uzyskać adres wyrażenie jednoargumentowe, który ocenia do zmiennej stałej, użyj operator address-of `&`:</span><span class="sxs-lookup"><span data-stu-id="12bda-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator `&`:</span></span>  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="12bda-104">Operator address-of można zastosować tylko do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="12bda-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="12bda-105">Jeśli zmienna jest zmienną ruchome, możesz użyć [stałej instrukcji](../../../csharp/language-reference/keywords/fixed-statement.md) tymczasowo naprawić przed uzyskiwanie adresu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="12bda-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="12bda-106">Jest obowiązek upewnij się, że zmienna jest zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="12bda-106">It's your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="12bda-107">Kompilator nie wygeneruje komunikat o błędzie, jeśli zmienna nie jest zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="12bda-107">The compiler doesn't issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="12bda-108">Nie można pobrać adres stała lub wartość.</span><span class="sxs-lookup"><span data-stu-id="12bda-108">You can't get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12bda-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="12bda-109">Example</span></span>  
 <span data-ttu-id="12bda-110">W tym przykładzie wskaźnik do `int`, `p`i przypisanie adresu zmiennej całkowitą `number`.</span><span class="sxs-lookup"><span data-stu-id="12bda-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="12bda-111">Zmienna `number` zainicjowano wyniku przypisanie do `*p`.</span><span class="sxs-lookup"><span data-stu-id="12bda-111">The variable `number` is initialized as a result of the assignment to `*p`.</span></span> <span data-ttu-id="12bda-112">Jeśli możesz przekształcić w komentarz tej instrukcji przypisania, inicjowanie zmiennej `number` zostanie usunięty, ale błąd kompilacji nie jest wystawiany.</span><span class="sxs-lookup"><span data-stu-id="12bda-112">If you comment out this assignment statement, the initialization of the variable `number` is removed, but no compile-time error is issued.</span></span>  

> [!NOTE]
> <span data-ttu-id="12bda-113">W tym przykładzie z kompilacji [ `-unsafe` ](../../language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="12bda-113">Compile this example with the [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="12bda-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12bda-114">See Also</span></span>  
 [<span data-ttu-id="12bda-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="12bda-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="12bda-116">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="12bda-116">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="12bda-117">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="12bda-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="12bda-118">Typy</span><span class="sxs-lookup"><span data-stu-id="12bda-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="12bda-119">unsafe</span><span class="sxs-lookup"><span data-stu-id="12bda-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="12bda-120">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="12bda-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="12bda-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="12bda-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
