---
title: Przekazywanie parametrów — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 60ac7a8d982e7788f07debce114896859385c8e2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705473"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="fcfc7-102">Przekazywanie parametrów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="fcfc7-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="fcfc7-103">W C#programie argumenty mogą być przekazane do parametrów przez wartość lub przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="fcfc7-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="fcfc7-104">Przekazywanie przez odwołanie umożliwia składowe, metody, właściwości, indeksatory, operatory i konstruktory, aby zmienić wartość parametrów i spowodować, że ta zmiana będzie trwała w środowisku wywołującym.</span><span class="sxs-lookup"><span data-stu-id="fcfc7-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="fcfc7-105">Aby przekazać parametr przez odwołanie z intencją zmiany wartości, użyj słowa kluczowego `ref`lub `out`.</span><span class="sxs-lookup"><span data-stu-id="fcfc7-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="fcfc7-106">Aby przejść przez odwołanie z intencją uniknięcia kopiowania, ale nie zmiany wartości, użyj modyfikatora `in`.</span><span class="sxs-lookup"><span data-stu-id="fcfc7-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="fcfc7-107">Dla uproszczenia tylko `ref` słowo kluczowe jest używane w przykładach w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="fcfc7-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="fcfc7-108">Aby uzyskać więcej informacji o różnicach między `in`, `ref`i `out`, zobacz [w](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)i [out](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="fcfc7-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), and [out](../../language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="fcfc7-109">Poniższy przykład ilustruje różnicę między parametrami Value i Reference.</span><span class="sxs-lookup"><span data-stu-id="fcfc7-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 <span data-ttu-id="fcfc7-110">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="fcfc7-110">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="fcfc7-111">Przekazywanie parametrów typu wartość</span><span class="sxs-lookup"><span data-stu-id="fcfc7-111">Passing Value-Type Parameters</span></span>](./passing-value-type-parameters.md)  
  
- [<span data-ttu-id="fcfc7-112">Przekazywanie parametrów typu odwołanie</span><span class="sxs-lookup"><span data-stu-id="fcfc7-112">Passing Reference-Type Parameters</span></span>](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="fcfc7-113">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="fcfc7-113">C# Language Specification</span></span>  

<span data-ttu-id="fcfc7-114">Aby uzyskać więcej informacji, zobacz [listy argumentów](~/_csharplang/spec/expressions.md#argument-lists) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="fcfc7-114">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="fcfc7-115">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="fcfc7-115">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fcfc7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fcfc7-116">See also</span></span>

- [<span data-ttu-id="fcfc7-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fcfc7-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fcfc7-118">Metody</span><span class="sxs-lookup"><span data-stu-id="fcfc7-118">Methods</span></span>](./methods.md)
