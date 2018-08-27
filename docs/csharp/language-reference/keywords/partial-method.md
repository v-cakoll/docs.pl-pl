---
title: partial — Metoda (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 69e16dd8b0fe0055124aca90fea65a36d9e413f3
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933688"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="9cf85-102">partial — Metoda (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9cf85-102">partial (Method) (C# Reference)</span></span>
<span data-ttu-id="9cf85-103">Metoda częściowa ma jeho signatura zdefiniowane w jednej części typu częściowego, a jego implementacja zdefiniowane w innej części tego typu.</span><span class="sxs-lookup"><span data-stu-id="9cf85-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="9cf85-104">Metody częściowe umożliwiają klasy projektantów zapewnić punkty zaczepienia metody, podobny do programów obsługi zdarzeń, które deweloperzy mogą zdecydować się na implementacji, czy nie.</span><span class="sxs-lookup"><span data-stu-id="9cf85-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="9cf85-105">Jeśli deweloper nie dostarcza implementację, kompilator usuwa podpisu w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9cf85-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="9cf85-106">Do metod częściowych mają zastosowanie następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="9cf85-106">The following conditions apply to partial methods:</span></span>  
  
-   <span data-ttu-id="9cf85-107">Podpisy w obie części typu częściowego muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="9cf85-107">Signatures in both parts of the partial type must match.</span></span>  
  
-   <span data-ttu-id="9cf85-108">Metoda musi zwracać typ void.</span><span class="sxs-lookup"><span data-stu-id="9cf85-108">The method must return void.</span></span>  
  
-   <span data-ttu-id="9cf85-109">Brak modyfikatorów dostępu są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="9cf85-109">No access modifiers are allowed.</span></span> <span data-ttu-id="9cf85-110">Metody częściowe są niejawnie prywatne.</span><span class="sxs-lookup"><span data-stu-id="9cf85-110">Partial methods are implicitly private.</span></span>  
  
 <span data-ttu-id="9cf85-111">Metoda częściowa definicja z dwóch części klasy częściowej można znaleźć w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9cf85-111">The following example shows a partial method defined in two parts of a partial class:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]  
  
 <span data-ttu-id="9cf85-112">Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="9cf85-112">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cf85-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9cf85-113">See Also</span></span>

- [<span data-ttu-id="9cf85-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9cf85-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="9cf85-115">partial (typ)</span><span class="sxs-lookup"><span data-stu-id="9cf85-115">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)
