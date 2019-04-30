---
title: 'Porady: uzyskiwanie adresu zmiennej - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: b12d3bf99f32a3526bd4a1ec8c49b1fd88afd68a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61708799"
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="c49d7-102">Porady: uzyskiwanie adresu zmiennej (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="c49d7-102">How to: obtain the address of a variable (C# Programming Guide)</span></span>

<span data-ttu-id="c49d7-103">Aby uzyskać adres wyrażenie jednoargumentowe, co jest ewaluowane jako zmienna ustalona, należy użyć operatora address-of `&`:</span><span class="sxs-lookup"><span data-stu-id="c49d7-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator `&`:</span></span>  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="c49d7-104">Operatora address-of może być tylko zastosowany do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c49d7-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="c49d7-105">Jeśli zmienna jest zmienną ruchome, możesz użyć [stałej instrukcji](../../../csharp/language-reference/keywords/fixed-statement.md) tymczasowo naprawić zmiennej przed uzyskaniem adresu.</span><span class="sxs-lookup"><span data-stu-id="c49d7-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span> <span data-ttu-id="c49d7-106">Aby uzyskać więcej informacji na temat zmiennych ruchome, zobacz [stałe i zmienne ruchome](/dotnet/csharp/language-reference/language-specification/unsafe-code#fixed-and-moveable-variables).</span><span class="sxs-lookup"><span data-stu-id="c49d7-106">For more information about moveable variables, see [Fixed and moveable variables](/dotnet/csharp/language-reference/language-specification/unsafe-code#fixed-and-moveable-variables).</span></span> 
  
 <span data-ttu-id="c49d7-107">Jest odpowiedzialny za zapewnienie, że zmienna jest inicjowana.</span><span class="sxs-lookup"><span data-stu-id="c49d7-107">It's your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="c49d7-108">Kompilator nie wygeneruje komunikat o błędzie, jeśli zmienna nie jest zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="c49d7-108">The compiler doesn't issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="c49d7-109">Nie można pobrać adresu stała lub wartość.</span><span class="sxs-lookup"><span data-stu-id="c49d7-109">You can't get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c49d7-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49d7-110">Example</span></span>  
 <span data-ttu-id="c49d7-111">W tym przykładzie, wskaźnik do `int`, `p`i przypisanie adresu zmienną całkowitoliczbową `number`.</span><span class="sxs-lookup"><span data-stu-id="c49d7-111">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="c49d7-112">Zmienna `number` jest inicjowana w wyniku przypisanie do `*p`.</span><span class="sxs-lookup"><span data-stu-id="c49d7-112">The variable `number` is initialized as a result of the assignment to `*p`.</span></span> <span data-ttu-id="c49d7-113">Jeśli komentarz wystąpi poza tym instrukcja przypisania inicjowania zmiennej `number` zostanie usunięty, ale błąd kompilacji nie jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="c49d7-113">If you comment out this assignment statement, the initialization of the variable `number` is removed, but no compile-time error is issued.</span></span>  

> [!NOTE]
> <span data-ttu-id="c49d7-114">Skompilowania tego przykładu z [ `-unsafe` ](../../language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c49d7-114">Compile this example with the [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="c49d7-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c49d7-115">See also</span></span>

- [<span data-ttu-id="c49d7-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c49d7-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c49d7-117">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="c49d7-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="c49d7-118">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="c49d7-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="c49d7-119">Typy</span><span class="sxs-lookup"><span data-stu-id="c49d7-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="c49d7-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="c49d7-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="c49d7-121">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c49d7-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="c49d7-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="c49d7-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
