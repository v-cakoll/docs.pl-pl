---
title: params (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 692c2f61ae99f1c1c8e04a5a1bcad08814d286fe
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753953"
---
# <a name="params-c-reference"></a><span data-ttu-id="1189a-102">params (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1189a-102">params (C# Reference)</span></span>
<span data-ttu-id="1189a-103">Za pomocą `params` — słowo kluczowe, można określić [parametru metody](../../../csharp/language-reference/keywords/method-parameters.md) która przyjmuje zmienną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="1189a-103">By using the `params` keyword, you can specify a [method parameter](../../../csharp/language-reference/keywords/method-parameters.md) that takes a variable number of arguments.</span></span>  
  
 <span data-ttu-id="1189a-104">Możesz wysłać rozdzielana przecinkami lista argumentów o typie określonym w deklaracji parametrów lub tablice argumentów określonego typu.</span><span class="sxs-lookup"><span data-stu-id="1189a-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="1189a-105">Możesz również wysłać bez argumentów.</span><span class="sxs-lookup"><span data-stu-id="1189a-105">You also can send no arguments.</span></span> <span data-ttu-id="1189a-106">Jeśli wyślesz żadnych argumentów, długość `params` listy wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="1189a-106">If you send no arguments, the length of the `params` list is zero.</span></span>  
  
 <span data-ttu-id="1189a-107">Żadne dodatkowe parametry są dozwolone po `params` — słowo kluczowe w deklaracji metody i tylko jeden `params` słowo kluczowe jest dozwolone w deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="1189a-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>  
 
 <span data-ttu-id="1189a-108">Deklarowany typ `params` parametr musi być tablicy jednowymiarowej, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="1189a-108">The declared type of the `params` parameter must be a single-dimensional array, as the following example shows.</span></span> <span data-ttu-id="1189a-109">W przeciwnym razie błąd kompilatora [CS0225](../../../csharp/misc/cs0225.md) występuje.</span><span class="sxs-lookup"><span data-stu-id="1189a-109">Otherwise, a compiler error [CS0225](../../../csharp/misc/cs0225.md) occurs.</span></span>
  
## <a name="example"></a><span data-ttu-id="1189a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="1189a-110">Example</span></span>  
 <span data-ttu-id="1189a-111">W poniższym przykładzie pokazano różne sposoby, w których argumenty mogą być wysyłane do `params` parametru.</span><span class="sxs-lookup"><span data-stu-id="1189a-111">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1189a-112">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1189a-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1189a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1189a-113">See Also</span></span>  
 [<span data-ttu-id="1189a-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1189a-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1189a-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1189a-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1189a-116">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="1189a-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1189a-117">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="1189a-117">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
