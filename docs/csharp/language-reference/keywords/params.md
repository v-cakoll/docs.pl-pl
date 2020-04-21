---
title: params — słowo kluczowe dla tablic parametrów — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 77d7fd19ff57f80f401191027e2fae95026e1966
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738842"
---
# <a name="params-c-reference"></a><span data-ttu-id="c20a5-102">params (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c20a5-102">params (C# Reference)</span></span>

<span data-ttu-id="c20a5-103">Za pomocą `params` słowa kluczowego można określić [parametr metody,](method-parameters.md) który przyjmuje zmienną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="c20a5-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span> <span data-ttu-id="c20a5-104">Typ parametru musi być tablicą jednowymiarową.</span><span class="sxs-lookup"><span data-stu-id="c20a5-104">The parameter type must be a single-dimensional array.</span></span>

<span data-ttu-id="c20a5-105">Żadne dodatkowe parametry są `params` dozwolone po słowie kluczowym `params` w deklaracji metody i tylko jedno słowo kluczowe jest dozwolone w deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="c20a5-105">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="c20a5-106">Jeśli zadeklarowany typ `params` parametru nie jest tablicą jednowymiarową, występuje błąd kompilatora [CS0225.](../../misc/cs0225.md)</span><span class="sxs-lookup"><span data-stu-id="c20a5-106">If the declared type of the `params` parameter is not a single-dimensional array, compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

<span data-ttu-id="c20a5-107">Po wywołaniu metody `params` z parametrem można przekazać:</span><span class="sxs-lookup"><span data-stu-id="c20a5-107">When you call a method with a `params` parameter, you can pass in:</span></span>

- <span data-ttu-id="c20a5-108">Oddzielona przecinkami lista argumentów typu elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="c20a5-108">A comma-separated list of arguments of the type of the array elements.</span></span>
- <span data-ttu-id="c20a5-109">Tablica argumentów określonego typu.</span><span class="sxs-lookup"><span data-stu-id="c20a5-109">An array of arguments of the specified type.</span></span>
- <span data-ttu-id="c20a5-110">Brak argumentów.</span><span class="sxs-lookup"><span data-stu-id="c20a5-110">No arguments.</span></span> <span data-ttu-id="c20a5-111">Jeśli nie wyślesz żadnych argumentów, długość `params` listy wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="c20a5-111">If you send no arguments, the length of the `params` list is zero.</span></span>

## <a name="example"></a><span data-ttu-id="c20a5-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="c20a5-112">Example</span></span>

<span data-ttu-id="c20a5-113">W poniższym przykładzie przedstawiono różne sposoby, w jaki argumenty mogą być wysyłane do parametru. `params`</span><span class="sxs-lookup"><span data-stu-id="c20a5-113">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="c20a5-114">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c20a5-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c20a5-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c20a5-115">See also</span></span>

- [<span data-ttu-id="c20a5-116">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="c20a5-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c20a5-117">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="c20a5-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c20a5-118">C# Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="c20a5-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c20a5-119">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="c20a5-119">Method Parameters</span></span>](method-parameters.md)
