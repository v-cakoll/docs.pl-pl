---
title: Metoda częściowa C# — odwołanie
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 62efd8b47fb565316b417a65e1b0fe37e40786c8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713225"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="e03f6-102">Metoda częściowaC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="e03f6-102">partial method (C# Reference)</span></span>

<span data-ttu-id="e03f6-103">Metoda częściowa ma swój podpis zdefiniowany w jednej części typu częściowego i jego implementacja zdefiniowana w innej części typu.</span><span class="sxs-lookup"><span data-stu-id="e03f6-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="e03f6-104">Metody częściowe umożliwiają projektantom klas dostarczanie punktów zaczepienia metody, podobnie jak procedury obsługi zdarzeń, które deweloperzy mogą zdecydować się na wdrożenie lub nie.</span><span class="sxs-lookup"><span data-stu-id="e03f6-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="e03f6-105">Jeśli deweloper nie poda implementacji, kompilator usuwa sygnaturę w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e03f6-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="e03f6-106">Poniższe warunki dotyczą metod częściowych:</span><span class="sxs-lookup"><span data-stu-id="e03f6-106">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="e03f6-107">Sygnatury w obu częściach typu częściowego muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="e03f6-107">Signatures in both parts of the partial type must match.</span></span>

- <span data-ttu-id="e03f6-108">Metoda musi zwracać typ void.</span><span class="sxs-lookup"><span data-stu-id="e03f6-108">The method must return void.</span></span>

- <span data-ttu-id="e03f6-109">Modyfikatory dostępu nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="e03f6-109">No access modifiers are allowed.</span></span> <span data-ttu-id="e03f6-110">Metody częściowe są niejawnie prywatne.</span><span class="sxs-lookup"><span data-stu-id="e03f6-110">Partial methods are implicitly private.</span></span>

<span data-ttu-id="e03f6-111">Poniższy przykład przedstawia metodę częściową zdefiniowaną w dwóch częściach klasy częściowej:</span><span class="sxs-lookup"><span data-stu-id="e03f6-111">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="e03f6-112">Aby uzyskać więcej informacji, zobacz [częściowe klasy i metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="e03f6-112">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e03f6-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e03f6-113">See also</span></span>

- [<span data-ttu-id="e03f6-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e03f6-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e03f6-115">Typ częściowy</span><span class="sxs-lookup"><span data-stu-id="e03f6-115">partial type</span></span>](partial-type.md)
