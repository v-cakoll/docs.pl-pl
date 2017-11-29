---
title: "params (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e66cfc8e7b131a4443ee227df5e39c7e3b775324
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="params-c-reference"></a><span data-ttu-id="892cd-102">params (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="892cd-102">params (C# Reference)</span></span>
<span data-ttu-id="892cd-103">Za pomocą `params` — słowo kluczowe, można określić [parametru metody](../../../csharp/language-reference/keywords/method-parameters.md) który przyjmuje zmienną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="892cd-103">By using the `params` keyword, you can specify a [method parameter](../../../csharp/language-reference/keywords/method-parameters.md) that takes a variable number of arguments.</span></span>  
  
 <span data-ttu-id="892cd-104">Możesz wysłać rozdzielana przecinkami lista argumentów typu określonego w deklaracji parametru lub tablicę argumentów określonego typu.</span><span class="sxs-lookup"><span data-stu-id="892cd-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="892cd-105">Możesz również wysłać bez argumentów.</span><span class="sxs-lookup"><span data-stu-id="892cd-105">You also can send no arguments.</span></span> <span data-ttu-id="892cd-106">W przypadku wysłania bez argumentów długość `params` listy wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="892cd-106">If you send no arguments, the length of the `params` list is zero.</span></span>  
  
 <span data-ttu-id="892cd-107">Żadne dodatkowe parametry są dozwolone po `params` — słowo kluczowe w deklaracji metody i tylko jeden `params` słowo kluczowe jest dozwolone w deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="892cd-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="892cd-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="892cd-108">Example</span></span>  
 <span data-ttu-id="892cd-109">W poniższym przykładzie pokazano różne sposoby, w których argumenty mogą zostać przesłane do `params` parametru.</span><span class="sxs-lookup"><span data-stu-id="892cd-109">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="892cd-110">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="892cd-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="892cd-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="892cd-111">See Also</span></span>  
 [<span data-ttu-id="892cd-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="892cd-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="892cd-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="892cd-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="892cd-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="892cd-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="892cd-115">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="892cd-115">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
