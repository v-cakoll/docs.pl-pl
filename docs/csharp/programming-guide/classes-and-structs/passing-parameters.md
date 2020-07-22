---
title: Przekazywanie parametrów — Przewodnik programowania w języku C#
description: Można przekazać argument do parametru w języku C# według wartości lub odwołania. Zmiany argumentu przesłane przez odwołanie są utrwalane. Użyj ref lub out do przekazywania przez odwołanie.
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 875a42aacf3d7aa4124684aefafdcb07ff4c87d6
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864738"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="a3eac-105">Przekazywanie parametrów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="a3eac-105">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="a3eac-106">W języku C# argumenty mogą być przekazane do parametrów przez wartość lub przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="a3eac-106">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="a3eac-107">Przekazywanie przez odwołanie umożliwia składowe, metody, właściwości, indeksatory, operatory i konstruktory, aby zmienić wartość parametrów i spowodować, że ta zmiana będzie trwała w środowisku wywołującym.</span><span class="sxs-lookup"><span data-stu-id="a3eac-107">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="a3eac-108">Aby przekazać parametr przez odwołanie z intencją zmiany wartości, użyj `ref` `out` słowa kluczowego or.</span><span class="sxs-lookup"><span data-stu-id="a3eac-108">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="a3eac-109">Aby przejść przez odwołanie z intencją uniknięcia kopiowania, ale nie zmiany wartości, użyj `in` modyfikatora.</span><span class="sxs-lookup"><span data-stu-id="a3eac-109">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="a3eac-110">Dla uproszczenia tylko `ref` słowo kluczowe jest używane w przykładach w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="a3eac-110">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="a3eac-111">Aby uzyskać więcej informacji o różnicach między elementami `in` , `ref` , i `out` , zobacz [w](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)i [out](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="a3eac-111">For more information about the difference between `in`, `ref`, and `out`, see [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), and [out](../../language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="a3eac-112">Poniższy przykład ilustruje różnicę między parametrami Value i Reference.</span><span class="sxs-lookup"><span data-stu-id="a3eac-112">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 <span data-ttu-id="a3eac-113">Aby uzyskać więcej informacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="a3eac-113">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="a3eac-114">Przekazywanie parametrów typu wartość</span><span class="sxs-lookup"><span data-stu-id="a3eac-114">Passing Value-Type Parameters</span></span>](./passing-value-type-parameters.md)  
  
- [<span data-ttu-id="a3eac-115">Przekazywanie parametrów typu odwołanie</span><span class="sxs-lookup"><span data-stu-id="a3eac-115">Passing Reference-Type Parameters</span></span>](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="a3eac-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a3eac-116">C# Language Specification</span></span>  

<span data-ttu-id="a3eac-117">Aby uzyskać więcej informacji, zobacz [listy argumentów](~/_csharplang/spec/expressions.md#argument-lists) w [specyfikacji języka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="a3eac-117">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="a3eac-118">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="a3eac-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a3eac-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3eac-119">See also</span></span>

- [<span data-ttu-id="a3eac-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a3eac-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a3eac-121">Metody</span><span class="sxs-lookup"><span data-stu-id="a3eac-121">Methods</span></span>](./methods.md)
