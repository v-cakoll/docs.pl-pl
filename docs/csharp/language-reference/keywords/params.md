---
title: params — słowo C# kluczowe-Reference
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 90d224080f607cbac96514aaf5ac6d67affef9e0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713238"
---
# <a name="params-c-reference"></a><span data-ttu-id="d25d3-102">params (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d25d3-102">params (C# Reference)</span></span>

<span data-ttu-id="d25d3-103">Za pomocą słowa kluczowego `params` można określić [parametr metody](method-parameters.md) , który przyjmuje zmienną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="d25d3-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span>

<span data-ttu-id="d25d3-104">Można wysłać rozdzieloną przecinkami listę argumentów typu określonego w deklaracji parametru lub tablicy argumentów określonego typu.</span><span class="sxs-lookup"><span data-stu-id="d25d3-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="d25d3-105">Nie można również wysyłać żadnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="d25d3-105">You also can send no arguments.</span></span> <span data-ttu-id="d25d3-106">Jeśli nie wyślesz żadnych argumentów, długość listy `params` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="d25d3-106">If you send no arguments, the length of the `params` list is zero.</span></span>

<span data-ttu-id="d25d3-107">Żadne dodatkowe parametry nie są dozwolone po słowie kluczowym `params` w deklaracji metody, a w deklaracji metody dozwolony jest tylko jeden `params` słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d25d3-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="d25d3-108">Zadeklarowany typ parametru `params` musi być tablicą jednowymiarową, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d25d3-108">The declared type of the `params` parameter must be a single-dimensional array, as the following example shows.</span></span> <span data-ttu-id="d25d3-109">W przeciwnym razie wystąpi błąd kompilatora [CS0225](../../misc/cs0225.md) .</span><span class="sxs-lookup"><span data-stu-id="d25d3-109">Otherwise, a compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

## <a name="example"></a><span data-ttu-id="d25d3-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="d25d3-110">Example</span></span>

<span data-ttu-id="d25d3-111">Poniższy przykład ilustruje różne sposoby, w których argumenty mogą być wysyłane do parametru `params`.</span><span class="sxs-lookup"><span data-stu-id="d25d3-111">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)] 

## <a name="c-language-specification"></a><span data-ttu-id="d25d3-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d25d3-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d25d3-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d25d3-113">See also</span></span>

- [<span data-ttu-id="d25d3-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d25d3-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d25d3-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d25d3-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d25d3-116">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="d25d3-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d25d3-117">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="d25d3-117">Method Parameters</span></span>](method-parameters.md)
