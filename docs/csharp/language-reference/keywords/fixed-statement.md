---
title: fixed — Instrukcja (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 13633e71c863b075eede41c9a18419d65350bdb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="6287d-102">fixed — Instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6287d-102">fixed Statement (C# Reference)</span></span>
<span data-ttu-id="6287d-103">`fixed` Instrukcji uniemożliwia przemieszczanie zmienną ruchomy moduł garbage collector.</span><span class="sxs-lookup"><span data-stu-id="6287d-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="6287d-104">`fixed` Instrukcji jest dozwolona tylko w [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="6287d-104">The `fixed` statement is only permitted in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="6287d-105">`Fixed`można również utworzyć [stały rozmiar buforów](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="6287d-105">`Fixed` can also be used to create [fixed size buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 <span data-ttu-id="6287d-106">`fixed` Instrukcja ustawia wskaźnik zarządzanych zmienną i "numerów PIN" zmiennej podczas wykonywania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6287d-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="6287d-107">Bez `fixed`, wskaźników do zmiennych zarządzanych ruchome będzie znikomym ponieważ wyrzucanie elementów bezużytecznych można przenosić zmienne nieprzewidywalny.</span><span class="sxs-lookup"><span data-stu-id="6287d-107">Without `fixed`, pointers to movable managed variables would be of little use since garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="6287d-108">Kompilator języka C# tylko można przypisać wskaźnik do zmiennej zarządzanych w `fixed` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6287d-108">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]  
  
 <span data-ttu-id="6287d-109">Wskaźnik można zainicjować za pomocą tablicy, ciąg, buforu o stałym rozmiarze lub adresu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6287d-109">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="6287d-110">Poniższy przykład przedstawia użycie zmiennej adresów, tablic i ciągów.</span><span class="sxs-lookup"><span data-stu-id="6287d-110">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="6287d-111">Aby uzyskać więcej informacji na temat bufory o ustalonym rozmiarze, zobacz [buforów o rozmiarze stałym](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="6287d-111">For more information about fixed-size buffers, see [Fixed Size Buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]  
  
 <span data-ttu-id="6287d-112">Należy zainicjować wielu wskaźników, jak długo będą tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="6287d-112">You can initialize multiple pointers, as long as they are all of the same type.</span></span>  
  
```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```
  
 <span data-ttu-id="6287d-113">Aby zainicjować wskaźników różnych typów, po prostu zagnieździć `fixed` instrukcje, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6287d-113">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]  
  
 <span data-ttu-id="6287d-114">Po wykonaniu kodu w instrukcji zmiennych przypiętych są odpiąć i wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6287d-114">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="6287d-115">W związku z tym nie wskazują na tych zmiennych poza `fixed` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6287d-115">Therefore, do not point to those variables outside the `fixed` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6287d-116">Nie można modyfikować wskaźników zainicjowany w instrukcjach "fixed".</span><span class="sxs-lookup"><span data-stu-id="6287d-116">Pointers initialized in fixed statements cannot be modified.</span></span>  
  
 <span data-ttu-id="6287d-117">W trybie bezpiecznym można przydzielić pamięci na stosie, w którym nie podlega wyrzucanie elementów bezużytecznych i dlatego nie trzeba przypięty.</span><span class="sxs-lookup"><span data-stu-id="6287d-117">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="6287d-118">Aby uzyskać więcej informacji, zobacz [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="6287d-118">For more information, see [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6287d-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="6287d-119">Example</span></span>  
 [!code-csharp[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6287d-120">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6287d-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6287d-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6287d-121">See Also</span></span>  
 [<span data-ttu-id="6287d-122">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="6287d-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6287d-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6287d-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6287d-124">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6287d-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6287d-125">unsafe</span><span class="sxs-lookup"><span data-stu-id="6287d-125">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="6287d-126">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="6287d-126">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
