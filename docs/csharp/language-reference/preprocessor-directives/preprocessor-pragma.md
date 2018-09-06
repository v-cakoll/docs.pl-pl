---
title: '#pragma — (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 5ae397cc61e0c6b58ed2079369131ebb7e352eae
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747486"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="c5df8-102">#pragma (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c5df8-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="c5df8-103">Dyrektywa `#pragma` zapewnia specjalne instrukcje dla kompilatora dotyczące kompilowania pliku, w którym występuje.</span><span class="sxs-lookup"><span data-stu-id="c5df8-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="c5df8-104">Instrukcje muszą być obsługiwane przez kompilator. </span><span class="sxs-lookup"><span data-stu-id="c5df8-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="c5df8-105">Innymi słowy, nie można użyć dyrektywy `#pragma` do tworzenia niestandardowych instrukcji przetwarzania wstępnego.</span><span class="sxs-lookup"><span data-stu-id="c5df8-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="c5df8-106">Kompilator Microsoft C# obsługuje dwie instrukcje `#pragma`:</span><span class="sxs-lookup"><span data-stu-id="c5df8-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="c5df8-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="c5df8-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="c5df8-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="c5df8-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="c5df8-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5df8-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5df8-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5df8-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="c5df8-111">Nazwa rozpoznanej dyrektywy pragma.</span><span class="sxs-lookup"><span data-stu-id="c5df8-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="c5df8-112">Argumenty określone dla dyrektywy pragma.</span><span class="sxs-lookup"><span data-stu-id="c5df8-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5df8-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5df8-113">See Also</span></span>

- [<span data-ttu-id="c5df8-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c5df8-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c5df8-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c5df8-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c5df8-116">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="c5df8-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
- [<span data-ttu-id="c5df8-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="c5df8-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
- [<span data-ttu-id="c5df8-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="c5df8-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)
