---
title: Dyrektywy preprocesora języka C#
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: f63ba3e0bd89a88ad04b14c2f359a8cde65e8f12
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608600"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="eb8d2-102">Dyrektywy preprocesora języka C#</span><span class="sxs-lookup"><span data-stu-id="eb8d2-102">C# preprocessor directives</span></span>
<span data-ttu-id="eb8d2-103">Ta sekcja zawiera informacje o następujących C# dyrektywach preprocesora:</span><span class="sxs-lookup"><span data-stu-id="eb8d2-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="eb8d2-104">#if</span><span class="sxs-lookup"><span data-stu-id="eb8d2-104">#if</span></span>](./preprocessor-if.md)
- [<span data-ttu-id="eb8d2-105">#else</span><span class="sxs-lookup"><span data-stu-id="eb8d2-105">#else</span></span>](./preprocessor-else.md)
- [<span data-ttu-id="eb8d2-106">#elif</span><span class="sxs-lookup"><span data-stu-id="eb8d2-106">#elif</span></span>](./preprocessor-elif.md)
- [<span data-ttu-id="eb8d2-107">#endif</span><span class="sxs-lookup"><span data-stu-id="eb8d2-107">#endif</span></span>](./preprocessor-endif.md)
- [<span data-ttu-id="eb8d2-108">#define</span><span class="sxs-lookup"><span data-stu-id="eb8d2-108">#define</span></span>](./preprocessor-define.md)
- [<span data-ttu-id="eb8d2-109">#undef</span><span class="sxs-lookup"><span data-stu-id="eb8d2-109">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="eb8d2-110">#warning</span><span class="sxs-lookup"><span data-stu-id="eb8d2-110">#warning</span></span>](./preprocessor-warning.md)
- [<span data-ttu-id="eb8d2-111">#error</span><span class="sxs-lookup"><span data-stu-id="eb8d2-111">#error</span></span>](./preprocessor-error.md)
- [<span data-ttu-id="eb8d2-112">#line</span><span class="sxs-lookup"><span data-stu-id="eb8d2-112">#line</span></span>](./preprocessor-line.md)
- [<span data-ttu-id="eb8d2-113">#region</span><span class="sxs-lookup"><span data-stu-id="eb8d2-113">#region</span></span>](./preprocessor-region.md)
- [<span data-ttu-id="eb8d2-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="eb8d2-114">#endregion</span></span>](./preprocessor-endregion.md)
- [<span data-ttu-id="eb8d2-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="eb8d2-115">#pragma</span></span>](./preprocessor-pragma.md)
- [<span data-ttu-id="eb8d2-116">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="eb8d2-116">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="eb8d2-117">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="eb8d2-117">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

<span data-ttu-id="eb8d2-118">Więcej informacji i przykłady można znaleźć w poszczególnych tematach.</span><span class="sxs-lookup"><span data-stu-id="eb8d2-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="eb8d2-119">Mimo że kompilator nie ma oddzielnego preprocesora, dyrektywy opisane w tej sekcji są przetwarzane przy założeniu, że taki preprocesor istnieje.</span><span class="sxs-lookup"><span data-stu-id="eb8d2-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="eb8d2-120">Dyrektywy te są pomocne przy kompilacji warunkowej.</span><span class="sxs-lookup"><span data-stu-id="eb8d2-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="eb8d2-121">W przeciwieństwie do dyrektyw w językach C i C++ nie można ich używać do tworzenia makr.</span><span class="sxs-lookup"><span data-stu-id="eb8d2-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="eb8d2-122">Dyrektywa preprocesora musi być jedyną instrukcją w wierszu.</span><span class="sxs-lookup"><span data-stu-id="eb8d2-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb8d2-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb8d2-123">See also</span></span>

- [<span data-ttu-id="eb8d2-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="eb8d2-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eb8d2-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="eb8d2-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
