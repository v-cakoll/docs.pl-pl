---
title: Dyrektywy preprocesora C#
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: 1c0a97cabce347be0bc9367f3d090a1fc699db19
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "47459649"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="94ab8-102">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="94ab8-102">C# preprocessor directives</span></span>
<span data-ttu-id="94ab8-103">Ta sekcja zawiera informacje o następujących dyrektywy preprocesora C#:</span><span class="sxs-lookup"><span data-stu-id="94ab8-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="94ab8-104">#if</span><span class="sxs-lookup"><span data-stu-id="94ab8-104">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
- [<span data-ttu-id="94ab8-105">#else</span><span class="sxs-lookup"><span data-stu-id="94ab8-105">#else</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)
- [<span data-ttu-id="94ab8-106">#elif</span><span class="sxs-lookup"><span data-stu-id="94ab8-106">#elif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)
- [<span data-ttu-id="94ab8-107">#endif</span><span class="sxs-lookup"><span data-stu-id="94ab8-107">#endif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)
- [<span data-ttu-id="94ab8-108">#define</span><span class="sxs-lookup"><span data-stu-id="94ab8-108">#define</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)
- [<span data-ttu-id="94ab8-109">#undef</span><span class="sxs-lookup"><span data-stu-id="94ab8-109">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)
- [<span data-ttu-id="94ab8-110">#warning</span><span class="sxs-lookup"><span data-stu-id="94ab8-110">#warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md)
- [<span data-ttu-id="94ab8-111">#error</span><span class="sxs-lookup"><span data-stu-id="94ab8-111">#error</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md)
- [<span data-ttu-id="94ab8-112">#line</span><span class="sxs-lookup"><span data-stu-id="94ab8-112">#line</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-line.md)
- [<span data-ttu-id="94ab8-113">#region</span><span class="sxs-lookup"><span data-stu-id="94ab8-113">#region</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-region.md)
- [<span data-ttu-id="94ab8-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="94ab8-114">#endregion</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md)
- [<span data-ttu-id="94ab8-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="94ab8-115">#pragma</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma.md)
- [<span data-ttu-id="94ab8-116">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="94ab8-116">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)
- [<span data-ttu-id="94ab8-117">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="94ab8-117">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

<span data-ttu-id="94ab8-118">Zobacz tematy, aby uzyskać więcej informacji i przykładów.</span><span class="sxs-lookup"><span data-stu-id="94ab8-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="94ab8-119">Mimo że kompilator nie ma oddzielnego preprocesora, dyrektywy opisane w tej sekcji są przetwarzane przy założeniu, że taki preprocesor istnieje.</span><span class="sxs-lookup"><span data-stu-id="94ab8-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="94ab8-120">Dyrektywy te są pomocne przy kompilacji warunkowej.</span><span class="sxs-lookup"><span data-stu-id="94ab8-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="94ab8-121">W przeciwieństwie do dyrektyw w językach C i C++ nie można ich używać do tworzenia makr.</span><span class="sxs-lookup"><span data-stu-id="94ab8-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="94ab8-122">Dyrektywa preprocesora musi być jedyną instrukcją w wierszu.</span><span class="sxs-lookup"><span data-stu-id="94ab8-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="94ab8-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94ab8-123">See also</span></span>

- [<span data-ttu-id="94ab8-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="94ab8-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="94ab8-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="94ab8-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
