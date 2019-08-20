---
title: Konwersje wskaźników — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 81b2110e6a571e174693fd272d1c6b4bf44dbae3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588219"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="b7bc9-102">Konwersje wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="b7bc9-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="b7bc9-103">W poniższej tabeli przedstawiono wstępnie zdefiniowane konwersje niejawnych wskaźników.</span><span class="sxs-lookup"><span data-stu-id="b7bc9-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="b7bc9-104">Konwersje niejawne mogą wystąpić w wielu sytuacjach, w tym wywoływanie metod i instrukcje przypisania.</span><span class="sxs-lookup"><span data-stu-id="b7bc9-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="b7bc9-105">Niejawne konwersje wskaźników</span><span class="sxs-lookup"><span data-stu-id="b7bc9-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="b7bc9-106">Z</span><span class="sxs-lookup"><span data-stu-id="b7bc9-106">From</span></span>|<span data-ttu-id="b7bc9-107">Zadanie</span><span class="sxs-lookup"><span data-stu-id="b7bc9-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="b7bc9-108">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="b7bc9-108">Any pointer type</span></span>|<span data-ttu-id="b7bc9-109">pozycję</span><span class="sxs-lookup"><span data-stu-id="b7bc9-109">void\*</span></span>|  
|<span data-ttu-id="b7bc9-110">wartość null</span><span class="sxs-lookup"><span data-stu-id="b7bc9-110">null</span></span>|<span data-ttu-id="b7bc9-111">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="b7bc9-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="b7bc9-112">Jawna konwersja wskaźnika jest używana do przeprowadzania konwersji, dla których nie istnieje niejawna konwersja za pomocą wyrażenia Cast.</span><span class="sxs-lookup"><span data-stu-id="b7bc9-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="b7bc9-113">W poniższej tabeli przedstawiono te konwersje.</span><span class="sxs-lookup"><span data-stu-id="b7bc9-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="b7bc9-114">Jawne konwersje wskaźników</span><span class="sxs-lookup"><span data-stu-id="b7bc9-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="b7bc9-115">Z</span><span class="sxs-lookup"><span data-stu-id="b7bc9-115">From</span></span>|<span data-ttu-id="b7bc9-116">Zadanie</span><span class="sxs-lookup"><span data-stu-id="b7bc9-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="b7bc9-117">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="b7bc9-117">Any pointer type</span></span>|<span data-ttu-id="b7bc9-118">Dowolny inny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="b7bc9-118">Any other pointer type</span></span>|  
|<span data-ttu-id="b7bc9-119">bajty, Byte, Short, UShort, int, uint, Long lub ULONG</span><span class="sxs-lookup"><span data-stu-id="b7bc9-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="b7bc9-120">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="b7bc9-120">Any pointer type</span></span>|  
|<span data-ttu-id="b7bc9-121">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="b7bc9-121">Any pointer type</span></span>|<span data-ttu-id="b7bc9-122">bajty, Byte, Short, UShort, int, uint, Long lub ULONG</span><span class="sxs-lookup"><span data-stu-id="b7bc9-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b7bc9-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="b7bc9-123">Example</span></span>  
 <span data-ttu-id="b7bc9-124">W poniższym przykładzie wskaźnik do `int` jest konwertowany na wskaźnik do. `byte`</span><span class="sxs-lookup"><span data-stu-id="b7bc9-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="b7bc9-125">Zauważ, że wskaźnik wskazuje najniższy przyjmowany bajt zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b7bc9-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="b7bc9-126">Po kolejnym zwiększeniu wyniku do rozmiaru `int` (4 bajty) można wyświetlić pozostałe bajty zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b7bc9-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b7bc9-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7bc9-127">See also</span></span>

- [<span data-ttu-id="b7bc9-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b7bc9-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b7bc9-129">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="b7bc9-129">Pointer types</span></span>](./pointer-types.md)
- [<span data-ttu-id="b7bc9-130">Typy</span><span class="sxs-lookup"><span data-stu-id="b7bc9-130">Types</span></span>](../../language-reference/keywords/types.md)
- [<span data-ttu-id="b7bc9-131">unsafe</span><span class="sxs-lookup"><span data-stu-id="b7bc9-131">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="b7bc9-132">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b7bc9-132">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="b7bc9-133">stackalloc</span><span class="sxs-lookup"><span data-stu-id="b7bc9-133">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
