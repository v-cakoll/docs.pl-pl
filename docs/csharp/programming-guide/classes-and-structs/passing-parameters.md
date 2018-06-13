---
title: Przekazywanie parametrów (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: a1ccfff8081d101eee46360009653b0591dfb3ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323108"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="9bc19-102">Przekazywanie parametrów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="9bc19-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="9bc19-103">W języku C# argumenty mogą być przekazywane do parametrów według wartości lub według odwołania.</span><span class="sxs-lookup"><span data-stu-id="9bc19-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="9bc19-104">Przekazywanie poprzez odwołanie umożliwia członkom funkcji, metody, właściwości, indeksatorów, operatory, a konstruktorów może zmienić wartości parametrów, a zmiana pozostają w środowisku wywołującego.</span><span class="sxs-lookup"><span data-stu-id="9bc19-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="9bc19-105">Aby przekazać parametr przez odwołanie z zamiarem zmiany wartości, należy użyć `ref`, lub `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="9bc19-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="9bc19-106">Aby przekazać przez odwołanie z zamiarem unikając kopiowania, ale nie zmienia się wartość, użyj `in` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="9bc19-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="9bc19-107">Dla uproszczenia tylko `ref` — słowo kluczowe jest używany w przykładach w niniejszym temacie.</span><span class="sxs-lookup"><span data-stu-id="9bc19-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="9bc19-108">Aby uzyskać więcej informacji na temat różnic między `in`, `ref`, i `out`, zobacz [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), [limit](../../../csharp/language-reference/keywords/out-parameter-modifier.md), i [ Przekazywanie tablic za pomocą ref i out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="9bc19-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), and [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="9bc19-109">Poniższy przykład przedstawia różnicę między odwołanie i wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="9bc19-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 <span data-ttu-id="9bc19-110">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="9bc19-110">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="9bc19-111">Przekazywanie parametrów typu wartość</span><span class="sxs-lookup"><span data-stu-id="9bc19-111">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="9bc19-112">Przekazywanie parametrów typu odwołanie</span><span class="sxs-lookup"><span data-stu-id="9bc19-112">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="9bc19-113">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9bc19-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9bc19-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9bc19-114">See Also</span></span>  
 [<span data-ttu-id="9bc19-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9bc19-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9bc19-116">Metody</span><span class="sxs-lookup"><span data-stu-id="9bc19-116">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
