---
title: "Parametry metody (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 924e261cc876d2428e28ed0f490beb46b95f96e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="93e14-102">Parametry metody (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="93e14-102">Method Parameters (C# Reference)</span></span>
<span data-ttu-id="93e14-103">Jeśli parametr jest zadeklarowany dla metody bez [ref](../../../csharp/language-reference/keywords/ref.md) lub [limit](../../../csharp/language-reference/keywords/out.md), parametr może mieć wartość skojarzona z nim.</span><span class="sxs-lookup"><span data-stu-id="93e14-103">If a parameter is declared for a method without [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md), the parameter can have a value associated with it.</span></span> <span data-ttu-id="93e14-104">Tę wartość można zmienić w metodzie, ale zmiany wartości nie zostaną zachowane, gdy formant przechodzi do procedury wywołującej.</span><span class="sxs-lookup"><span data-stu-id="93e14-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="93e14-105">Za pomocą słowa kluczowego parametru metody, można zmienić to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="93e14-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="93e14-106">W tej sekcji opisano słowa kluczowe, które można użyć przy deklarowaniu parametry metody:</span><span class="sxs-lookup"><span data-stu-id="93e14-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   [<span data-ttu-id="93e14-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="93e14-107">params</span></span>](../../../csharp/language-reference/keywords/params.md)  
  
-   [<span data-ttu-id="93e14-108">REF</span><span class="sxs-lookup"><span data-stu-id="93e14-108">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
  
-   [<span data-ttu-id="93e14-109">limit</span><span class="sxs-lookup"><span data-stu-id="93e14-109">out</span></span>](../../../csharp/language-reference/keywords/out.md)  
  
## <a name="see-also"></a><span data-ttu-id="93e14-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93e14-110">See Also</span></span>  
 [<span data-ttu-id="93e14-111">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="93e14-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="93e14-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="93e14-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="93e14-113">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="93e14-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
