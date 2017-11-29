---
title: "Przekazywanie parametrów (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9e0e06d67f9da39c6b55f91e35d4a75b43353f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="f0459-102">Przekazywanie parametrów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="f0459-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="f0459-103">W języku C# argumenty mogą być przekazywane do parametrów według wartości lub według odwołania.</span><span class="sxs-lookup"><span data-stu-id="f0459-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="f0459-104">Przekazywanie poprzez odwołanie umożliwia członkom funkcji, metody, właściwości, indeksatorów, operatory, a konstruktorów może zmienić wartości parametrów, a zmiana pozostają w środowisku wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f0459-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="f0459-105">Aby przekazać parametr przez odwołanie, użyj `ref` lub `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="f0459-105">To pass a parameter by reference, use the `ref` or `out` keyword.</span></span> <span data-ttu-id="f0459-106">Dla uproszczenia tylko `ref` — słowo kluczowe jest używany w przykładach w niniejszym temacie.</span><span class="sxs-lookup"><span data-stu-id="f0459-106">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="f0459-107">Aby uzyskać więcej informacji na temat różnic między `ref` i `out`, zobacz [ref](../../../csharp/language-reference/keywords/ref.md), [limit](../../../csharp/language-reference/keywords/out.md), i [przekazywanie tablic za pomocą ref i out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="f0459-107">For more information about the difference between `ref` and `out`, see [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out.md), and [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="f0459-108">Poniższy przykład przedstawia różnicę między odwołanie i wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="f0459-108">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 <span data-ttu-id="f0459-109">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="f0459-109">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="f0459-110">Przekazywanie parametrów typu wartość</span><span class="sxs-lookup"><span data-stu-id="f0459-110">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="f0459-111">Przekazywanie parametrów typu odwołanie</span><span class="sxs-lookup"><span data-stu-id="f0459-111">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="f0459-112">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f0459-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f0459-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0459-113">See Also</span></span>  
 [<span data-ttu-id="f0459-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f0459-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f0459-115">Metody</span><span class="sxs-lookup"><span data-stu-id="f0459-115">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
