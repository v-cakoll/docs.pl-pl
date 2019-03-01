---
title: Konwersje wskaźników - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 91be48aa2ca64b152af3dc3f33c713bf4adac0c7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968390"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="1d12d-102">Konwersje wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="1d12d-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="1d12d-103">W poniższej tabeli przedstawiono konwersje wskaźnika niejawne wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="1d12d-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="1d12d-104">Niejawne konwersje mogą wystąpić w wielu sytuacjach, w tym metody wywoływania i przypisania poufności informacji.</span><span class="sxs-lookup"><span data-stu-id="1d12d-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="1d12d-105">Konwersje niejawne wskaźników</span><span class="sxs-lookup"><span data-stu-id="1d12d-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="1d12d-106">Z</span><span class="sxs-lookup"><span data-stu-id="1d12d-106">From</span></span>|<span data-ttu-id="1d12d-107">Zadanie</span><span class="sxs-lookup"><span data-stu-id="1d12d-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="1d12d-108">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="1d12d-108">Any pointer type</span></span>|<span data-ttu-id="1d12d-109">void \*</span><span class="sxs-lookup"><span data-stu-id="1d12d-109">void\*</span></span>|  
|<span data-ttu-id="1d12d-110">wartość null</span><span class="sxs-lookup"><span data-stu-id="1d12d-110">null</span></span>|<span data-ttu-id="1d12d-111">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="1d12d-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="1d12d-112">Konwersja jawna wskaźnika jest używany do wykonywania konwersji, dla których istnieje niejawna konwersja, za pomocą wyrażenia rzutowania.</span><span class="sxs-lookup"><span data-stu-id="1d12d-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="1d12d-113">W poniższej tabeli przedstawiono takiej konwersji.</span><span class="sxs-lookup"><span data-stu-id="1d12d-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="1d12d-114">Konwersje jawne wskaźników</span><span class="sxs-lookup"><span data-stu-id="1d12d-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="1d12d-115">Z</span><span class="sxs-lookup"><span data-stu-id="1d12d-115">From</span></span>|<span data-ttu-id="1d12d-116">Zadanie</span><span class="sxs-lookup"><span data-stu-id="1d12d-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="1d12d-117">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="1d12d-117">Any pointer type</span></span>|<span data-ttu-id="1d12d-118">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="1d12d-118">Any other pointer type</span></span>|  
|<span data-ttu-id="1d12d-119">sbyte, bajt, short, ushort, int, uint, long lub ulong</span><span class="sxs-lookup"><span data-stu-id="1d12d-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="1d12d-120">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="1d12d-120">Any pointer type</span></span>|  
|<span data-ttu-id="1d12d-121">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="1d12d-121">Any pointer type</span></span>|<span data-ttu-id="1d12d-122">sbyte, bajt, short, ushort, int, uint, long lub ulong</span><span class="sxs-lookup"><span data-stu-id="1d12d-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1d12d-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d12d-123">Example</span></span>  
 <span data-ttu-id="1d12d-124">W poniższym przykładzie, wskaźnik do `int` jest konwertowana na wskaźnik do `byte`.</span><span class="sxs-lookup"><span data-stu-id="1d12d-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="1d12d-125">Należy zauważyć, że wskaźnik wskazuje najniższą zaadresowane bajt zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1d12d-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="1d12d-126">Gdy kolejno inkrementacji wyniku przy rozmiarze `int` (4 bajtów), można wyświetlić pozostałe bajty zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1d12d-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="1d12d-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d12d-127">See also</span></span>

- [<span data-ttu-id="1d12d-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1d12d-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="1d12d-129">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="1d12d-129">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="1d12d-130">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="1d12d-130">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="1d12d-131">Typy</span><span class="sxs-lookup"><span data-stu-id="1d12d-131">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="1d12d-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="1d12d-132">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="1d12d-133">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1d12d-133">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="1d12d-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="1d12d-134">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
