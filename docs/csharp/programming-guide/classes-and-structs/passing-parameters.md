---
title: Przekazywanie parametrów - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 3e205ecba48df69c0e7f289ad8201765b35d5767
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238146"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="5f138-102">Przekazywanie parametrów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="5f138-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="5f138-103">W języku C# argumenty można przekazać do parametrów, przez wartość lub przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="5f138-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="5f138-104">Przekazywanie poprzez odwołanie włączenie funkcji elementów członkowskich, metody, właściwości, indeksatory, operatory i konstruktory, aby zmienić wartości parametrów i zmiana pozostają w środowiska wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5f138-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="5f138-105">Aby przekazać parametr według odwołania z zamiarem zmiany wartości, należy użyć `ref`, lub `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="5f138-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="5f138-106">Aby Przekaż przez odwołania z celem uniknięcia kopiowania, ale nie zostanie zmieniona wartość, należy użyć `in` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="5f138-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="5f138-107">Dla uproszczenia tylko `ref` — słowo kluczowe jest używana w przykładach w niniejszym temacie.</span><span class="sxs-lookup"><span data-stu-id="5f138-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="5f138-108">Aby uzyskać więcej informacji na temat różnic między `in`, `ref`, i `out`, zobacz [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), i [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="5f138-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), and [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="5f138-109">Poniższy przykład ilustruje różnicę między parametrami wartości i odwołań.</span><span class="sxs-lookup"><span data-stu-id="5f138-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 <span data-ttu-id="5f138-110">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="5f138-110">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="5f138-111">Przekazywanie parametrów typu wartość</span><span class="sxs-lookup"><span data-stu-id="5f138-111">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="5f138-112">Przekazywanie parametrów typu odwołanie</span><span class="sxs-lookup"><span data-stu-id="5f138-112">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="5f138-113">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5f138-113">C# Language Specification</span></span>  

<span data-ttu-id="5f138-114">Aby uzyskać więcej informacji, zobacz [listy argumentów](~/_csharplang/spec/expressions.md#argument-lists) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="5f138-114">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="5f138-115">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="5f138-115">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5f138-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f138-116">See Also</span></span>

- [<span data-ttu-id="5f138-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5f138-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="5f138-118">Metody</span><span class="sxs-lookup"><span data-stu-id="5f138-118">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
