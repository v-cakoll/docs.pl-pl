---
title: Parametry metody — odwołanie do języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 2cc7f9178fa5c1a040be9d45ba66fac292bb0e28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713374"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="fbb95-102">Parametry metody (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="fbb95-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="fbb95-103">Parametry zadeklarowane dla metody bez [w](./in-parameter-modifier.md), [ref](./ref.md) lub [out](./out-parameter-modifier.md), są przekazywane do metody wywoływanej przez wartość.</span><span class="sxs-lookup"><span data-stu-id="fbb95-103">Parameters declared for a method without [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="fbb95-104">Tę wartość można zmienić w metodzie, ale zmieniona wartość nie zostanie zachowana, gdy kontrola przechodzi z powrotem do procedury wywoływania.</span><span class="sxs-lookup"><span data-stu-id="fbb95-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="fbb95-105">Za pomocą słowa kluczowego parametrmetody można zmienić to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="fbb95-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="fbb95-106">W tej sekcji opisano słowa kluczowe, których można użyć podczas deklarowania parametrów metody:</span><span class="sxs-lookup"><span data-stu-id="fbb95-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
- <span data-ttu-id="fbb95-107">[params](./params.md) określa, że ten parametr może mieć zmienną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="fbb95-107">[params](./params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
- <span data-ttu-id="fbb95-108">[w](./in-parameter-modifier.md) określa, że ten parametr jest przekazywany przez odwołanie, ale jest odczytywany tylko przez wywoływana metoda.</span><span class="sxs-lookup"><span data-stu-id="fbb95-108">[in](./in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
- <span data-ttu-id="fbb95-109">[ref](./ref.md) określa, że ten parametr jest przekazywany przez odwołanie i może być odczytywany lub zapisywany przez wywoływaną metodę.</span><span class="sxs-lookup"><span data-stu-id="fbb95-109">[ref](./ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
- <span data-ttu-id="fbb95-110">[out](./out-parameter-modifier.md) określa, że ten parametr jest przekazywany przez odwołanie i jest zapisywany przez wywoływaną metodę.</span><span class="sxs-lookup"><span data-stu-id="fbb95-110">[out](./out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fbb95-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fbb95-111">See also</span></span>

- [<span data-ttu-id="fbb95-112">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="fbb95-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fbb95-113">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="fbb95-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fbb95-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="fbb95-114">C# Keywords</span></span>](./index.md)
