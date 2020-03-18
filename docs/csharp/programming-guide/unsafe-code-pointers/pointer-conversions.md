---
title: Konwersje wskaźnika — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 517166331d2bcf73132269ce2adcf68d5f60b4fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76745364"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="b728c-102">Konwersje wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="b728c-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="b728c-103">W poniższej tabeli przedstawiono wstępnie zdefiniowane niejawne konwersje wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="b728c-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="b728c-104">Konwersje niejawne mogą wystąpić w wielu sytuacjach, w tym wywoływania metody i instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="b728c-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="b728c-105">Niejawne konwersje wskaźnika</span><span class="sxs-lookup"><span data-stu-id="b728c-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="b728c-106">Z</span><span class="sxs-lookup"><span data-stu-id="b728c-106">From</span></span>|<span data-ttu-id="b728c-107">Do</span><span class="sxs-lookup"><span data-stu-id="b728c-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="b728c-108">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="b728c-108">Any pointer type</span></span>|<span data-ttu-id="b728c-109">nieważne\*</span><span class="sxs-lookup"><span data-stu-id="b728c-109">void\*</span></span>|  
|<span data-ttu-id="b728c-110">null</span><span class="sxs-lookup"><span data-stu-id="b728c-110">null</span></span>|<span data-ttu-id="b728c-111">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="b728c-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="b728c-112">Jawna konwersja wskaźnika służy do wykonywania konwersji, dla których nie ma konwersji niejawnych, przy użyciu wyrażenia rzutowania.</span><span class="sxs-lookup"><span data-stu-id="b728c-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="b728c-113">W poniższej tabeli przedstawiono te konwersje.</span><span class="sxs-lookup"><span data-stu-id="b728c-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="b728c-114">Jawne konwersje wskaźnika</span><span class="sxs-lookup"><span data-stu-id="b728c-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="b728c-115">Z</span><span class="sxs-lookup"><span data-stu-id="b728c-115">From</span></span>|<span data-ttu-id="b728c-116">Do</span><span class="sxs-lookup"><span data-stu-id="b728c-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="b728c-117">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="b728c-117">Any pointer type</span></span>|<span data-ttu-id="b728c-118">Każdy inny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="b728c-118">Any other pointer type</span></span>|  
|<span data-ttu-id="b728c-119">sbajt, bajt, krótki, ushort, int, uint, długi lub ulong</span><span class="sxs-lookup"><span data-stu-id="b728c-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="b728c-120">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="b728c-120">Any pointer type</span></span>|  
|<span data-ttu-id="b728c-121">Dowolny typ wskaźnika</span><span class="sxs-lookup"><span data-stu-id="b728c-121">Any pointer type</span></span>|<span data-ttu-id="b728c-122">sbajt, bajt, krótki, ushort, int, uint, długi lub ulong</span><span class="sxs-lookup"><span data-stu-id="b728c-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b728c-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="b728c-123">Example</span></span>  
 <span data-ttu-id="b728c-124">W poniższym przykładzie wskaźnik `int` do jest konwertowany `byte`na wskaźnik do .</span><span class="sxs-lookup"><span data-stu-id="b728c-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="b728c-125">Należy zauważyć, że wskaźnik wskazuje najniższy bajt adresowany zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b728c-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="b728c-126">Podczas sukcesywnego zwiększania wyniku, do rozmiaru `int` (4 bajty), można wyświetlić pozostałe bajty zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b728c-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b728c-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b728c-127">See also</span></span>

- [<span data-ttu-id="b728c-128">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="b728c-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b728c-129">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="b728c-129">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="b728c-130">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="b728c-130">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="b728c-131">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="b728c-131">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="b728c-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="b728c-132">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="b728c-133">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b728c-133">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="b728c-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="b728c-134">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
