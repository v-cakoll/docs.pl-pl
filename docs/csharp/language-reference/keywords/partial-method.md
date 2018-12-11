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
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238289"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="9bb8a-102">Metoda częściowa (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9bb8a-102">partial method (C# Reference)</span></span>

<span data-ttu-id="9bb8a-103">Metoda częściowa ma jeho signatura zdefiniowane w jednej części typu częściowego, a jego implementacja zdefiniowane w innej części tego typu.</span><span class="sxs-lookup"><span data-stu-id="9bb8a-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="9bb8a-104">Metody częściowe umożliwiają klasy projektantów zapewnić punkty zaczepienia metody, podobny do programów obsługi zdarzeń, które deweloperzy mogą zdecydować się na implementacji, czy nie.</span><span class="sxs-lookup"><span data-stu-id="9bb8a-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="9bb8a-105">Jeśli deweloper nie dostarcza implementację, kompilator usuwa podpisu w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9bb8a-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="9bb8a-106">Do metod częściowych mają zastosowanie następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="9bb8a-106">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="9bb8a-107">Podpisy w obie części typu częściowego muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="9bb8a-107">Signatures in both parts of the partial type must match.</span></span>

- <span data-ttu-id="9bb8a-108">Metoda musi zwracać typ void.</span><span class="sxs-lookup"><span data-stu-id="9bb8a-108">The method must return void.</span></span>

- <span data-ttu-id="9bb8a-109">Brak modyfikatorów dostępu są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="9bb8a-109">No access modifiers are allowed.</span></span> <span data-ttu-id="9bb8a-110">Metody częściowe są niejawnie prywatne.</span><span class="sxs-lookup"><span data-stu-id="9bb8a-110">Partial methods are implicitly private.</span></span>

<span data-ttu-id="9bb8a-111">Metoda częściowa definicja z dwóch części klasy częściowej można znaleźć w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9bb8a-111">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="9bb8a-112">Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="9bb8a-112">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9bb8a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9bb8a-113">See also</span></span>

- [<span data-ttu-id="9bb8a-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9bb8a-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9bb8a-115">typu częściowego</span><span class="sxs-lookup"><span data-stu-id="9bb8a-115">partial type</span></span>](partial-type.md)