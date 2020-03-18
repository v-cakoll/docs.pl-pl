---
title: '#else - C# Odwołanie'
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: 967ef38687b739ef3bea3f8923ab26bba0b6cea9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712562"
---
# <a name="else-c-reference"></a><span data-ttu-id="d22a2-102">#else (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d22a2-102">#else (C# Reference)</span></span>
<span data-ttu-id="d22a2-103">`#else`umożliwia utworzenie złożonej dyrektywy warunkowej, tak aby jeśli żadne z wyrażeń w poprzedniej [#if](./preprocessor-if.md) lub (opcjonalnie) `#endif` [#elif](./preprocessor-elif.md) dyrektywy oceniają, `true`kompilator oceni cały kod między `#else` i kolejnych .</span><span class="sxs-lookup"><span data-stu-id="d22a2-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](./preprocessor-if.md) or (optional) [#elif](./preprocessor-elif.md) directives evaluate to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d22a2-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d22a2-104">Remarks</span></span>  
 <span data-ttu-id="d22a2-105">[#endif](./preprocessor-endif.md) musi być następna `#else`dyrektywa preprocesora po .</span><span class="sxs-lookup"><span data-stu-id="d22a2-105">[#endif](./preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="d22a2-106">Zobacz [#if](./preprocessor-if.md) przykład użycia `#else`.</span><span class="sxs-lookup"><span data-stu-id="d22a2-106">See [#if](./preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d22a2-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d22a2-107">See also</span></span>

- [<span data-ttu-id="d22a2-108">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="d22a2-108">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d22a2-109">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="d22a2-109">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d22a2-110">Dyrektywy przedprocesorowe C#</span><span class="sxs-lookup"><span data-stu-id="d22a2-110">C# Preprocessor Directives</span></span>](./index.md)
