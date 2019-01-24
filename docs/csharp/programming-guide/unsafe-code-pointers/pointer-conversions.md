---
title: Konwersje wskaźników - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 8fa1c1442d146c9d2fbdb2fa969b2e29d7ef765d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498310"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="40b9c-102">Konwersje wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="40b9c-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="40b9c-103">W poniższej tabeli przedstawiono konwersje wskaźnika niejawne wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="40b9c-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="40b9c-104">Niejawne konwersje mogą wystąpić w wielu sytuacjach, w tym metody wywoływania i przypisania poufności informacji.</span><span class="sxs-lookup"><span data-stu-id="40b9c-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="40b9c-105">Konwersje niejawne wskaźników</span><span class="sxs-lookup"><span data-stu-id="40b9c-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="40b9c-106">Z</span><span class="sxs-lookup"><span data-stu-id="40b9c-106">From</span></span>|<span data-ttu-id="40b9c-107">Zadanie</span><span class="sxs-lookup"><span data-stu-id="40b9c-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="40b9c-108">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="40b9c-108">Any pointer type</span></span>|<span data-ttu-id="40b9c-109">void \*</span><span class="sxs-lookup"><span data-stu-id="40b9c-109">void\*</span></span>|  
|<span data-ttu-id="40b9c-110">null</span><span class="sxs-lookup"><span data-stu-id="40b9c-110">null</span></span>|<span data-ttu-id="40b9c-111">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="40b9c-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="40b9c-112">Konwersja jawna wskaźnika jest używany do wykonywania konwersji, dla których istnieje niejawna konwersja, za pomocą wyrażenia rzutowania.</span><span class="sxs-lookup"><span data-stu-id="40b9c-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="40b9c-113">W poniższej tabeli przedstawiono takiej konwersji.</span><span class="sxs-lookup"><span data-stu-id="40b9c-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="40b9c-114">Konwersje jawne wskaźników</span><span class="sxs-lookup"><span data-stu-id="40b9c-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="40b9c-115">Z</span><span class="sxs-lookup"><span data-stu-id="40b9c-115">From</span></span>|<span data-ttu-id="40b9c-116">Zadanie</span><span class="sxs-lookup"><span data-stu-id="40b9c-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="40b9c-117">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="40b9c-117">Any pointer type</span></span>|<span data-ttu-id="40b9c-118">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="40b9c-118">Any other pointer type</span></span>|  
|<span data-ttu-id="40b9c-119">sbyte, bajt, short, ushort, int, uint, long lub ulong</span><span class="sxs-lookup"><span data-stu-id="40b9c-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="40b9c-120">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="40b9c-120">Any pointer type</span></span>|  
|<span data-ttu-id="40b9c-121">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="40b9c-121">Any pointer type</span></span>|<span data-ttu-id="40b9c-122">sbyte, bajt, short, ushort, int, uint, long lub ulong</span><span class="sxs-lookup"><span data-stu-id="40b9c-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="40b9c-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="40b9c-123">Example</span></span>  
 <span data-ttu-id="40b9c-124">W poniższym przykładzie, wskaźnik do `int` jest konwertowana na wskaźnik do `byte`.</span><span class="sxs-lookup"><span data-stu-id="40b9c-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="40b9c-125">Należy zauważyć, że wskaźnik wskazuje najniższą zaadresowane bajt zmiennej.</span><span class="sxs-lookup"><span data-stu-id="40b9c-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="40b9c-126">Gdy kolejno inkrementacji wyniku przy rozmiarze `int` (4 bajtów), można wyświetlić pozostałe bajty zmiennej.</span><span class="sxs-lookup"><span data-stu-id="40b9c-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="40b9c-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40b9c-127">See also</span></span>

- [<span data-ttu-id="40b9c-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="40b9c-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="40b9c-129">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="40b9c-129">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="40b9c-130">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="40b9c-130">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="40b9c-131">Typy</span><span class="sxs-lookup"><span data-stu-id="40b9c-131">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="40b9c-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="40b9c-132">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="40b9c-133">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="40b9c-133">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="40b9c-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="40b9c-134">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
