---
title: Metoda częściowa - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 742d6ca744ac723179718f1400e600411712dd40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660947"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="4f5c0-102">Metoda częściowa (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4f5c0-102">partial method (C# Reference)</span></span>

<span data-ttu-id="4f5c0-103">Metoda częściowa ma jeho signatura zdefiniowane w jednej części typu częściowego, a jego implementacja zdefiniowane w innej części tego typu.</span><span class="sxs-lookup"><span data-stu-id="4f5c0-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="4f5c0-104">Metody częściowe umożliwiają klasy projektantów zapewnić punkty zaczepienia metody, podobny do programów obsługi zdarzeń, które deweloperzy mogą zdecydować się na implementacji, czy nie.</span><span class="sxs-lookup"><span data-stu-id="4f5c0-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="4f5c0-105">Jeśli deweloper nie dostarcza implementację, kompilator usuwa podpisu w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4f5c0-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="4f5c0-106">Do metod częściowych mają zastosowanie następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="4f5c0-106">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="4f5c0-107">Podpisy w obie części typu częściowego muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="4f5c0-107">Signatures in both parts of the partial type must match.</span></span>

- <span data-ttu-id="4f5c0-108">Metoda musi zwracać typ void.</span><span class="sxs-lookup"><span data-stu-id="4f5c0-108">The method must return void.</span></span>

- <span data-ttu-id="4f5c0-109">Brak modyfikatorów dostępu są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="4f5c0-109">No access modifiers are allowed.</span></span> <span data-ttu-id="4f5c0-110">Metody częściowe są niejawnie prywatne.</span><span class="sxs-lookup"><span data-stu-id="4f5c0-110">Partial methods are implicitly private.</span></span>

<span data-ttu-id="4f5c0-111">Metoda częściowa definicja z dwóch części klasy częściowej można znaleźć w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4f5c0-111">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="4f5c0-112">Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="4f5c0-112">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4f5c0-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f5c0-113">See also</span></span>

- [<span data-ttu-id="4f5c0-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4f5c0-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4f5c0-115">typu częściowego</span><span class="sxs-lookup"><span data-stu-id="4f5c0-115">partial type</span></span>](partial-type.md)