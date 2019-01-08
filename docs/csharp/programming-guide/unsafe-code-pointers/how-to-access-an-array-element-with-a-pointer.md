---
title: Jak uzyskać dostęp do elementu tablicy za pomocą wskaźnika - C# Programming Guide
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 4f5d82e0ccdffcb694e3030aabe58b8da687a5e1
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084800"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a><span data-ttu-id="33b51-102">Jak uzyskać dostęp do elementu tablicy za pomocą wskaźnika (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="33b51-102">How to access an array element with a pointer (C# Programming Guide)</span></span>

<span data-ttu-id="33b51-103">W niebezpiecznym kontekście uzyskujesz dostęp elementu w pamięci, używając dostępu do elementu wskaźnika, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="33b51-103">In an unsafe context, you can access an element in memory by using pointer element access, as shown in the following example:</span></span>

```csharp
char* charPointer = stackalloc char[123];
for (int i = 65; i < 123; i++)
{
    charPointer[i] = (char)i; //access array elements
}
```

<span data-ttu-id="33b51-104">Wyrażenie w nawiasach kwadratowych musi umożliwiać niejawną konwersję na `int`, `uint`, `long`, lub `ulong`.</span><span class="sxs-lookup"><span data-stu-id="33b51-104">The expression in square brackets must be implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="33b51-105">Operacja `p[e]` jest odpowiednikiem `*(p+e)`.</span><span class="sxs-lookup"><span data-stu-id="33b51-105">The operation `p[e]` is equivalent to `*(p+e)`.</span></span> <span data-ttu-id="33b51-106">Podobnie jak C i C++, dostępu do elementu wskaźnik nie sprawdza obecności liczbach błędy.</span><span class="sxs-lookup"><span data-stu-id="33b51-106">Like C and C++, the pointer element access does not check for out-of-bounds errors.</span></span>

## <a name="example"></a><span data-ttu-id="33b51-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="33b51-107">Example</span></span>

<span data-ttu-id="33b51-108">W tym przykładzie 123 lokalizacji pamięci są przydzielane do tablicy znaków `charPointer`.</span><span class="sxs-lookup"><span data-stu-id="33b51-108">In this example, 123 memory locations are allocated to a character array, `charPointer`.</span></span> <span data-ttu-id="33b51-109">Tablica jest używana do wyświetlania małe litery i wielkie litery w dwóch [dla](../../../csharp/language-reference/keywords/for.md) pętli.</span><span class="sxs-lookup"><span data-stu-id="33b51-109">The array is used to display the lowercase letters and the uppercase letters in two [for](../../../csharp/language-reference/keywords/for.md) loops.</span></span>

<span data-ttu-id="33b51-110">Należy zauważyć, że wyrażenie `charPointer[i]` jest równoważne wyrażeniu `*(charPointer + i)`, i ten sam efekt można uzyskać przy użyciu jednej z dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="33b51-110">Notice that the expression `charPointer[i]` is equivalent to the expression `*(charPointer + i)`, and you can obtain the same result by using either of the two expressions.</span></span>

[!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]

[!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]

<span data-ttu-id="33b51-111">**Wielkie litery:**
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**
**małe litery:**
**abcdefghijklmnopqrstuvwxyz**</span><span class="sxs-lookup"><span data-stu-id="33b51-111">**Uppercase letters:**
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**
**Lowercase letters:**
**abcdefghijklmnopqrstuvwxyz**</span></span>

## <a name="see-also"></a><span data-ttu-id="33b51-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33b51-112">See also</span></span>

- [<span data-ttu-id="33b51-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="33b51-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="33b51-114">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="33b51-114">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="33b51-115">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="33b51-115">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="33b51-116">Typy</span><span class="sxs-lookup"><span data-stu-id="33b51-116">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="33b51-117">unsafe</span><span class="sxs-lookup"><span data-stu-id="33b51-117">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="33b51-118">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="33b51-118">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="33b51-119">stackalloc</span><span class="sxs-lookup"><span data-stu-id="33b51-119">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
