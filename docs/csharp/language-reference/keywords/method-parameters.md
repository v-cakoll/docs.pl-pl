---
title: Parametry metody - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: f6d0309a91c426123be13a4302d711c92d4ea0f7
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242733"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="fef31-102">Parametry metody (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="fef31-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="fef31-103">Parametry zadeklarowane dla metody bez [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md), są przekazywane do metody wywoływane przez wartość.</span><span class="sxs-lookup"><span data-stu-id="fef31-103">Parameters declared for a method without [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="fef31-104">Tę wartość można zmienić w metodzie, ale zmiany wartości nie zostaną zachowane, gdy kontrola przechodzi do procedury wywołującej.</span><span class="sxs-lookup"><span data-stu-id="fef31-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="fef31-105">Za pomocą słowo kluczowe parametru metody, można zmienić to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="fef31-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="fef31-106">W tej sekcji opisano słowa kluczowe, których można użyć podczas deklarowania parametry metody:</span><span class="sxs-lookup"><span data-stu-id="fef31-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   <span data-ttu-id="fef31-107">[params](../../../csharp/language-reference/keywords/params.md) Określa, że ten parametr może potrwać zmienną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="fef31-107">[params](../../../csharp/language-reference/keywords/params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
-   <span data-ttu-id="fef31-108">[w](../../../csharp/language-reference/keywords/in-parameter-modifier.md) Określa, że ten parametr jest przekazywany przez odwołanie, ale jest odczytywany tylko przez metodę o nazwie.</span><span class="sxs-lookup"><span data-stu-id="fef31-108">[in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
-   <span data-ttu-id="fef31-109">[REF](../../../csharp/language-reference/keywords/ref.md) Określa, że ten parametr jest przekazywany przez odwołanie i może być odczytywanych lub zapisywanych przez metodę o nazwie.</span><span class="sxs-lookup"><span data-stu-id="fef31-109">[ref](../../../csharp/language-reference/keywords/ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
-   <span data-ttu-id="fef31-110">[limit](../../../csharp/language-reference/keywords/out-parameter-modifier.md) Określa, że ten parametr jest przekazywany przez odwołanie i są zapisywane przez metodę o nazwie.</span><span class="sxs-lookup"><span data-stu-id="fef31-110">[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fef31-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fef31-111">See Also</span></span>

- [<span data-ttu-id="fef31-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="fef31-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="fef31-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fef31-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="fef31-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="fef31-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
