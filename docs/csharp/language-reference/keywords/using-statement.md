---
title: za pomocą instrukcji - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: df116a200795fd20405381fd71e82d1d6fe662bc
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614392"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="99b5e-102">Using — instrukcja (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="99b5e-102">using statement (C# Reference)</span></span>

<span data-ttu-id="99b5e-103">Miejsce wygodnej składni, która zapewnia prawidłowe użycie <xref:System.IDisposable> obiektów.</span><span class="sxs-lookup"><span data-stu-id="99b5e-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="99b5e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="99b5e-104">Example</span></span>

<span data-ttu-id="99b5e-105">Poniższy przykład pokazuje, jak używać `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="99b5e-105">The following example shows how to use the `using` statement.</span></span>

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

## <a name="remarks"></a><span data-ttu-id="99b5e-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99b5e-106">Remarks</span></span>

<span data-ttu-id="99b5e-107"><xref:System.IO.File> i <xref:System.Drawing.Font> to przykłady typów zarządzanych, uzyskujących dostęp do niezarządzanych zasobów (w tym dojścia do plików wielkości liter i konteksty urządzenia).</span><span class="sxs-lookup"><span data-stu-id="99b5e-107"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="99b5e-108">Istnieje wiele innych rodzajów zasobów niezarządzanych i typy biblioteki klas, które hermetyzują je.</span><span class="sxs-lookup"><span data-stu-id="99b5e-108">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="99b5e-109">Typy takie musi implementować <xref:System.IDisposable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="99b5e-109">All such types must implement the <xref:System.IDisposable> interface.</span></span>

<span data-ttu-id="99b5e-110">Gdy okres istnienia `IDisposable` obiektu jest ograniczona do jednej metody, należy zadeklarować i Utwórz wystąpienie w `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="99b5e-110">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="99b5e-111">`using` Instrukcja wywołuje <xref:System.IDisposable.Dispose%2A> metody na obiekt w prawidłowy sposób i (Jeśli używasz tego jak pokazano wcześniej) powoduje także sam wykraczać poza zakres obiekt zaraz <xref:System.IDisposable.Dispose%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="99b5e-111">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="99b5e-112">W ramach `using` bloku, obiekt jest tylko do odczytu i nie można zmodyfikować ani ponownie przypisane.</span><span class="sxs-lookup"><span data-stu-id="99b5e-112">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>

<span data-ttu-id="99b5e-113">`using` Instrukcji zapewnia, że <xref:System.IDisposable.Dispose%2A> jest wywoływana, nawet jeśli wystąpi wyjątek w obrębie `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="99b5e-113">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="99b5e-114">Ten sam efekt można osiągnąć, umieszczając w obiekcie wewnątrz właściwości `try` bloku, a następnie wywołując <xref:System.IDisposable.Dispose%2A> w `finally` zablokować; w rzeczywistości jest to sposób, w jaki `using` instrukcji jest tłumaczony przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="99b5e-114">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="99b5e-115">W przykładzie kodu wcześniej rozwija następujący kod w czasie kompilacji (Uwaga: bardzo nawiasy klamrowe, aby utworzyć ograniczony zakres dla obiektu "):</span><span class="sxs-lookup"><span data-stu-id="99b5e-115">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

<span data-ttu-id="99b5e-116">Aby uzyskać więcej informacji na temat `try` - `finally` poufności informacji, zobacz [try-finally](try-finally.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="99b5e-116">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) topic.</span></span>

<span data-ttu-id="99b5e-117">Wiele wystąpień tego typu może być zadeklarowana w `using` instrukcji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="99b5e-117">Multiple instances of a type can be declared in the `using` statement, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

<span data-ttu-id="99b5e-118">Można utworzyć wystąpienia obiektu zasobu, a następnie przekaż zmienną `using` instrukcji, ale nie jest najlepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="99b5e-118">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="99b5e-119">W takim przypadku po liście kontroli `using` zablokować, pozostaje obiekt w zakresie, ale prawdopodobnie nie ma dostępu do niezarządzanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="99b5e-119">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="99b5e-120">Innymi słowy nie są w pełni inicjalizacji dłużej.</span><span class="sxs-lookup"><span data-stu-id="99b5e-120">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="99b5e-121">Jeśli spróbujesz użyć obiektu poza `using` zablokować ryzyka powoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="99b5e-121">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="99b5e-122">Z tego powodu zaleca ogólnie do utworzenia wystąpienia obiektu w `using` instrukcji i jego zakres, aby ograniczyć `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="99b5e-122">For this reason, it's generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

<span data-ttu-id="99b5e-123">Aby uzyskać więcej informacji na temat usuwania `IDisposable` obiekty, zobacz [używanie obiektów implementujących interfejs IDisposable](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="99b5e-123">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="99b5e-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="99b5e-124">C# language specification</span></span>

<span data-ttu-id="99b5e-125">Aby uzyskać więcej informacji, zobacz [za pomocą instrukcji](~/_csharplang/spec/statements.md#the-using-statement) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="99b5e-125">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="99b5e-126">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="99b5e-126">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="99b5e-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99b5e-127">See also</span></span>

- [<span data-ttu-id="99b5e-128">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="99b5e-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="99b5e-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="99b5e-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="99b5e-130">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="99b5e-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="99b5e-131">using, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="99b5e-131">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="99b5e-132">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="99b5e-132">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="99b5e-133">Używanie obiektów implementujących interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="99b5e-133">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="99b5e-134">Interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="99b5e-134">IDisposable interface</span></span>](xref:System.IDisposable)