---
title: '#pragma C# — odwołanie'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 65ca38ff6993117b6ed9f716d4ac93ba2d4a9ddf
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605672"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="c5abe-102">#pragma (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c5abe-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="c5abe-103">Dyrektywa `#pragma` zapewnia specjalne instrukcje dla kompilatora dotyczące kompilowania pliku, w którym występuje.</span><span class="sxs-lookup"><span data-stu-id="c5abe-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="c5abe-104">Instrukcje muszą być obsługiwane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="c5abe-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="c5abe-105">Innymi słowy, nie można użyć dyrektywy `#pragma` do tworzenia niestandardowych instrukcji przetwarzania wstępnego.</span><span class="sxs-lookup"><span data-stu-id="c5abe-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="c5abe-106">Kompilator Microsoft C# obsługuje dwie instrukcje `#pragma`:</span><span class="sxs-lookup"><span data-stu-id="c5abe-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="c5abe-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="c5abe-107">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="c5abe-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="c5abe-108">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="c5abe-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5abe-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5abe-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5abe-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="c5abe-111">Nazwa rozpoznanej dyrektywy pragma.</span><span class="sxs-lookup"><span data-stu-id="c5abe-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="c5abe-112">Argumenty określone dla dyrektywy pragma.</span><span class="sxs-lookup"><span data-stu-id="c5abe-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5abe-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5abe-113">See also</span></span>

- [<span data-ttu-id="c5abe-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c5abe-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c5abe-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c5abe-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c5abe-116">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="c5abe-116">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="c5abe-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="c5abe-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="c5abe-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="c5abe-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
