---
title: 'Porady: uzyskiwanie dostępu do elementu tablicy za pomocą wskaźnika - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 59765dbcad6c28cf2ad9f3df2052df19cafd08f1
ms.sourcegitcommit: 75567a3cb437009db55949c6092f4e77ed1a9da4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2019
ms.locfileid: "54307282"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a><span data-ttu-id="9aa5c-102">Porady: uzyskiwanie dostępu do elementu tablicy za pomocą wskaźnika (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="9aa5c-102">How to: access an array element with a pointer (C# Programming Guide)</span></span>

<span data-ttu-id="9aa5c-103">W niebezpiecznym kontekście uzyskujesz dostęp elementu w pamięci, używając dostępu do elementu wskaźnika, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9aa5c-103">In an unsafe context, you can access an element in memory by using pointer element access, as shown in the following example:</span></span>

```csharp
char* charPointer = stackalloc char[123];
for (int i = 65; i < 123; i++)
{
    charPointer[i] = (char)i; //access array elements
}
```

<span data-ttu-id="9aa5c-104">Wyrażenie w nawiasach kwadratowych musi umożliwiać niejawną konwersję na `int`, `uint`, `long`, lub `ulong`.</span><span class="sxs-lookup"><span data-stu-id="9aa5c-104">The expression in square brackets must be implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="9aa5c-105">Operacja `p[e]` jest odpowiednikiem `*(p+e)`.</span><span class="sxs-lookup"><span data-stu-id="9aa5c-105">The operation `p[e]` is equivalent to `*(p+e)`.</span></span> <span data-ttu-id="9aa5c-106">Podobnie jak C i C++, dostępu do elementu wskaźnik nie sprawdza obecności liczbach błędy.</span><span class="sxs-lookup"><span data-stu-id="9aa5c-106">Like C and C++, the pointer element access does not check for out-of-bounds errors.</span></span>

## <a name="example"></a><span data-ttu-id="9aa5c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="9aa5c-107">Example</span></span>

<span data-ttu-id="9aa5c-108">W tym przykładzie 123 lokalizacji pamięci są przydzielane do tablicy znaków `charPointer`.</span><span class="sxs-lookup"><span data-stu-id="9aa5c-108">In this example, 123 memory locations are allocated to a character array, `charPointer`.</span></span> <span data-ttu-id="9aa5c-109">Tablica jest używana do wyświetlania małe litery i wielkie litery w dwóch [dla](../../../csharp/language-reference/keywords/for.md) pętli.</span><span class="sxs-lookup"><span data-stu-id="9aa5c-109">The array is used to display the lowercase letters and the uppercase letters in two [for](../../../csharp/language-reference/keywords/for.md) loops.</span></span>

<span data-ttu-id="9aa5c-110">Należy zauważyć, że wyrażenie `charPointer[i]` jest równoważne wyrażeniu `*(charPointer + i)`, i ten sam efekt można uzyskać przy użyciu jednej z dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="9aa5c-110">Notice that the expression `charPointer[i]` is equivalent to the expression `*(charPointer + i)`, and you can obtain the same result by using either of the two expressions.</span></span>

[!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]

[!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]

<span data-ttu-id="9aa5c-111">**Wielkie litery:**</span><span class="sxs-lookup"><span data-stu-id="9aa5c-111">**Uppercase letters:**</span></span>  
<span data-ttu-id="9aa5c-112">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span><span class="sxs-lookup"><span data-stu-id="9aa5c-112">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span></span>  
<span data-ttu-id="9aa5c-113">**Małe litery:**</span><span class="sxs-lookup"><span data-stu-id="9aa5c-113">**Lowercase letters:**</span></span>  
<span data-ttu-id="9aa5c-114">**abcdefghijklmnopqrstuvwxyz**</span><span class="sxs-lookup"><span data-stu-id="9aa5c-114">**abcdefghijklmnopqrstuvwxyz**</span></span>  

## <a name="see-also"></a><span data-ttu-id="9aa5c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9aa5c-115">See also</span></span>

- [<span data-ttu-id="9aa5c-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9aa5c-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="9aa5c-117">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="9aa5c-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="9aa5c-118">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="9aa5c-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="9aa5c-119">Typy</span><span class="sxs-lookup"><span data-stu-id="9aa5c-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="9aa5c-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="9aa5c-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="9aa5c-121">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9aa5c-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="9aa5c-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="9aa5c-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
