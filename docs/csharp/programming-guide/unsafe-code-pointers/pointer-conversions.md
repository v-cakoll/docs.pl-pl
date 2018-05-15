---
title: Konwersje wskaźników (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: e0c3a409d76468a6e214a96e8bb326a9d906fe18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="83d91-102">Konwersje wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="83d91-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="83d91-103">W poniższej tabeli przedstawiono wstępnie zdefiniowane wskaźnika niejawne konwersje.</span><span class="sxs-lookup"><span data-stu-id="83d91-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="83d91-104">Niejawne konwersje może wystąpić w wielu sytuacjach, w tym instrukcje metody wywoływania i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="83d91-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="83d91-105">Wskaźnik niejawne konwersje</span><span class="sxs-lookup"><span data-stu-id="83d91-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="83d91-106">Z</span><span class="sxs-lookup"><span data-stu-id="83d91-106">From</span></span>|<span data-ttu-id="83d91-107">Do</span><span class="sxs-lookup"><span data-stu-id="83d91-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="83d91-108">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="83d91-108">Any pointer type</span></span>|<span data-ttu-id="83d91-109">void \*</span><span class="sxs-lookup"><span data-stu-id="83d91-109">void\*</span></span>|  
|<span data-ttu-id="83d91-110">null</span><span class="sxs-lookup"><span data-stu-id="83d91-110">null</span></span>|<span data-ttu-id="83d91-111">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="83d91-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="83d91-112">Konwersja jawna wskaźnika jest używany do wykonywania konwersji, dla których nie jest niejawna konwersja, używając wyrażenia rzutowania.</span><span class="sxs-lookup"><span data-stu-id="83d91-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="83d91-113">W poniższej tabeli przedstawiono te konwersji.</span><span class="sxs-lookup"><span data-stu-id="83d91-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="83d91-114">Konwersje jawne wskaźników</span><span class="sxs-lookup"><span data-stu-id="83d91-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="83d91-115">Z</span><span class="sxs-lookup"><span data-stu-id="83d91-115">From</span></span>|<span data-ttu-id="83d91-116">Do</span><span class="sxs-lookup"><span data-stu-id="83d91-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="83d91-117">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="83d91-117">Any pointer type</span></span>|<span data-ttu-id="83d91-118">Innego typu wskaźnika</span><span class="sxs-lookup"><span data-stu-id="83d91-118">Any other pointer type</span></span>|  
|<span data-ttu-id="83d91-119">sbyte, byte, short, ushort, int, uint, long lub ulong</span><span class="sxs-lookup"><span data-stu-id="83d91-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="83d91-120">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="83d91-120">Any pointer type</span></span>|  
|<span data-ttu-id="83d91-121">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="83d91-121">Any pointer type</span></span>|<span data-ttu-id="83d91-122">sbyte, byte, short, ushort, int, uint, long lub ulong</span><span class="sxs-lookup"><span data-stu-id="83d91-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="83d91-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="83d91-123">Example</span></span>  
 <span data-ttu-id="83d91-124">W poniższym przykładzie wskaźnik do `int` jest konwertowana na wskaźnik do `byte`.</span><span class="sxs-lookup"><span data-stu-id="83d91-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="83d91-125">Zwróć uwagę, że wskaźnik wskazuje najniższa bajtów zaadresowane zmiennej.</span><span class="sxs-lookup"><span data-stu-id="83d91-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="83d91-126">Gdy kolejno inkrementacji wyniku do rozmiaru `int` (4 bajty), można wyświetlić Pozostała liczba bajtów zmiennej.</span><span class="sxs-lookup"><span data-stu-id="83d91-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="83d91-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83d91-127">See Also</span></span>  
 [<span data-ttu-id="83d91-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="83d91-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="83d91-129">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="83d91-129">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="83d91-130">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="83d91-130">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="83d91-131">Typy</span><span class="sxs-lookup"><span data-stu-id="83d91-131">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="83d91-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="83d91-132">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="83d91-133">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="83d91-133">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="83d91-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="83d91-134">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
