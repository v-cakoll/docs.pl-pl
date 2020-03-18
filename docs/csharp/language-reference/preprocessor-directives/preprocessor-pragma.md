---
title: '#pragma - C# Odwołanie'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 3bd62364aeae0f21715711324655ef7d00d88afc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712458"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="7b89a-102">#pragma (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7b89a-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="7b89a-103">`#pragma`daje kompilatorowi specjalne instrukcje dotyczące kompilacji pliku, w którym się pojawia.</span><span class="sxs-lookup"><span data-stu-id="7b89a-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="7b89a-104">Instrukcje muszą być obsługiwane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="7b89a-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="7b89a-105">Innymi słowy nie można `#pragma` użyć do tworzenia niestandardowych instrukcji wstępnego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="7b89a-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="7b89a-106">Kompilator Języka Microsoft C# obsługuje następujące dwie `#pragma` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="7b89a-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="7b89a-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="7b89a-107">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="7b89a-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="7b89a-108">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="7b89a-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7b89a-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b89a-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b89a-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="7b89a-111">Nazwa uznanej pragmy.</span><span class="sxs-lookup"><span data-stu-id="7b89a-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="7b89a-112">Argumenty specyficzne dla Pragmy.</span><span class="sxs-lookup"><span data-stu-id="7b89a-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b89a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b89a-113">See also</span></span>

- [<span data-ttu-id="7b89a-114">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="7b89a-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7b89a-115">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="7b89a-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7b89a-116">Dyrektywy przedprocesorowe C#</span><span class="sxs-lookup"><span data-stu-id="7b89a-116">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="7b89a-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="7b89a-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="7b89a-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="7b89a-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
