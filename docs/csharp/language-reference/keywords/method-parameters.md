---
title: "Parametry metody (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b20d2d233350cfb9de55cbd07e722082ec311597
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="62a9a-102">Parametry metody (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="62a9a-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="62a9a-103">Zadeklarowane parametry dla metody bez [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md), są przekazywane do metody wywoływane przez wartość.</span><span class="sxs-lookup"><span data-stu-id="62a9a-103">Parameters declared for a method without [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="62a9a-104">Tę wartość można zmienić w metodzie, ale zmiany wartości nie zostaną zachowane, gdy formant przechodzi do procedury wywołującej.</span><span class="sxs-lookup"><span data-stu-id="62a9a-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="62a9a-105">Za pomocą słowa kluczowego parametru metody, można zmienić to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="62a9a-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="62a9a-106">W tej sekcji opisano słowa kluczowe, które można użyć przy deklarowaniu parametry metody:</span><span class="sxs-lookup"><span data-stu-id="62a9a-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   [<span data-ttu-id="62a9a-107">params</span><span class="sxs-lookup"><span data-stu-id="62a9a-107">params</span></span>](../../../csharp/language-reference/keywords/params.md)  
  
-   [<span data-ttu-id="62a9a-108">in</span><span class="sxs-lookup"><span data-stu-id="62a9a-108">in</span></span>](../../../csharp/language-reference/keywords/in-parameter-modifier.md)  
  
-   [<span data-ttu-id="62a9a-109">ref</span><span class="sxs-lookup"><span data-stu-id="62a9a-109">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
  
-   [<span data-ttu-id="62a9a-110">out</span><span class="sxs-lookup"><span data-stu-id="62a9a-110">out</span></span>](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
  
## <a name="see-also"></a><span data-ttu-id="62a9a-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62a9a-111">See Also</span></span>  
 [<span data-ttu-id="62a9a-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="62a9a-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="62a9a-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="62a9a-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="62a9a-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="62a9a-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
