---
title: using — Instrukcja (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: ec4849dda0f28ad1f0e0ebb2c493a33005107db4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500975"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="11f59-102">using — Instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="11f59-102">using Statement (C# Reference)</span></span>
<span data-ttu-id="11f59-103">Miejsce wygodnej składni, która zapewnia prawidłowe użycie <xref:System.IDisposable> obiektów.</span><span class="sxs-lookup"><span data-stu-id="11f59-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11f59-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="11f59-104">Example</span></span>  
 <span data-ttu-id="11f59-105">Poniższy przykład pokazuje, jak używać `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="11f59-105">The following example shows how to use the `using` statement.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="11f59-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11f59-106">Remarks</span></span>  
 <span data-ttu-id="11f59-107"><xref:System.IO.File> i <xref:System.Drawing.Font> to przykłady typów zarządzanych, uzyskujących dostęp do niezarządzanych zasobów (w tym dojścia do plików wielkości liter i konteksty urządzenia).</span><span class="sxs-lookup"><span data-stu-id="11f59-107"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="11f59-108">Istnieje wiele innych rodzajów zasobów niezarządzanych i typy biblioteki klas, które hermetyzują je.</span><span class="sxs-lookup"><span data-stu-id="11f59-108">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="11f59-109">Typy takie musi implementować <xref:System.IDisposable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="11f59-109">All such types must implement the <xref:System.IDisposable> interface.</span></span>  
  
<span data-ttu-id="11f59-110">Gdy okres istnienia `IDisposable` obiektu jest ograniczona do jednej metody, należy zadeklarować i Utwórz wystąpienie w `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="11f59-110">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="11f59-111">`using` Instrukcja wywołuje <xref:System.IDisposable.Dispose%2A> metody na obiekt w prawidłowy sposób i (Jeśli używasz tego jak pokazano wcześniej) powoduje także sam wykraczać poza zakres obiekt zaraz <xref:System.IDisposable.Dispose%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="11f59-111">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="11f59-112">W ramach `using` bloku, obiekt jest tylko do odczytu i nie można zmodyfikować ani ponownie przypisane.</span><span class="sxs-lookup"><span data-stu-id="11f59-112">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>  
  
 <span data-ttu-id="11f59-113">`using` Instrukcji zapewnia, że <xref:System.IDisposable.Dispose%2A> jest wywoływana, nawet jeśli wystąpi wyjątek w obrębie `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="11f59-113">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="11f59-114">Ten sam efekt można osiągnąć, umieszczając w obiekcie wewnątrz właściwości `try` bloku, a następnie wywołując <xref:System.IDisposable.Dispose%2A> w `finally` zablokować; w rzeczywistości jest to sposób, w jaki `using` instrukcji jest tłumaczony przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="11f59-114">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="11f59-115">W przykładzie kodu wcześniej rozwija następujący kod w czasie kompilacji (Uwaga: bardzo nawiasy klamrowe, aby utworzyć ograniczony zakres dla obiektu "):</span><span class="sxs-lookup"><span data-stu-id="11f59-115">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
 
 <span data-ttu-id="11f59-116">Aby uzyskać więcej informacji na temat `try` - `finally` poufności informacji, zobacz [try-finally](try-finally.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="11f59-116">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) topic.</span></span>
  
 <span data-ttu-id="11f59-117">Wiele wystąpień tego typu może być zadeklarowana w `using` instrukcji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="11f59-117">Multiple instances of a type can be declared in the `using` statement, as shown in the following example:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 <span data-ttu-id="11f59-118">Można utworzyć wystąpienia obiektu zasobu, a następnie przekaż zmienną `using` instrukcji, ale nie jest najlepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="11f59-118">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="11f59-119">W takim przypadku po liście kontroli `using` zablokować, pozostaje obiekt w zakresie, ale prawdopodobnie nie ma dostępu do niezarządzanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="11f59-119">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="11f59-120">Innymi słowy nie są w pełni inicjalizacji dłużej.</span><span class="sxs-lookup"><span data-stu-id="11f59-120">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="11f59-121">Jeśli spróbujesz użyć obiektu poza `using` zablokować ryzyka powoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="11f59-121">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="11f59-122">Z tego powodu zaleca ogólnie do utworzenia wystąpienia obiektu w `using` instrukcji i jego zakres, aby ograniczyć `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="11f59-122">For this reason, it's generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
<span data-ttu-id="11f59-123">Aby uzyskać więcej informacji na temat usuwania `IDisposable` obiekty, zobacz [używanie obiektów implementujących interfejs IDisposable](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="11f59-123">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="11f59-124">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="11f59-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="11f59-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11f59-125">See Also</span></span>

- [<span data-ttu-id="11f59-126">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="11f59-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="11f59-127">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="11f59-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="11f59-128">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="11f59-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="11f59-129">using, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="11f59-129">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
- [<span data-ttu-id="11f59-130">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="11f59-130">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
- [<span data-ttu-id="11f59-131">Używanie obiektów implementujących interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="11f59-131">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)  
- [<span data-ttu-id="11f59-132">Interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="11f59-132">IDisposable interface</span></span>](xref:System.IDisposable)
