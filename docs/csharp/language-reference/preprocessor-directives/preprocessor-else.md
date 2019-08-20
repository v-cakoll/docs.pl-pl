---
title: '#else- C# Reference'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: d6a514f71b3526b2ffe347cdd971b81907fb0aad
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605717"
---
# <a name="else-c-reference"></a><span data-ttu-id="27aae-102">#else (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="27aae-102">#else (C# Reference)</span></span>
<span data-ttu-id="27aae-103">`#else`umożliwia utworzenie złożonej dyrektywy warunkowej, tak aby w przypadku braku wyrażeń w powyższym [#if](./preprocessor-if.md) lub (opcjonalnie) [#elif](./preprocessor-elif.md) dyrektywy nie były oceniane do `true`, kompilator oceni cały kod między `#else` i kolejne `#endif`.</span><span class="sxs-lookup"><span data-stu-id="27aae-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](./preprocessor-if.md) or (optional) [#elif](./preprocessor-elif.md) directives evaluate to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27aae-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27aae-104">Remarks</span></span>  
 <span data-ttu-id="27aae-105">Następną dyrektywą preprocesora po [ musi być ](./preprocessor-endif.md)#endif`#else`.</span><span class="sxs-lookup"><span data-stu-id="27aae-105">[#endif](./preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="27aae-106">Aby zapoznać się z przykładem użycia dyrektywy [, zobacz ](./preprocessor-if.md)#if`#else`.</span><span class="sxs-lookup"><span data-stu-id="27aae-106">See [#if](./preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27aae-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27aae-107">See also</span></span>

- [<span data-ttu-id="27aae-108">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="27aae-108">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="27aae-109">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="27aae-109">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="27aae-110">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="27aae-110">C# Preprocessor Directives</span></span>](./index.md)
