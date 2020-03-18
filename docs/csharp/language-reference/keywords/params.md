---
title: słowo kluczowe params - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: f462ccc2421fef3ea111d263ec035a701cf04775
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173552"
---
# <a name="params-c-reference"></a><span data-ttu-id="5a26b-102">params (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5a26b-102">params (C# Reference)</span></span>

<span data-ttu-id="5a26b-103">Za pomocą `params` słowa kluczowego, można określić [parametr metody,](method-parameters.md) który przyjmuje zmienną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="5a26b-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span>

<span data-ttu-id="5a26b-104">Można wysłać oddzieloną przecinkami listę argumentów typu określonego w deklaracji parametrów lub tablicę argumentów określonego typu.</span><span class="sxs-lookup"><span data-stu-id="5a26b-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="5a26b-105">Można również wysyłać żadnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="5a26b-105">You also can send no arguments.</span></span> <span data-ttu-id="5a26b-106">Jeśli nie wyślesz żadnych `params` argumentów, długość listy wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="5a26b-106">If you send no arguments, the length of the `params` list is zero.</span></span>

<span data-ttu-id="5a26b-107">Żadne dodatkowe parametry nie są `params` dozwolone po słowa kluczowego `params` w deklaracji metody i tylko jedno słowo kluczowe jest dozwolone w deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="5a26b-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="5a26b-108">Zadeklarowany typ `params` parametru musi być tablicą jednowymiarową, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5a26b-108">The declared type of the `params` parameter must be a single-dimensional array, as the following example shows.</span></span> <span data-ttu-id="5a26b-109">W przeciwnym razie wystąpi błąd kompilatora [CS0225.](../../misc/cs0225.md)</span><span class="sxs-lookup"><span data-stu-id="5a26b-109">Otherwise, a compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

## <a name="example"></a><span data-ttu-id="5a26b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="5a26b-110">Example</span></span>

<span data-ttu-id="5a26b-111">W poniższym przykładzie przedstawiono różne sposoby, w `params` których argumenty mogą być wysyłane do parametru.</span><span class="sxs-lookup"><span data-stu-id="5a26b-111">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="5a26b-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5a26b-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5a26b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a26b-113">See also</span></span>

- [<span data-ttu-id="5a26b-114">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="5a26b-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5a26b-115">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="5a26b-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5a26b-116">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="5a26b-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5a26b-117">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="5a26b-117">Method Parameters</span></span>](method-parameters.md)
