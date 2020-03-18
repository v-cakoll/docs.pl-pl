---
title: using statement - C# Odwołanie
ms.date: 10/15/2019
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 52cde99fd029ce50f159b2a87fbfbf47fc79dccc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712965"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="2023e-102">using statement (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="2023e-102">using statement (C# Reference)</span></span>

<span data-ttu-id="2023e-103">Zapewnia wygodną składnię, która <xref:System.IDisposable> zapewnia prawidłowe użycie obiektów.</span><span class="sxs-lookup"><span data-stu-id="2023e-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="2023e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2023e-104">Example</span></span>

<span data-ttu-id="2023e-105">W poniższym przykładzie pokazano, jak używać `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2023e-105">The following example shows how to use the `using` statement.</span></span>

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

<span data-ttu-id="2023e-106">Począwszy od języka C# 8.0, można użyć `using` następującej alternatywnej składni dla instrukcji, która nie wymaga nawiasów klamrowych:</span><span class="sxs-lookup"><span data-stu-id="2023e-106">Beginning with C# 8.0, you can use the following alternative syntax for the `using` statement that doesn't require braces:</span></span>

[!code-csharp[csrefKeywordsNamespace#New](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#ModernUsing)]

## <a name="remarks"></a><span data-ttu-id="2023e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2023e-107">Remarks</span></span>

<span data-ttu-id="2023e-108"><xref:System.IO.File>i <xref:System.Drawing.Font> są przykładami typów zarządzanych, które uzyskują dostęp do zasobów niezarządzanych (w tym przypadku dojścia do plików i kontekstów urządzeń).</span><span class="sxs-lookup"><span data-stu-id="2023e-108"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="2023e-109">Istnieje wiele innych rodzajów zasobów niezarządzanych i typów bibliotek klas, które je hermetyzują.</span><span class="sxs-lookup"><span data-stu-id="2023e-109">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="2023e-110">Wszystkie takie typy <xref:System.IDisposable> muszą implementować interfejs.</span><span class="sxs-lookup"><span data-stu-id="2023e-110">All such types must implement the <xref:System.IDisposable> interface.</span></span>

<span data-ttu-id="2023e-111">Gdy okres istnienia `IDisposable` obiektu jest ograniczona do jednej metody, należy zadeklarować i utworzyć wystąpienia w `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2023e-111">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="2023e-112">Instrukcja `using` wywołuje <xref:System.IDisposable.Dispose%2A> metodę na obiekcie w prawidłowy sposób i (gdy używasz go, jak pokazano wcześniej) powoduje <xref:System.IDisposable.Dispose%2A> również, że sam obiekt, aby przejść poza zakres, jak tylko zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="2023e-112">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="2023e-113">W `using` bloku obiekt jest tylko do odczytu i nie można go modyfikować ani ponownie przypisywać.</span><span class="sxs-lookup"><span data-stu-id="2023e-113">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>

<span data-ttu-id="2023e-114">Instrukcja `using` zapewnia, <xref:System.IDisposable.Dispose%2A> że jest wywoływana, `using` nawet jeśli wystąpi wyjątek w bloku.</span><span class="sxs-lookup"><span data-stu-id="2023e-114">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="2023e-115">Ten sam wynik można osiągnąć, umieszczając `try` obiekt wewnątrz <xref:System.IDisposable.Dispose%2A> bloku, a następnie wywołując w `finally` bloku; w rzeczywistości jest to, jak instrukcja `using` jest tłumaczona przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="2023e-115">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="2023e-116">Przykład kodu wcześniej rozszerza się do następującego kodu w czasie kompilacji (zwróć uwagę na dodatkowe nawiasy klamrowe, aby utworzyć ograniczony zakres dla obiektu):</span><span class="sxs-lookup"><span data-stu-id="2023e-116">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

<span data-ttu-id="2023e-117">Nowsza `using` składnia instrukcji przekłada się na bardzo podobny kod.</span><span class="sxs-lookup"><span data-stu-id="2023e-117">The newer `using` statement syntax translates to very similar code.</span></span> <span data-ttu-id="2023e-118">Blok `try` zostanie otwarty, gdzie zmienna jest zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="2023e-118">The `try` block opens where the variable is declared.</span></span> <span data-ttu-id="2023e-119">Blok `finally` jest dodawany na zamknięciu otaczającego bloku, zazwyczaj na końcu metody.</span><span class="sxs-lookup"><span data-stu-id="2023e-119">The `finally` block is added at the close of the enclosing block, typically at the end of a method.</span></span>

<span data-ttu-id="2023e-120">Aby uzyskać więcej `try` - `finally` informacji na temat instrukcji, zobacz temat [try-finally.](try-finally.md)</span><span class="sxs-lookup"><span data-stu-id="2023e-120">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) topic.</span></span>

<span data-ttu-id="2023e-121">Wiele wystąpień typu można zadeklarować `using` w instrukcji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2023e-121">Multiple instances of a type can be declared in the `using` statement, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

<span data-ttu-id="2023e-122">Można połączyć wiele deklaracji tego samego typu przy użyciu nowej składni wprowadzone z C# 8, jak również.</span><span class="sxs-lookup"><span data-stu-id="2023e-122">You can combine multiple declarations of the same type using the new syntax introduced with C# 8 as well.</span></span> <span data-ttu-id="2023e-123">Jest to pokazane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2023e-123">This is shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#MultipleUsing)]

<span data-ttu-id="2023e-124">Można utworzyć wystąpienia obiektu zasobu, a następnie `using` przekazać zmienną do instrukcji, ale nie jest to najlepsze rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="2023e-124">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="2023e-125">W takim przypadku po `using` kontroli opuszcza blok, obiekt pozostaje w zakresie, ale prawdopodobnie nie ma dostępu do jego zasobów niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="2023e-125">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="2023e-126">Innymi słowy, nie jest już w pełni zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="2023e-126">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="2023e-127">Jeśli spróbujesz użyć `using` obiektu poza blokiem, istnieje ryzyko, powodując wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2023e-127">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="2023e-128">Z tego powodu zazwyczaj lepiej jest utworzyć wystąpienia obiektu w `using` instrukcji i ograniczyć `using` jego zakres do bloku.</span><span class="sxs-lookup"><span data-stu-id="2023e-128">For this reason, it's generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

<span data-ttu-id="2023e-129">Aby uzyskać więcej informacji `IDisposable` na temat usuwania obiektów, zobacz [Korzystanie z obiektów, które implementują IDisposable](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="2023e-129">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2023e-130">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2023e-130">C# language specification</span></span>

<span data-ttu-id="2023e-131">Aby uzyskać więcej informacji, zobacz [Using instrukcji](~/_csharplang/spec/statements.md#the-using-statement) w [specyfikacji języka Języka C #](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="2023e-131">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="2023e-132">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="2023e-132">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="2023e-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2023e-133">See also</span></span>

- [<span data-ttu-id="2023e-134">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="2023e-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2023e-135">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="2023e-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2023e-136">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="2023e-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2023e-137">using, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="2023e-137">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="2023e-138">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="2023e-138">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="2023e-139">Korzystanie z obiektów implementujących IDisposable</span><span class="sxs-lookup"><span data-stu-id="2023e-139">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="2023e-140">Interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="2023e-140">IDisposable interface</span></span>](xref:System.IDisposable)
- [<span data-ttu-id="2023e-141">używanie instrukcji w języku C# 8.0</span><span class="sxs-lookup"><span data-stu-id="2023e-141">using statement in C# 8.0</span></span>](~/_csharplang/proposals/csharp-8.0/using.md)
