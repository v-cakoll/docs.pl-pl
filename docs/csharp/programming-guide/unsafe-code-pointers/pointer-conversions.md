---
title: Konwersje wskaźników - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 3cef2f2d2af2d285504daea14aa57c55b9e9a21b
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833457"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="e6882-102">Konwersje wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="e6882-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="e6882-103">W poniższej tabeli przedstawiono konwersje wskaźnika niejawne wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="e6882-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="e6882-104">Niejawne konwersje mogą wystąpić w wielu sytuacjach, w tym metody wywoływania i przypisania poufności informacji.</span><span class="sxs-lookup"><span data-stu-id="e6882-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="e6882-105">Konwersje niejawne wskaźników</span><span class="sxs-lookup"><span data-stu-id="e6882-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="e6882-106">Z</span><span class="sxs-lookup"><span data-stu-id="e6882-106">From</span></span>|<span data-ttu-id="e6882-107">Zadanie</span><span class="sxs-lookup"><span data-stu-id="e6882-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="e6882-108">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="e6882-108">Any pointer type</span></span>|<span data-ttu-id="e6882-109">void \*</span><span class="sxs-lookup"><span data-stu-id="e6882-109">void\*</span></span>|  
|<span data-ttu-id="e6882-110">wartość null</span><span class="sxs-lookup"><span data-stu-id="e6882-110">null</span></span>|<span data-ttu-id="e6882-111">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="e6882-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="e6882-112">Konwersja jawna wskaźnika jest używany do wykonywania konwersji, dla których istnieje niejawna konwersja, za pomocą wyrażenia rzutowania.</span><span class="sxs-lookup"><span data-stu-id="e6882-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="e6882-113">W poniższej tabeli przedstawiono takiej konwersji.</span><span class="sxs-lookup"><span data-stu-id="e6882-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="e6882-114">Konwersje jawne wskaźników</span><span class="sxs-lookup"><span data-stu-id="e6882-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="e6882-115">Z</span><span class="sxs-lookup"><span data-stu-id="e6882-115">From</span></span>|<span data-ttu-id="e6882-116">Zadanie</span><span class="sxs-lookup"><span data-stu-id="e6882-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="e6882-117">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="e6882-117">Any pointer type</span></span>|<span data-ttu-id="e6882-118">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="e6882-118">Any other pointer type</span></span>|  
|<span data-ttu-id="e6882-119">sbyte, bajt, short, ushort, int, uint, long lub ulong</span><span class="sxs-lookup"><span data-stu-id="e6882-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="e6882-120">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="e6882-120">Any pointer type</span></span>|  
|<span data-ttu-id="e6882-121">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="e6882-121">Any pointer type</span></span>|<span data-ttu-id="e6882-122">sbyte, bajt, short, ushort, int, uint, long lub ulong</span><span class="sxs-lookup"><span data-stu-id="e6882-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e6882-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="e6882-123">Example</span></span>  
 <span data-ttu-id="e6882-124">W poniższym przykładzie, wskaźnik do `int` jest konwertowana na wskaźnik do `byte`.</span><span class="sxs-lookup"><span data-stu-id="e6882-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="e6882-125">Należy zauważyć, że wskaźnik wskazuje najniższą zaadresowane bajt zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e6882-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="e6882-126">Gdy kolejno inkrementacji wyniku przy rozmiarze `int` (4 bajtów), można wyświetlić pozostałe bajty zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e6882-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="e6882-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6882-127">See also</span></span>

- [<span data-ttu-id="e6882-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e6882-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e6882-129">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="e6882-129">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="e6882-130">Typy</span><span class="sxs-lookup"><span data-stu-id="e6882-130">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="e6882-131">unsafe</span><span class="sxs-lookup"><span data-stu-id="e6882-131">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="e6882-132">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e6882-132">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="e6882-133">stackalloc</span><span class="sxs-lookup"><span data-stu-id="e6882-133">stackalloc</span></span>](../../../csharp/language-reference/operators/stackalloc.md)
