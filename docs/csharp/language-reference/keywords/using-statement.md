---
title: using — C# odwołanie
ms.date: 10/15/2019
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 52cde99fd029ce50f159b2a87fbfbf47fc79dccc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712965"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="090e5-102">using — instrukcjaC# (Reference)</span><span class="sxs-lookup"><span data-stu-id="090e5-102">using statement (C# Reference)</span></span>

<span data-ttu-id="090e5-103">Zapewnia wygodną składnię, która zapewnia poprawne korzystanie z <xref:System.IDisposable> obiektów.</span><span class="sxs-lookup"><span data-stu-id="090e5-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="090e5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="090e5-104">Example</span></span>

<span data-ttu-id="090e5-105">Poniższy przykład pokazuje, jak używać instrukcji `using`.</span><span class="sxs-lookup"><span data-stu-id="090e5-105">The following example shows how to use the `using` statement.</span></span>

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

<span data-ttu-id="090e5-106">Począwszy od C# 8,0, można użyć następującej składni alternatywnej dla instrukcji `using`, która nie wymaga nawiasów klamrowych:</span><span class="sxs-lookup"><span data-stu-id="090e5-106">Beginning with C# 8.0, you can use the following alternative syntax for the `using` statement that doesn't require braces:</span></span>

[!code-csharp[csrefKeywordsNamespace#New](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#ModernUsing)]

## <a name="remarks"></a><span data-ttu-id="090e5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="090e5-107">Remarks</span></span>

<span data-ttu-id="090e5-108"><xref:System.IO.File> i <xref:System.Drawing.Font> są przykładami typów zarządzanych, które uzyskują dostęp do niezarządzanych zasobów (w tym przypadku dojścia do plików i konteksty urządzenia).</span><span class="sxs-lookup"><span data-stu-id="090e5-108"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="090e5-109">Istnieje wiele innych rodzajów niezarządzanych zasobów i typów bibliotek klas, które hermetyzują.</span><span class="sxs-lookup"><span data-stu-id="090e5-109">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="090e5-110">Wszystkie takie typy muszą implementować interfejs <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="090e5-110">All such types must implement the <xref:System.IDisposable> interface.</span></span>

<span data-ttu-id="090e5-111">Gdy okres istnienia obiektu `IDisposable` jest ograniczony do pojedynczej metody, należy zadeklarować ją i utworzyć jej wystąpienie w instrukcji `using`.</span><span class="sxs-lookup"><span data-stu-id="090e5-111">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="090e5-112">Instrukcja `using` wywołuje metodę <xref:System.IDisposable.Dispose%2A> na obiekcie w prawidłowy sposób i (gdy jest używana wcześniej), powoduje również, że obiekt nie wyjdzie poza zakres od razu po wywołaniu <xref:System.IDisposable.Dispose%2A>.</span><span class="sxs-lookup"><span data-stu-id="090e5-112">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="090e5-113">W bloku `using` obiekt jest tylko do odczytu i nie można go modyfikować ani ponownie przypisywać.</span><span class="sxs-lookup"><span data-stu-id="090e5-113">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>

<span data-ttu-id="090e5-114">Instrukcja `using` zapewnia, że <xref:System.IDisposable.Dispose%2A> jest wywoływana, nawet jeśli wystąpi wyjątek w bloku `using`.</span><span class="sxs-lookup"><span data-stu-id="090e5-114">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="090e5-115">Można osiągnąć ten sam wynik, umieszczając obiekt wewnątrz bloku `try`, a następnie wywołując <xref:System.IDisposable.Dispose%2A> w bloku `finally`; w rzeczywistości jest to sposób tłumaczenia instrukcji `using` przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="090e5-115">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="090e5-116">Przykładowy kod jest rozwinięty do poniższego kodu w czasie kompilacji (należy zwrócić uwagę na dodatkowe nawiasy klamrowe, aby utworzyć ograniczony zakres dla obiektu):</span><span class="sxs-lookup"><span data-stu-id="090e5-116">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

<span data-ttu-id="090e5-117">Nowsza składnia instrukcji `using` Wykonuje translację na bardzo podobny kod.</span><span class="sxs-lookup"><span data-stu-id="090e5-117">The newer `using` statement syntax translates to very similar code.</span></span> <span data-ttu-id="090e5-118">Zostanie otwarty blok `try`, w którym jest zadeklarowana zmienna.</span><span class="sxs-lookup"><span data-stu-id="090e5-118">The `try` block opens where the variable is declared.</span></span> <span data-ttu-id="090e5-119">Blok `finally` jest dodawany w pobliżu otaczającego bloku, na ogół na końcu metody.</span><span class="sxs-lookup"><span data-stu-id="090e5-119">The `finally` block is added at the close of the enclosing block, typically at the end of a method.</span></span>

<span data-ttu-id="090e5-120">Aby uzyskać więcej informacji na temat instrukcji `try`-`finally`, zobacz temat [try-finally](try-finally.md) .</span><span class="sxs-lookup"><span data-stu-id="090e5-120">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) topic.</span></span>

<span data-ttu-id="090e5-121">W instrukcji `using` można zadeklarować wiele wystąpień typu, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="090e5-121">Multiple instances of a type can be declared in the `using` statement, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

<span data-ttu-id="090e5-122">Można połączyć wiele deklaracji tego samego typu, używając nowej składni wprowadzonej przy użyciu C# również 8.</span><span class="sxs-lookup"><span data-stu-id="090e5-122">You can combine multiple declarations of the same type using the new syntax introduced with C# 8 as well.</span></span> <span data-ttu-id="090e5-123">Jest to pokazane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="090e5-123">This is shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#MultipleUsing)]

<span data-ttu-id="090e5-124">Można utworzyć wystąpienie obiektu zasobu, a następnie przekazać zmienną do instrukcji `using`, ale nie jest to najlepsze rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="090e5-124">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="090e5-125">W takim przypadku, gdy kontrolka opuszcza blok `using`, obiekt pozostaje w zakresie, ale prawdopodobnie nie ma dostępu do jego niezarządzanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="090e5-125">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="090e5-126">Innymi słowy, nie jest już w pełni zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="090e5-126">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="090e5-127">Jeśli spróbujesz użyć obiektu poza blokiem `using`, istnieje ryzyko, że zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="090e5-127">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="090e5-128">Z tego powodu zwykle lepiej jest utworzyć wystąpienie obiektu w instrukcji `using` i ograniczyć jego zakres do bloku `using`.</span><span class="sxs-lookup"><span data-stu-id="090e5-128">For this reason, it's generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

<span data-ttu-id="090e5-129">Aby uzyskać więcej informacji na temat usuwania obiektów `IDisposable`, zobacz [Używanie obiektów implementujących interfejs IDisposable](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="090e5-129">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="090e5-130">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="090e5-130">C# language specification</span></span>

<span data-ttu-id="090e5-131">Aby uzyskać więcej informacji, zobacz [instrukcja using](~/_csharplang/spec/statements.md#the-using-statement) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="090e5-131">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="090e5-132">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="090e5-132">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="090e5-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="090e5-133">See also</span></span>

- [<span data-ttu-id="090e5-134">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="090e5-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="090e5-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="090e5-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="090e5-136">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="090e5-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="090e5-137">using, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="090e5-137">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="090e5-138">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="090e5-138">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="090e5-139">Używanie obiektów implementujących interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="090e5-139">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="090e5-140">Interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="090e5-140">IDisposable interface</span></span>](xref:System.IDisposable)
- [<span data-ttu-id="090e5-141">Instrukcja Using w C# 8,0</span><span class="sxs-lookup"><span data-stu-id="090e5-141">using statement in C# 8.0</span></span>](~/_csharplang/proposals/csharp-8.0/using.md)
