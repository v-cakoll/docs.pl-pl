---
title: metoda częściowa — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 62efd8b47fb565316b417a65e1b0fe37e40786c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713225"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="680f9-102">metoda częściowa (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="680f9-102">partial method (C# Reference)</span></span>

<span data-ttu-id="680f9-103">Metoda częściowa ma swój podpis zdefiniowany w jednej części typu częściowego, a jej implementacja zdefiniowana w innej części typu.</span><span class="sxs-lookup"><span data-stu-id="680f9-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="680f9-104">Metody częściowe umożliwiają projektantom klas zapewnienie haków metody, podobnie jak programy obsługi zdarzeń, które deweloperzy mogą zdecydować się zaimplementować, czy nie.</span><span class="sxs-lookup"><span data-stu-id="680f9-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="680f9-105">Jeśli deweloper nie dostarcza implementacji, kompilator usuwa podpis w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="680f9-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="680f9-106">Następujące warunki mają zastosowanie do metod częściowych:</span><span class="sxs-lookup"><span data-stu-id="680f9-106">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="680f9-107">Podpisy w obu częściach typu częściowego muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="680f9-107">Signatures in both parts of the partial type must match.</span></span>

- <span data-ttu-id="680f9-108">Metoda musi zwracać void.</span><span class="sxs-lookup"><span data-stu-id="680f9-108">The method must return void.</span></span>

- <span data-ttu-id="680f9-109">Modyfikatory dostępu nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="680f9-109">No access modifiers are allowed.</span></span> <span data-ttu-id="680f9-110">Metody częściowe są niejawnie prywatne.</span><span class="sxs-lookup"><span data-stu-id="680f9-110">Partial methods are implicitly private.</span></span>

<span data-ttu-id="680f9-111">W poniższym przykładzie przedstawiono metodę częściową zdefiniowaną w dwóch częściach klasy częściowej:</span><span class="sxs-lookup"><span data-stu-id="680f9-111">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="680f9-112">Aby uzyskać więcej informacji, zobacz [Klasy częściowe i metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="680f9-112">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="680f9-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="680f9-113">See also</span></span>

- [<span data-ttu-id="680f9-114">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="680f9-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="680f9-115">typ częściowy</span><span class="sxs-lookup"><span data-stu-id="680f9-115">partial type</span></span>](partial-type.md)
