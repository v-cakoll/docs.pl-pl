---
title: "volatile (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1cefa39313c3c551e8d05fbc31e528b86c6888d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="volatile-c-reference"></a><span data-ttu-id="a101b-102">volatile (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a101b-102">volatile (C# Reference)</span></span>
<span data-ttu-id="a101b-103">`volatile` — Słowo kluczowe wskazuje, czy pole może zostać zmodyfikowany przez wiele wątków, które są wykonywane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="a101b-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="a101b-104">Pola, które są zadeklarowane `volatile` nie są objęte optymalizacje kompilatora, które przyjmuje dostępu przez jednego wątku.</span><span class="sxs-lookup"><span data-stu-id="a101b-104">Fields that are declared `volatile` are not subject to compiler optimizations that assume access by a single thread.</span></span> <span data-ttu-id="a101b-105">Dzięki temu, czy aktualną wartość znajduje się w polu przez cały czas.</span><span class="sxs-lookup"><span data-stu-id="a101b-105">This ensures that the most up-to-date value is present in the field at all times.</span></span>  
  
 <span data-ttu-id="a101b-106">`volatile` Modyfikator jest zwykle używany dla pola, który jest dostępny przez wiele wątków bez użycia [blokady](../../../csharp/language-reference/keywords/lock-statement.md) instrukcji do serializacji dostępu.</span><span class="sxs-lookup"><span data-stu-id="a101b-106">The `volatile` modifier is usually used for a field that is accessed by multiple threads without using the [lock](../../../csharp/language-reference/keywords/lock-statement.md) statement to serialize access.</span></span>  
  
 <span data-ttu-id="a101b-107">`volatile` — Słowo kluczowe może odnosić się do pól z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="a101b-107">The `volatile` keyword can be applied to fields of these types:</span></span>  
  
-   <span data-ttu-id="a101b-108">Typy referencyjne.</span><span class="sxs-lookup"><span data-stu-id="a101b-108">Reference types.</span></span>  
  
-   <span data-ttu-id="a101b-109">Typy wskaźnika (w niebezpiecznym kontekście).</span><span class="sxs-lookup"><span data-stu-id="a101b-109">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="a101b-110">Należy pamiętać, że chociaż sama wskaźnik może być nietrwałe, obiekt, który wskazuje nie.</span><span class="sxs-lookup"><span data-stu-id="a101b-110">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="a101b-111">Innymi słowy nie można zadeklarować "wskaźnik do volatile."</span><span class="sxs-lookup"><span data-stu-id="a101b-111">In other words, you cannot declare a "pointer to volatile."</span></span>  
  
-   <span data-ttu-id="a101b-112">Typy, takie jak sbyte, byte, short, ushort, int, uint, char, float i bool.</span><span class="sxs-lookup"><span data-stu-id="a101b-112">Types such as sbyte, byte, short, ushort, int, uint, char, float, and bool.</span></span>  
  
-   <span data-ttu-id="a101b-113">Typ wyliczeniowy z jednym z następujących typów podstawowych: byte, sbyte, short, ushort, int lub uint.</span><span class="sxs-lookup"><span data-stu-id="a101b-113">An enum type with one of the following base types: byte, sbyte, short, ushort, int, or uint.</span></span>  
  
-   <span data-ttu-id="a101b-114">Parametry typu ogólnego, znane jako typy referencyjne.</span><span class="sxs-lookup"><span data-stu-id="a101b-114">Generic type parameters known to be reference types.</span></span>  
  
-   <span data-ttu-id="a101b-115"><xref:System.IntPtr>i <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="a101b-115"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>  
  
 <span data-ttu-id="a101b-116">Volatile — słowo kluczowe można zastosować tylko do pól klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="a101b-116">The volatile keyword can only be applied to fields of a class or struct.</span></span> <span data-ttu-id="a101b-117">Nie można deklarować zmiennych lokalnych `volatile`.</span><span class="sxs-lookup"><span data-stu-id="a101b-117">Local variables cannot be declared `volatile`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a101b-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="a101b-118">Example</span></span>  
 <span data-ttu-id="a101b-119">Poniższy przykład przedstawia sposób zadeklarować zmiennej pole publiczne jako `volatile`.</span><span class="sxs-lookup"><span data-stu-id="a101b-119">The following example shows how to declare a public field variable as `volatile`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="a101b-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="a101b-120">Example</span></span>  
 <span data-ttu-id="a101b-121">W poniższym przykładzie pokazano, jak wątek pomocniczy lub procesu roboczego można tworzyć i używane do przetwarzania równolegle z podstawowym wątku.</span><span class="sxs-lookup"><span data-stu-id="a101b-121">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="a101b-122">Aby uzyskać ogólne informacje o wielowątkowości, zobacz [wątki](../../../standard/threading/index.md) i [wątki](../../programming-guide/concepts/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="a101b-122">For background information about multithreading, see [Threading](../../../standard/threading/index.md) and [Threading](../../programming-guide/concepts/threading/index.md).</span></span>  
  
 [!code-csharp[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="a101b-123">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a101b-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a101b-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a101b-124">See Also</span></span>  
 [<span data-ttu-id="a101b-125">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="a101b-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a101b-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a101b-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a101b-127">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="a101b-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="a101b-128">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="a101b-128">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
