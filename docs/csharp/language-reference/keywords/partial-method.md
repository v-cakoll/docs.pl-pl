---
title: partial — Metoda (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 29b5d442a1aa33babc24aee987e749c93a5ec727
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269044"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="9b7e0-102">partial — Metoda (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9b7e0-102">partial (Method) (C# Reference)</span></span>
<span data-ttu-id="9b7e0-103">Metoda częściowa ma podpis zdefiniowane w jednej części typu częściowego, a jej implementacja zdefiniowany w innej części typu.</span><span class="sxs-lookup"><span data-stu-id="9b7e0-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="9b7e0-104">Metody częściowe umożliwia projektantom klasy Podaj punkty zaczepienia metody, podobny do programów obsługi zdarzeń, które deweloperzy mogą zdecydować się na implementacji lub nie.</span><span class="sxs-lookup"><span data-stu-id="9b7e0-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="9b7e0-105">Jeśli projektanta nie dostarcza implementację, kompilator usuwa podpisu w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9b7e0-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="9b7e0-106">Do metody częściowe mają zastosowanie następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="9b7e0-106">The following conditions apply to partial methods:</span></span>  
  
-   <span data-ttu-id="9b7e0-107">Podpisy obie części typu częściowego muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="9b7e0-107">Signatures in both parts of the partial type must match.</span></span>  
  
-   <span data-ttu-id="9b7e0-108">Metoda musi zwracać typ void.</span><span class="sxs-lookup"><span data-stu-id="9b7e0-108">The method must return void.</span></span>  
  
-   <span data-ttu-id="9b7e0-109">Modyfikatory dostępu, nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="9b7e0-109">No access modifiers are allowed.</span></span> <span data-ttu-id="9b7e0-110">Metody częściowe są domyślnie prywatne.</span><span class="sxs-lookup"><span data-stu-id="9b7e0-110">Partial methods are implicitly private.</span></span>  
  
 <span data-ttu-id="9b7e0-111">W poniższym przykładzie przedstawiono metody częściowej zdefiniowane w dwóch częściach częściowej klasy:</span><span class="sxs-lookup"><span data-stu-id="9b7e0-111">The following example shows a partial method defined in two parts of a partial class:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]  
  
 <span data-ttu-id="9b7e0-112">Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="9b7e0-112">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b7e0-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b7e0-113">See Also</span></span>  
 [<span data-ttu-id="9b7e0-114">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="9b7e0-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9b7e0-115">partial (typ)</span><span class="sxs-lookup"><span data-stu-id="9b7e0-115">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)
