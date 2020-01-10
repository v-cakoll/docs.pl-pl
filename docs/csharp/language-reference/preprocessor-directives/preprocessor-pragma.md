---
title: '#pragma C# — odwołanie'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 3bd62364aeae0f21715711324655ef7d00d88afc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712458"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="ccc8c-102">#pragma (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ccc8c-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="ccc8c-103">Dyrektywa `#pragma` zapewnia specjalne instrukcje dla kompilatora dotyczące kompilowania pliku, w którym występuje.</span><span class="sxs-lookup"><span data-stu-id="ccc8c-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="ccc8c-104">Instrukcje muszą być obsługiwane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="ccc8c-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="ccc8c-105">Innymi słowy, nie można użyć dyrektywy `#pragma` do tworzenia niestandardowych instrukcji przetwarzania wstępnego.</span><span class="sxs-lookup"><span data-stu-id="ccc8c-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="ccc8c-106">Kompilator Microsoft C# obsługuje dwie instrukcje `#pragma`:</span><span class="sxs-lookup"><span data-stu-id="ccc8c-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="ccc8c-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="ccc8c-107">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="ccc8c-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="ccc8c-108">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="ccc8c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="ccc8c-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccc8c-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="ccc8c-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="ccc8c-111">Nazwa rozpoznanej dyrektywy pragma.</span><span class="sxs-lookup"><span data-stu-id="ccc8c-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="ccc8c-112">Argumenty określone dla dyrektywy pragma.</span><span class="sxs-lookup"><span data-stu-id="ccc8c-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccc8c-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ccc8c-113">See also</span></span>

- [<span data-ttu-id="ccc8c-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ccc8c-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ccc8c-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ccc8c-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ccc8c-116">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="ccc8c-116">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="ccc8c-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="ccc8c-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="ccc8c-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="ccc8c-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
