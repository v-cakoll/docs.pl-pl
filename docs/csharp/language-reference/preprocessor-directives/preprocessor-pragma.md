---
title: '#pragma — C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 65867bc441711193f93142d1c65122b6bc60c25d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241830"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="f72a5-102">#pragma (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f72a5-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="f72a5-103">Dyrektywa `#pragma` zapewnia specjalne instrukcje dla kompilatora dotyczące kompilowania pliku, w którym występuje.</span><span class="sxs-lookup"><span data-stu-id="f72a5-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="f72a5-104">Instrukcje muszą być obsługiwane przez kompilator. </span><span class="sxs-lookup"><span data-stu-id="f72a5-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="f72a5-105">Innymi słowy, nie można użyć dyrektywy `#pragma` do tworzenia niestandardowych instrukcji przetwarzania wstępnego.</span><span class="sxs-lookup"><span data-stu-id="f72a5-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="f72a5-106">Kompilator Microsoft C# obsługuje dwie instrukcje `#pragma`:</span><span class="sxs-lookup"><span data-stu-id="f72a5-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="f72a5-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="f72a5-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="f72a5-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="f72a5-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="f72a5-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="f72a5-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f72a5-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="f72a5-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="f72a5-111">Nazwa rozpoznanej dyrektywy pragma.</span><span class="sxs-lookup"><span data-stu-id="f72a5-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="f72a5-112">Argumenty określone dla dyrektywy pragma.</span><span class="sxs-lookup"><span data-stu-id="f72a5-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f72a5-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f72a5-113">See Also</span></span>

- [<span data-ttu-id="f72a5-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f72a5-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="f72a5-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f72a5-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f72a5-116">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="f72a5-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
- [<span data-ttu-id="f72a5-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="f72a5-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
- [<span data-ttu-id="f72a5-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="f72a5-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)
