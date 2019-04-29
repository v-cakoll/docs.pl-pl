---
title: słowo kluczowe params — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: dd9699eb50f7dffc7c2f4976a79afbf689ba2470
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660986"
---
# <a name="params-c-reference"></a><span data-ttu-id="155ce-102">params (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="155ce-102">params (C# Reference)</span></span>

<span data-ttu-id="155ce-103">Za pomocą `params` — słowo kluczowe, można określić [parametru metody](method-parameters.md) która przyjmuje zmienną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="155ce-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span>

<span data-ttu-id="155ce-104">Możesz wysłać rozdzielana przecinkami lista argumentów o typie określonym w deklaracji parametrów lub tablice argumentów określonego typu.</span><span class="sxs-lookup"><span data-stu-id="155ce-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="155ce-105">Możesz również wysłać bez argumentów.</span><span class="sxs-lookup"><span data-stu-id="155ce-105">You also can send no arguments.</span></span> <span data-ttu-id="155ce-106">Jeśli wyślesz żadnych argumentów, długość `params` listy wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="155ce-106">If you send no arguments, the length of the `params` list is zero.</span></span>

<span data-ttu-id="155ce-107">Żadne dodatkowe parametry są dozwolone po `params` — słowo kluczowe w deklaracji metody i tylko jeden `params` słowo kluczowe jest dozwolone w deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="155ce-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="155ce-108">Deklarowany typ `params` parametr musi być tablicy jednowymiarowej, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="155ce-108">The declared type of the `params` parameter must be a single-dimensional array, as the following example shows.</span></span> <span data-ttu-id="155ce-109">W przeciwnym razie błąd kompilatora [CS0225](../../misc/cs0225.md) występuje.</span><span class="sxs-lookup"><span data-stu-id="155ce-109">Otherwise, a compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

## <a name="example"></a><span data-ttu-id="155ce-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="155ce-110">Example</span></span>

<span data-ttu-id="155ce-111">W poniższym przykładzie pokazano różne sposoby, w których argumenty mogą być wysyłane do `params` parametru.</span><span class="sxs-lookup"><span data-stu-id="155ce-111">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)] 

## <a name="c-language-specification"></a><span data-ttu-id="155ce-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="155ce-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="155ce-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="155ce-113">See also</span></span>

- [<span data-ttu-id="155ce-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="155ce-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="155ce-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="155ce-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="155ce-116">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="155ce-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="155ce-117">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="155ce-117">Method Parameters</span></span>](method-parameters.md)