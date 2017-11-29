---
title: "Porady: inkrementacja i dekrementacja wskaźników (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2c8efc6d0844d867ad6eebccf3bb22c03e6d5020
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a><span data-ttu-id="c67b6-102">Porady: inkrementacja i dekrementacja wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c67b6-102">How to: Increment and Decrement Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="c67b6-103">Użyj inkrementacji i dekrementacji, `++` i `--`, aby zmienić lokalizację wskaźnika przez [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) dla wskaźnika typu wskaźnika — typ *.</span><span class="sxs-lookup"><span data-stu-id="c67b6-103">Use the increment and the decrement operators, `++` and `--`, to change the pointer location by [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) for a pointer of type pointer-type*.</span></span> <span data-ttu-id="c67b6-104">Inkrementacja i dekrementacja wyrażeń mieć następującą formę:</span><span class="sxs-lookup"><span data-stu-id="c67b6-104">The increment and decrement expressions take the following form:</span></span>  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 <span data-ttu-id="c67b6-105">Operatory inkrementacji i dekrementacji można zastosować do wskaźników dowolnego typu, z wyjątkiem typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="c67b6-105">The increment and decrement operators can be applied to pointers of any type except the type `void*`.</span></span>  
  
 <span data-ttu-id="c67b6-106">Efekt zastosowania operatora inkrementacji do wskaźnika typu `pointer-type` jest dodanie [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) adres, który jest zawarty w zmiennej wskaźnikowej.</span><span class="sxs-lookup"><span data-stu-id="c67b6-106">The effect of applying the increment operator to a pointer of the type `pointer-type` is to add [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) to the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="c67b6-107">Skutek stosowania operator dekrementacji do wskaźnika typu `pointer-type` jest do odjęcia `sizeof` (`pointer-type`) z adresu, który jest zawarty w zmiennej wskaźnikowej.</span><span class="sxs-lookup"><span data-stu-id="c67b6-107">The effect of applying the decrement operator to a pointer of the type `pointer-type` is to subtract `sizeof` (`pointer-type`) from the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="c67b6-108">Żadne wyjątki są generowane, gdy domeny wskaźnika przepełnienie w operacji, a wynik zależy od implementacji.</span><span class="sxs-lookup"><span data-stu-id="c67b6-108">No exceptions are generated when the operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c67b6-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="c67b6-109">Example</span></span>  
 <span data-ttu-id="c67b6-110">W tym przykładzie można wykonywać krokowo tablicy przez zwiększanie wskaźnika przez rozmiar `int`.</span><span class="sxs-lookup"><span data-stu-id="c67b6-110">In this example, you step through an array by incrementing the pointer by the size of `int`.</span></span> <span data-ttu-id="c67b6-111">Z każdym kroku możesz wyświetlić adres i zawartość elementu tablicy.</span><span class="sxs-lookup"><span data-stu-id="c67b6-111">With each step, you display the address and the content of the array element.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
 <span data-ttu-id="c67b6-112">**Wartości: 0 @ adres: 12860272**</span><span class="sxs-lookup"><span data-stu-id="c67b6-112">**Value:0 @ Address:12860272**</span></span>  
<span data-ttu-id="c67b6-113">**Wartości: 1 @ adres: 12860276**</span><span class="sxs-lookup"><span data-stu-id="c67b6-113">**Value:1 @ Address:12860276**</span></span>  
<span data-ttu-id="c67b6-114">**Wartość: 2 @ adres: 12860280**</span><span class="sxs-lookup"><span data-stu-id="c67b6-114">**Value:2 @ Address:12860280**</span></span>  
<span data-ttu-id="c67b6-115">**Wartość: 3 @ adres: 12860284**</span><span class="sxs-lookup"><span data-stu-id="c67b6-115">**Value:3 @ Address:12860284**</span></span>  
<span data-ttu-id="c67b6-116">**Wartość: 4 @ adres: 12860288**</span><span class="sxs-lookup"><span data-stu-id="c67b6-116">**Value:4 @ Address:12860288**</span></span>   
## <a name="see-also"></a><span data-ttu-id="c67b6-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c67b6-117">See Also</span></span>  
 [<span data-ttu-id="c67b6-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c67b6-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c67b6-119">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="c67b6-119">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="c67b6-120">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="c67b6-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="c67b6-121">Manipulowanie wskaźnikami</span><span class="sxs-lookup"><span data-stu-id="c67b6-121">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [<span data-ttu-id="c67b6-122">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="c67b6-122">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="c67b6-123">Typy</span><span class="sxs-lookup"><span data-stu-id="c67b6-123">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="c67b6-124">unsafe</span><span class="sxs-lookup"><span data-stu-id="c67b6-124">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="c67b6-125">Fixed — instrukcja</span><span class="sxs-lookup"><span data-stu-id="c67b6-125">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="c67b6-126">stackalloc</span><span class="sxs-lookup"><span data-stu-id="c67b6-126">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
