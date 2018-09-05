---
title: Konwersje wskaźników (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: db809fa9e086351184adcac43d67f53e9456894c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43554138"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="8ce25-102">Konwersje wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="8ce25-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="8ce25-103">W poniższej tabeli przedstawiono konwersje wskaźnika niejawne wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="8ce25-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="8ce25-104">Niejawne konwersje mogą wystąpić w wielu sytuacjach, w tym metody wywoływania i przypisania poufności informacji.</span><span class="sxs-lookup"><span data-stu-id="8ce25-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="8ce25-105">Konwersje niejawne wskaźników</span><span class="sxs-lookup"><span data-stu-id="8ce25-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="8ce25-106">Z</span><span class="sxs-lookup"><span data-stu-id="8ce25-106">From</span></span>|<span data-ttu-id="8ce25-107">Zadanie</span><span class="sxs-lookup"><span data-stu-id="8ce25-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="8ce25-108">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="8ce25-108">Any pointer type</span></span>|<span data-ttu-id="8ce25-109">void \*</span><span class="sxs-lookup"><span data-stu-id="8ce25-109">void\*</span></span>|  
|<span data-ttu-id="8ce25-110">null</span><span class="sxs-lookup"><span data-stu-id="8ce25-110">null</span></span>|<span data-ttu-id="8ce25-111">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="8ce25-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="8ce25-112">Konwersja jawna wskaźnika jest używany do wykonywania konwersji, dla których istnieje niejawna konwersja, za pomocą wyrażenia rzutowania.</span><span class="sxs-lookup"><span data-stu-id="8ce25-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="8ce25-113">W poniższej tabeli przedstawiono takiej konwersji.</span><span class="sxs-lookup"><span data-stu-id="8ce25-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="8ce25-114">Konwersje jawne wskaźników</span><span class="sxs-lookup"><span data-stu-id="8ce25-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="8ce25-115">Z</span><span class="sxs-lookup"><span data-stu-id="8ce25-115">From</span></span>|<span data-ttu-id="8ce25-116">Zadanie</span><span class="sxs-lookup"><span data-stu-id="8ce25-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="8ce25-117">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="8ce25-117">Any pointer type</span></span>|<span data-ttu-id="8ce25-118">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="8ce25-118">Any other pointer type</span></span>|  
|<span data-ttu-id="8ce25-119">sbyte, bajt, short, ushort, int, uint, long lub ulong</span><span class="sxs-lookup"><span data-stu-id="8ce25-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="8ce25-120">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="8ce25-120">Any pointer type</span></span>|  
|<span data-ttu-id="8ce25-121">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="8ce25-121">Any pointer type</span></span>|<span data-ttu-id="8ce25-122">sbyte, bajt, short, ushort, int, uint, long lub ulong</span><span class="sxs-lookup"><span data-stu-id="8ce25-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8ce25-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ce25-123">Example</span></span>  
 <span data-ttu-id="8ce25-124">W poniższym przykładzie, wskaźnik do `int` jest konwertowana na wskaźnik do `byte`.</span><span class="sxs-lookup"><span data-stu-id="8ce25-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="8ce25-125">Należy zauważyć, że wskaźnik wskazuje najniższą zaadresowane bajt zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8ce25-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="8ce25-126">Gdy kolejno inkrementacji wyniku przy rozmiarze `int` (4 bajtów), można wyświetlić pozostałe bajty zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8ce25-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8ce25-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ce25-127">See Also</span></span>

- [<span data-ttu-id="8ce25-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8ce25-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="8ce25-129">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="8ce25-129">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="8ce25-130">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="8ce25-130">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="8ce25-131">Typy</span><span class="sxs-lookup"><span data-stu-id="8ce25-131">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="8ce25-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="8ce25-132">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="8ce25-133">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8ce25-133">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="8ce25-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="8ce25-134">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
