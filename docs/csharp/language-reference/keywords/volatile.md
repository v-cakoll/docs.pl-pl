---
title: volatile (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: be7e081b18702710c00b5b86a9bc152800f0cf3d
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43253170"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="63518-102">volatile (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="63518-102">volatile (C# Reference)</span></span>
<span data-ttu-id="63518-103">`volatile` — Słowo kluczowe wskazuje, że pola mogą zostać zmodyfikowane przez wiele wątków, które są wykonywane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="63518-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="63518-104">Pola, które są zadeklarowane `volatile` nie są objęte optymalizacje kompilatora, które zakładają dostępu przez jednego wątku.</span><span class="sxs-lookup"><span data-stu-id="63518-104">Fields that are declared `volatile` are not subject to compiler optimizations that assume access by a single thread.</span></span> <span data-ttu-id="63518-105">Te ograniczenia upewnij się, że wszystkie wątki będzie przestrzegać volatile zapisów wykonywane przez inny wątek, w kolejności, w którym zostały wykonane.</span><span class="sxs-lookup"><span data-stu-id="63518-105">These restrictions ensure that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="63518-106">Nie ma żadnej gwarancji, pojedynczy całkowita kolejności volatile zapisów wyświetlanego ze wszystkich wątków wykonania.</span><span class="sxs-lookup"><span data-stu-id="63518-106">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>  
  
 <span data-ttu-id="63518-107">`volatile` Modyfikator jest zwykle używany dla pola, która jest dostępna w wielu wątkach, bez użycia [blokady](../../../csharp/language-reference/keywords/lock-statement.md) instrukcję, aby serializować dostępu.</span><span class="sxs-lookup"><span data-stu-id="63518-107">The `volatile` modifier is usually used for a field that is accessed by multiple threads without using the [lock](../../../csharp/language-reference/keywords/lock-statement.md) statement to serialize access.</span></span>  
  
 <span data-ttu-id="63518-108">`volatile` — Słowo kluczowe mogą być stosowane do pól z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="63518-108">The `volatile` keyword can be applied to fields of these types:</span></span>  
  
-   <span data-ttu-id="63518-109">Typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="63518-109">Reference types.</span></span>  
  
-   <span data-ttu-id="63518-110">Typy wskaźników (w niebezpiecznym kontekście).</span><span class="sxs-lookup"><span data-stu-id="63518-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="63518-111">Należy pamiętać, że chociaż wskaźnika, sama może być nietrwałe, obiekt, który wskazuje nie może.</span><span class="sxs-lookup"><span data-stu-id="63518-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="63518-112">Innymi słowy nie można zadeklarować "wskaźnik volatile."</span><span class="sxs-lookup"><span data-stu-id="63518-112">In other words, you cannot declare a "pointer to volatile."</span></span>  
  
-   <span data-ttu-id="63518-113">Typy takie jak sbyte, byte, short, ushort, int, uint, char, float i bool.</span><span class="sxs-lookup"><span data-stu-id="63518-113">Types such as sbyte, byte, short, ushort, int, uint, char, float, and bool.</span></span>  
  
-   <span data-ttu-id="63518-114">Typ wyliczeniowy z jednym z następujących typów podstawowych: byte, sbyte, short, ushort, int lub uint.</span><span class="sxs-lookup"><span data-stu-id="63518-114">An enum type with one of the following base types: byte, sbyte, short, ushort, int, or uint.</span></span>  
  
-   <span data-ttu-id="63518-115">Parametry typu ogólnego, znane jako typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="63518-115">Generic type parameters known to be reference types.</span></span>  
  
-   <span data-ttu-id="63518-116"><xref:System.IntPtr> i <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="63518-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>  
  
 <span data-ttu-id="63518-117">Volatile — słowo kluczowe będzie stosowany tylko do pól klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="63518-117">The volatile keyword can only be applied to fields of a class or struct.</span></span> <span data-ttu-id="63518-118">Nie można zadeklarować zmienne lokalne `volatile`.</span><span class="sxs-lookup"><span data-stu-id="63518-118">Local variables cannot be declared `volatile`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63518-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="63518-119">Example</span></span>  
 <span data-ttu-id="63518-120">Poniższy przykład pokazuje sposób deklarowania zmiennej pole publiczne `volatile`.</span><span class="sxs-lookup"><span data-stu-id="63518-120">The following example shows how to declare a public field variable as `volatile`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="63518-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="63518-121">Example</span></span>  
 <span data-ttu-id="63518-122">Poniższy przykład pokazuje, jak wątek wiadomości pomocniczych lub procesu roboczego można tworzyć i używany do wykonywania przetwarzania równolegle z wątku głównego.</span><span class="sxs-lookup"><span data-stu-id="63518-122">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="63518-123">Aby uzyskać ogólne informacje o wielowątkowości, zobacz [zarządzana wątkowość](../../../standard/threading/index.md) i [wątki (C#)](../../programming-guide/concepts/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="63518-123">For background information about multithreading, see [Managed Threading](../../../standard/threading/index.md) and [Threading (C#)](../../programming-guide/concepts/threading/index.md).</span></span>  
  
 [!code-csharp[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="63518-124">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="63518-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="63518-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63518-125">See Also</span></span>

- [<span data-ttu-id="63518-126">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="63518-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="63518-127">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="63518-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="63518-128">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="63518-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="63518-129">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="63518-129">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
