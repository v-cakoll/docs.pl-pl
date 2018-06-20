---
title: using — Instrukcja (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 7bf9138721ecee63c65c2e39922aee96b1dfaa41
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208378"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="730c5-102">using — Instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="730c5-102">using Statement (C# Reference)</span></span>
<span data-ttu-id="730c5-103">Umożliwia wygodne składnię, która zapewnia prawidłowe użycie <xref:System.IDisposable> obiektów.</span><span class="sxs-lookup"><span data-stu-id="730c5-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="730c5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="730c5-104">Example</span></span>  
 <span data-ttu-id="730c5-105">Poniższy przykład przedstawia użycie `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="730c5-105">The following example shows how to use the `using` statement.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="730c5-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="730c5-106">Remarks</span></span>  
 <span data-ttu-id="730c5-107"><xref:System.IO.File> i <xref:System.Drawing.Font> przedstawiono przykładowe typy zarządzane, które uzyskują dostęp do zasobów niezarządzanych (w tym dojścia do plików w przypadku i konteksty urządzenia).</span><span class="sxs-lookup"><span data-stu-id="730c5-107"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="730c5-108">Istnieje wiele rodzajów zasoby niezarządzane i klasy biblioteki typów, które hermetyzują je.</span><span class="sxs-lookup"><span data-stu-id="730c5-108">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="730c5-109">Takich typów musi implementować <xref:System.IDisposable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="730c5-109">All such types must implement the <xref:System.IDisposable> interface.</span></span>  
  
<span data-ttu-id="730c5-110">Jeśli okres istnienia `IDisposable` obiektu jest ograniczony do pojedynczej metody, należy zadeklarować i utworzyć w `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="730c5-110">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="730c5-111">`using` Wywołania instrukcji <xref:System.IDisposable.Dispose%2A> metody dla obiekt w prawidłowy sposób i (gdy jest używany jak pokazano wcześniej) powoduje także obiekt, aby znaleźć poza zakresem natychmiast <xref:System.IDisposable.Dispose%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="730c5-111">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="730c5-112">W ramach `using` bloku, obiekt jest tylko do odczytu i nie można zmodyfikować lub ponownie przypisany.</span><span class="sxs-lookup"><span data-stu-id="730c5-112">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>  
  
 <span data-ttu-id="730c5-113">`using` Instrukcji upewnia się, że <xref:System.IDisposable.Dispose%2A> jest wywoływana, nawet jeśli wystąpi wyjątek w `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="730c5-113">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="730c5-114">Można uzyskać ten sam efekt, umieszczając obiekt wewnątrz `try` bloku, a następnie wywołując <xref:System.IDisposable.Dispose%2A> w `finally` zablokować; w rzeczywistości jest to sposób `using` instrukcji jest przetłumaczony przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="730c5-114">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="730c5-115">Przykładowy kod wcześniej rozwijany do następującego kodu w czasie kompilacji (Uwaga: dodatkowe nawiasy klamrowe do utworzenia ograniczony zakres dla obiekt):</span><span class="sxs-lookup"><span data-stu-id="730c5-115">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
 
 <span data-ttu-id="730c5-116">Aby uzyskać więcej informacji na temat `try` - `finally` instrukcji, zobacz [try-finally](try-finally.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="730c5-116">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) topic.</span></span>
  
 <span data-ttu-id="730c5-117">Wiele wystąpień tego typu mogą być deklarowane w `using` instrukcji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="730c5-117">Multiple instances of a type can be declared in the `using` statement, as shown in the following example:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 <span data-ttu-id="730c5-118">Można utworzyć wystąpienia obiektu zasobów, a następnie przekazać zmiennej `using` instrukcji, ale nie jest najlepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="730c5-118">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="730c5-119">W takim przypadku po liście kontroli `using` zablokować pozostaje obiekt w zakresie, ale prawdopodobnie nie ma dostępu do jego zasoby niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="730c5-119">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="730c5-120">Innymi słowy nie są w pełni zainicjowaniem już.</span><span class="sxs-lookup"><span data-stu-id="730c5-120">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="730c5-121">Jeśli spróbujesz użyć obiektu poza `using` zablokować ryzyka powoduje wyjątków.</span><span class="sxs-lookup"><span data-stu-id="730c5-121">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="730c5-122">Z tego powodu najlepiej ogólnie można utworzyć wystąpienia obiektu w `using` instrukcji i ograniczyć zakres do `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="730c5-122">For this reason, it's generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
<span data-ttu-id="730c5-123">Aby uzyskać więcej informacji na temat usuwania `IDisposable` obiekty, zobacz [przy użyciu obiektów, które implementują interfejs IDisposable](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="730c5-123">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="730c5-124">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="730c5-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="730c5-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="730c5-125">See Also</span></span>  
 [<span data-ttu-id="730c5-126">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="730c5-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="730c5-127">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="730c5-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="730c5-128">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="730c5-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="730c5-129">using, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="730c5-129">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
 [<span data-ttu-id="730c5-130">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="730c5-130">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
 [<span data-ttu-id="730c5-131">Używanie obiektów implementujących interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="730c5-131">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)  
 [<span data-ttu-id="730c5-132">Interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="730c5-132">IDisposable interface</span></span>](xref:System.IDisposable)
