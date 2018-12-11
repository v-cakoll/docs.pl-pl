---
title: 'Porady: inkrementacja i dekrementacja wskaźników (C# Programming Guide)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: c75432d88a1e96742573a6e69a4e035066a387c4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128339"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a><span data-ttu-id="b5b38-102">Porady: inkrementacja i dekrementacja wskaźników (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="b5b38-102">How to: increment and decrement pointers (C# Programming Guide)</span></span>

<span data-ttu-id="b5b38-103">Użyj inkrementacji i dekrementacji, `++` i `--`, aby zmienić lokalizację wskaźnika przez `sizeof(pointer-type)` wskaźnika typu `pointer-type*`.</span><span class="sxs-lookup"><span data-stu-id="b5b38-103">Use the increment and the decrement operators, `++` and `--`, to change the pointer location by `sizeof(pointer-type)` for a pointer of the type `pointer-type*`.</span></span> <span data-ttu-id="b5b38-104">Inkrementacja i dekrementacja wyrażeń mieć następującą formę:</span><span class="sxs-lookup"><span data-stu-id="b5b38-104">The increment and decrement expressions take the following form:</span></span>  
  
```csharp
++p;  
p++;  
--p;  
p--;  
```  
  
 <span data-ttu-id="b5b38-105">Operatory inkrementacji i dekrementacji może odnosić się do wskaźników dowolnego typu z wyjątkiem typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="b5b38-105">The increment and decrement operators can be applied to pointers of any type except the type `void*`.</span></span>  
  
 <span data-ttu-id="b5b38-106">Efektem zastosowania operatora inkrementacyjnego do wskaźnika typu `pointer-type*` jest dodanie `sizeof(pointer-type)` adres, który znajduje się w zmiennej wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="b5b38-106">The effect of applying the increment operator to a pointer of the type `pointer-type*` is to add `sizeof(pointer-type)` to the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="b5b38-107">Efektem zastosowania operatora dekrementacyjnego do wskaźnika typu `pointer-type*` ma Odejmij `sizeof(pointer-type)` z adresu, który znajduje się w zmiennej wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="b5b38-107">The effect of applying the decrement operator to a pointer of the type `pointer-type*` is to subtract `sizeof(pointer-type)` from the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="b5b38-108">Żadne wyjątki są generowane, gdy domena wskaźnik przepełnienie w operacji, a wynik zależy od implementacji.</span><span class="sxs-lookup"><span data-stu-id="b5b38-108">No exceptions are generated when the operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5b38-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="b5b38-109">Example</span></span>  
 <span data-ttu-id="b5b38-110">W tym przykładzie krok po kroku przez tablicę przez zwiększenie wskaźnika przez rozmiar `int`.</span><span class="sxs-lookup"><span data-stu-id="b5b38-110">In this example, you step through an array by incrementing the pointer by the size of `int`.</span></span> <span data-ttu-id="b5b38-111">Z każdego kroku możesz wyświetlić adres i zawartość elementu tablicy.</span><span class="sxs-lookup"><span data-stu-id="b5b38-111">With each step, you display the address and the content of the array element.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
<span data-ttu-id="b5b38-112">**Wartości: 0 @ adres: 12860272**
**wartości: 1 @ adres: 12860276**
**wartość: 2 @ adres: 12860280**
**wartość: 3 @ adresu : 12860284**
**12860288 @ adres: wartość: 4**</span><span class="sxs-lookup"><span data-stu-id="b5b38-112">**Value:0 @ Address:12860272**
**Value:1 @ Address:12860276**
**Value:2 @ Address:12860280**
**Value:3 @ Address:12860284**
**Value:4 @ Address:12860288**</span></span>

## <a name="see-also"></a><span data-ttu-id="b5b38-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5b38-113">See also</span></span>

- [<span data-ttu-id="b5b38-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b5b38-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b5b38-115">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="b5b38-115">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="b5b38-116">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="b5b38-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="b5b38-117">Manipulowanie wskaźnikami</span><span class="sxs-lookup"><span data-stu-id="b5b38-117">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="b5b38-118">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="b5b38-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="b5b38-119">Typy</span><span class="sxs-lookup"><span data-stu-id="b5b38-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="b5b38-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="b5b38-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="b5b38-121">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b5b38-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="b5b38-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="b5b38-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
- [<span data-ttu-id="b5b38-123">sizeof</span><span class="sxs-lookup"><span data-stu-id="b5b38-123">sizeof</span></span>](../../../csharp/language-reference/keywords/sizeof.md)
