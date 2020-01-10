---
title: Parametry metody — C# odwołanie
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 2cc7f9178fa5c1a040be9d45ba66fac292bb0e28
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713374"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="29211-102">Parametry metody (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="29211-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="29211-103">Parametry zadeklarowane dla metody bez elementu [in](./in-parameter-modifier.md), [ref](./ref.md) lub [out](./out-parameter-modifier.md)są przesyłane do metody wywoływanej przez wartość.</span><span class="sxs-lookup"><span data-stu-id="29211-103">Parameters declared for a method without [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="29211-104">Tę wartość można zmienić w metodzie, ale zmieniona wartość nie będzie zachowywana, gdy kontrola przechodzi z powrotem do procedury wywołującej.</span><span class="sxs-lookup"><span data-stu-id="29211-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="29211-105">Za pomocą słowa kluczowego Parameter metody można zmienić to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="29211-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="29211-106">W tej sekcji opisano słowa kluczowe, których można użyć podczas deklarowania parametrów metody:</span><span class="sxs-lookup"><span data-stu-id="29211-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
- <span data-ttu-id="29211-107">[params](./params.md) określa, że ten parametr może przyjmować zmienną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="29211-107">[params](./params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
- <span data-ttu-id="29211-108">[w programie](./in-parameter-modifier.md) określa, że ten parametr jest przesyłany przez odwołanie, ale jest odczytywany tylko przez wywołaną metodę.</span><span class="sxs-lookup"><span data-stu-id="29211-108">[in](./in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
- <span data-ttu-id="29211-109">[ref](./ref.md) określa, że ten parametr jest przesyłany przez odwołanie i może być odczytywany lub zapisywana przez wywołaną metodę.</span><span class="sxs-lookup"><span data-stu-id="29211-109">[ref](./ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
- <span data-ttu-id="29211-110">[określa,](./out-parameter-modifier.md) że ten parametr jest przesyłany przez odwołanie i jest zapisywana przez wywołaną metodę.</span><span class="sxs-lookup"><span data-stu-id="29211-110">[out](./out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="29211-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29211-111">See also</span></span>

- [<span data-ttu-id="29211-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="29211-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="29211-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="29211-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="29211-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="29211-114">C# Keywords</span></span>](./index.md)
