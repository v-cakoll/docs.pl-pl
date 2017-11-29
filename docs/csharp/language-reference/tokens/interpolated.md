---
title: "$ (Odwołanie w C#)"
ms.date: 02/09/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
ms.assetid: 7d9e21b5-eac3-4878-9530-50e4da578acd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d245bab063721abdb930aae113aab2094553b9bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-c-reference"></a><span data-ttu-id="50cb5-102">$ (Odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="50cb5-102">$ (C# Reference)</span></span>

<span data-ttu-id="50cb5-103">Określa ciąg literału jako [interpolowane ciąg](../keywords/interpolated-strings.md).</span><span class="sxs-lookup"><span data-stu-id="50cb5-103">Identifies a string literal as an [interpolated string](../keywords/interpolated-strings.md).</span></span> <span data-ttu-id="50cb5-104">Ciąg typu szablonu, który zawiera literały tekstowe wraz z programem jest ciągu interpolowanym *interpolowane wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="50cb5-104">An interpolated string is a template-like string that contains literal text along with *interpolated expressions*.</span></span> <span data-ttu-id="50cb5-105">Po usunięciu ciągu interpolowanym, na przykład w instrukcji przypisania lub wywołanie metody jego interpolowanego wyrażenia zastępuje ich reprezentacji ciągu w ciągu wynik.</span><span class="sxs-lookup"><span data-stu-id="50cb5-105">When the interpolated string is resolved, for example in an assignment statement or a method call, its interpolated expressions are replaced by their string representations in the result string.</span></span> <span data-ttu-id="50cb5-106">Ciągi interpolowane są elementy zastępcze [ciągi formatujące złożonego](../../../standard/base-types/composite-format.md) obsługiwane przez program .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50cb5-106">Interpolated strings are replacements for the [composite format strings](../../../standard/base-types/composite-format.md) supported by the .NET Framework.</span></span>

<span data-ttu-id="50cb5-107">W poniższym przykładzie użyto `$` znaków do definiowania ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="50cb5-107">The following example uses the `$` character to define an interpolated string.</span></span>

[!code-csharp[interpolated-string-symbol](../../../../samples/snippets/csharp/language-reference/keywords/dollar-sign1.cs#1)]

<span data-ttu-id="50cb5-108">Aby uzyskać więcej informacji dotyczących ciągi interpolowane, zobacz [ciągi interpolowane](../keywords/interpolated-strings.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="50cb5-108">For more information on interpolated strings, see the [Interpolated Strings](../keywords/interpolated-strings.md) topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="50cb5-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50cb5-109">See Also</span></span>  
 [<span data-ttu-id="50cb5-110">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="50cb5-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="50cb5-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="50cb5-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="50cb5-112">Znaki specjalne C#</span><span class="sxs-lookup"><span data-stu-id="50cb5-112">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)
