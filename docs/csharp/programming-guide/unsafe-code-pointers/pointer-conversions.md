---
title: Konwersje wskaźników — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 517166331d2bcf73132269ce2adcf68d5f60b4fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745364"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="92701-102">Konwersje wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="92701-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="92701-103">W poniższej tabeli przedstawiono wstępnie zdefiniowane konwersje niejawnych wskaźników.</span><span class="sxs-lookup"><span data-stu-id="92701-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="92701-104">Konwersje niejawne mogą wystąpić w wielu sytuacjach, w tym wywoływanie metod i instrukcje przypisania.</span><span class="sxs-lookup"><span data-stu-id="92701-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="92701-105">Niejawne konwersje wskaźników</span><span class="sxs-lookup"><span data-stu-id="92701-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="92701-106">Z</span><span class="sxs-lookup"><span data-stu-id="92701-106">From</span></span>|<span data-ttu-id="92701-107">Do</span><span class="sxs-lookup"><span data-stu-id="92701-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="92701-108">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="92701-108">Any pointer type</span></span>|<span data-ttu-id="92701-109">pozycję</span><span class="sxs-lookup"><span data-stu-id="92701-109">void\*</span></span>|  
|<span data-ttu-id="92701-110">wartość null</span><span class="sxs-lookup"><span data-stu-id="92701-110">null</span></span>|<span data-ttu-id="92701-111">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="92701-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="92701-112">Jawna konwersja wskaźnika jest używana do przeprowadzania konwersji, dla których nie istnieje niejawna konwersja za pomocą wyrażenia Cast.</span><span class="sxs-lookup"><span data-stu-id="92701-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="92701-113">W poniższej tabeli przedstawiono te konwersje.</span><span class="sxs-lookup"><span data-stu-id="92701-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="92701-114">Jawne konwersje wskaźników</span><span class="sxs-lookup"><span data-stu-id="92701-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="92701-115">Z</span><span class="sxs-lookup"><span data-stu-id="92701-115">From</span></span>|<span data-ttu-id="92701-116">Do</span><span class="sxs-lookup"><span data-stu-id="92701-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="92701-117">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="92701-117">Any pointer type</span></span>|<span data-ttu-id="92701-118">Dowolny inny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="92701-118">Any other pointer type</span></span>|  
|<span data-ttu-id="92701-119">bajty, Byte, Short, UShort, int, uint, Long lub ULONG</span><span class="sxs-lookup"><span data-stu-id="92701-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="92701-120">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="92701-120">Any pointer type</span></span>|  
|<span data-ttu-id="92701-121">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="92701-121">Any pointer type</span></span>|<span data-ttu-id="92701-122">bajty, Byte, Short, UShort, int, uint, Long lub ULONG</span><span class="sxs-lookup"><span data-stu-id="92701-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="92701-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="92701-123">Example</span></span>  
 <span data-ttu-id="92701-124">W poniższym przykładzie wskaźnik do `int` jest konwertowany na wskaźnik, aby `byte`.</span><span class="sxs-lookup"><span data-stu-id="92701-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="92701-125">Zauważ, że wskaźnik wskazuje najniższy przyjmowany bajt zmiennej.</span><span class="sxs-lookup"><span data-stu-id="92701-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="92701-126">Po kolejnych zwiększeniu wyniku do rozmiaru `int` (4 bajty) można wyświetlić pozostałe bajty zmiennej.</span><span class="sxs-lookup"><span data-stu-id="92701-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="92701-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92701-127">See also</span></span>

- [<span data-ttu-id="92701-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="92701-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="92701-129">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="92701-129">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="92701-130">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="92701-130">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="92701-131">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="92701-131">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="92701-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="92701-132">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="92701-133">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="92701-133">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="92701-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="92701-134">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
