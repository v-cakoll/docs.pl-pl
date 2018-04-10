---
title: using — Instrukcja (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1fdf37e1bfc57bf850b332f167e57d3e05d23e78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="a0fbb-102">using — Instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a0fbb-102">using Statement (C# Reference)</span></span>
<span data-ttu-id="a0fbb-103">Umożliwia wygodne składnię, która zapewnia prawidłowe użycie <xref:System.IDisposable> obiektów.</span><span class="sxs-lookup"><span data-stu-id="a0fbb-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0fbb-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0fbb-104">Example</span></span>  
 <span data-ttu-id="a0fbb-105">Poniższy przykład przedstawia użycie przy użyciu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a0fbb-105">The following example shows how to use the using statement.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="a0fbb-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a0fbb-106">Remarks</span></span>  
 <span data-ttu-id="a0fbb-107"><xref:System.IO.File>i <xref:System.Drawing.Font> przedstawiono przykładowe typy zarządzane, które uzyskują dostęp do zasobów niezarządzanych (w tym dojścia do plików w przypadku i konteksty urządzenia).</span><span class="sxs-lookup"><span data-stu-id="a0fbb-107"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="a0fbb-108">Istnieje wiele rodzajów zasoby niezarządzane i klasy biblioteki typów, które hermetyzują je.</span><span class="sxs-lookup"><span data-stu-id="a0fbb-108">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="a0fbb-109">Takich typów musi implementować <xref:System.IDisposable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a0fbb-109">All such types must implement the <xref:System.IDisposable> interface.</span></span>  
  
<span data-ttu-id="a0fbb-110">Jeśli okres istnienia `IDisposable` obiektu jest ograniczony do pojedynczej metody, należy zadeklarować i utworzyć w `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a0fbb-110">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in a `using` statement.</span></span> <span data-ttu-id="a0fbb-111">`using` Wywołania instrukcji <xref:System.IDisposable.Dispose%2A> metody dla obiekt w prawidłowy sposób i (gdy jest używany jak pokazano wcześniej) powoduje także obiekt, aby znaleźć poza zakresem natychmiast <xref:System.IDisposable.Dispose%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="a0fbb-111">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="a0fbb-112">W ramach `using` bloku, obiekt jest tylko do odczytu i nie można zmodyfikować lub ponownie przypisany.</span><span class="sxs-lookup"><span data-stu-id="a0fbb-112">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>  
  
 <span data-ttu-id="a0fbb-113">`using` Instrukcji upewnia się, że <xref:System.IDisposable.Dispose%2A> jest wywoływana, nawet jeśli wystąpi wyjątek podczas wywoływania metody dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="a0fbb-113">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs while you are calling methods on the object.</span></span> <span data-ttu-id="a0fbb-114">Umieszczanie obiektu wewnątrz bloku try, a następnie podczas wywoływania można osiągnąć ten sam rezultat <xref:System.IDisposable.Dispose%2A> w bloku finally; w rzeczywistości jest to sposób `using` instrukcji jest przetłumaczony przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="a0fbb-114">You can achieve the same result by putting the object inside a try block and then calling <xref:System.IDisposable.Dispose%2A> in a finally block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="a0fbb-115">Przykładowy kod wcześniej rozwijany do następującego kodu w czasie kompilacji (Uwaga: dodatkowe nawiasy klamrowe do utworzenia ograniczony zakres dla obiekt):</span><span class="sxs-lookup"><span data-stu-id="a0fbb-115">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
  
 <span data-ttu-id="a0fbb-116">Wiele wystąpień tego typu mogą być deklarowane w `using` instrukcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a0fbb-116">Multiple instances of a type can be declared in a `using` statement, as shown in the following example.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 <span data-ttu-id="a0fbb-117">Można utworzyć wystąpienia obiektu zasobów, a następnie przekazać zmiennej `using` instrukcji, ale nie jest najlepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="a0fbb-117">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="a0fbb-118">W takim przypadku obiekt pozostaje w zakresie po sterowanie wyjdzie `using` zablokować, mimo że prawdopodobnie nie ma dostępu do jego zasoby niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="a0fbb-118">In this case, the object remains in scope after control leaves the `using` block even though it will probably no longer have access to its unmanaged resources.</span></span> <span data-ttu-id="a0fbb-119">Innymi słowy jego będzie już można w pełni zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="a0fbb-119">In other words, it will no longer be fully initialized.</span></span> <span data-ttu-id="a0fbb-120">Jeśli spróbujesz użyć obiektu poza `using` zablokować ryzyka powoduje wyjątków.</span><span class="sxs-lookup"><span data-stu-id="a0fbb-120">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="a0fbb-121">Z tego powodu najlepiej ogólnie można utworzyć wystąpienia obiektu w `using` instrukcji i ograniczyć zakres do `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="a0fbb-121">For this reason, it is generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
<span data-ttu-id="a0fbb-122">Aby uzyskać więcej informacji na temat usuwania `IDisposable` obiekty, zobacz [przy użyciu obiektów, które implementują interfejs IDisposable](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="a0fbb-122">For more information on disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a0fbb-123">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a0fbb-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a0fbb-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0fbb-124">See Also</span></span>  
 [<span data-ttu-id="a0fbb-125">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="a0fbb-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a0fbb-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a0fbb-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a0fbb-127">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="a0fbb-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="a0fbb-128">Using — Dyrektywa</span><span class="sxs-lookup"><span data-stu-id="a0fbb-128">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
 [<span data-ttu-id="a0fbb-129">Wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="a0fbb-129">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
 [<span data-ttu-id="a0fbb-130">Używanie obiektów implementujących interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="a0fbb-130">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)  
 [<span data-ttu-id="a0fbb-131">Interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="a0fbb-131">IDisposable interface</span></span>](xref:System.IDisposable)
