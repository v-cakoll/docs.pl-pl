---
title: Używanie obiektów implementujących interfejs IDisposable
description: Dowiedz się, jak używać obiektów implementujących interfejs IDisposable w programie .NET. Typy korzystające z zasobów niezarządzanych implementują interfejs IDisposable, aby zezwalać na odzyskiwanie zasobów.
ms.date: 05/13/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
ms.openlocfilehash: 7d5d4080f22aab6870a230d495b4a4b9ebcb3b96
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599857"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="4af61-104">Używanie obiektów implementujących interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="4af61-104">Using objects that implement IDisposable</span></span>

<span data-ttu-id="4af61-105">Moduł zbierający elementy bezużyteczne środowiska uruchomieniowego języka wspólnego ponownie przejmuje pamięć używaną przez zarządzane obiekty, ale typy korzystające z zasobów niezarządzanych implementują <xref:System.IDisposable> interfejs w celu zezwalania na odzyskiwanie zasobów wymaganych przez te niezarządzane zasoby.</span><span class="sxs-lookup"><span data-stu-id="4af61-105">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the resources needed by these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="4af61-106">Po zakończeniu korzystania z obiektu, który implementuje <xref:System.IDisposable> , należy wywołać <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementację obiektu.</span><span class="sxs-lookup"><span data-stu-id="4af61-106">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="4af61-107">Można to zrobić na jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="4af61-107">You can do this in one of two ways:</span></span>

- <span data-ttu-id="4af61-108">Za pomocą instrukcji języka C# `using` ( `Using` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4af61-108">With the C# `using` statement (`Using` in Visual Basic).</span></span>
- <span data-ttu-id="4af61-109">Przez implementację `try/finally` bloku i wywołanie elementu <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> w `finally` .</span><span class="sxs-lookup"><span data-stu-id="4af61-109">By implementing a `try/finally` block, and calling the <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> in the `finally`.</span></span>

## <a name="the-using-statement"></a><span data-ttu-id="4af61-110">Instrukcja using</span><span class="sxs-lookup"><span data-stu-id="4af61-110">The using statement</span></span>

<span data-ttu-id="4af61-111">[ `using` Instrukcja](../../csharp/language-reference/keywords/using-statement.md) w języku C# i [ `Using` instrukcja](../../visual-basic/language-reference/statements/using-statement.md) w Visual Basic upraszczają kod, który należy napisać, aby oczyścić obiekt.</span><span class="sxs-lookup"><span data-stu-id="4af61-111">The [`using` statement](../../csharp/language-reference/keywords/using-statement.md) in C# and the [`Using` statement](../../visual-basic/language-reference/statements/using-statement.md) in Visual Basic simplify the code that you must write to cleanup an object.</span></span> <span data-ttu-id="4af61-112">`using`Instrukcja uzyskuje jeden lub więcej zasobów, wykonuje określone instrukcje i automatycznie usuwa obiekt.</span><span class="sxs-lookup"><span data-stu-id="4af61-112">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="4af61-113">Jednak `using` instrukcja jest przydatna tylko w przypadku obiektów, które są używane w zakresie metody, w której są zbudowane.</span><span class="sxs-lookup"><span data-stu-id="4af61-113">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>

<span data-ttu-id="4af61-114">Poniższy przykład używa `using` instrukcji w celu utworzenia i zwolnienia <xref:System.IO.StreamReader?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="4af61-114">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>

[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]

<span data-ttu-id="4af61-115">Mimo że <xref:System.IO.StreamReader> Klasa implementuje <xref:System.IDisposable> interfejs, który wskazuje, że używa niezarządzanego zasobu, przykład nie wywołuje jawnie <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="4af61-115">Although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4af61-116">Gdy kompilator języka C# lub Visual Basic napotka `using` instrukcję, emituje język pośredni (IL), który jest odpowiednikiem poniższego kodu, który jawnie zawiera `try/finally` blok.</span><span class="sxs-lookup"><span data-stu-id="4af61-116">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>

[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]

<span data-ttu-id="4af61-117">Instrukcja języka C# `using` umożliwia także uzyskanie wielu zasobów w pojedynczej instrukcji, która jest wewnętrznie odpowiednikiem zagnieżdżonych `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4af61-117">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="4af61-118">Poniższy przykład tworzy wystąpienie dwóch <xref:System.IO.StreamReader> obiektów w celu odczytania zawartości dwóch różnych plików.</span><span class="sxs-lookup"><span data-stu-id="4af61-118">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>

[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="4af61-119">Blok try/finally</span><span class="sxs-lookup"><span data-stu-id="4af61-119">Try/finally block</span></span>

<span data-ttu-id="4af61-120">Zamiast zawijać `try/finally` blok w `using` instrukcji, możesz wybrać opcję `try/finally` bezpośredniego wdrożenia bloku.</span><span class="sxs-lookup"><span data-stu-id="4af61-120">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="4af61-121">Może to być osobisty styl kodowania lub można to zrobić z jednego z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="4af61-121">It may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>

- <span data-ttu-id="4af61-122">Aby dołączyć `catch` blok obsługujący wyjątki zgłoszone w `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="4af61-122">To include a `catch` block to handle exceptions thrown in the `try` block.</span></span> <span data-ttu-id="4af61-123">W przeciwnym razie wyjątki zgłaszane w `using` instrukcji są nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="4af61-123">Otherwise, any exceptions thrown within the `using` statement are unhandled.</span></span>

- <span data-ttu-id="4af61-124">Aby utworzyć wystąpienie obiektu, który implementuje, <xref:System.IDisposable> którego zakres nie jest lokalny dla bloku, w którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="4af61-124">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>

<span data-ttu-id="4af61-125">Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że używa `try/catch/finally` bloku do tworzenia wystąpienia, używania i usuwania <xref:System.IO.StreamReader> obiektu oraz do obsługi wszelkich wyjątków zgłoszonych przez <xref:System.IO.StreamReader> konstruktora i jego <xref:System.IO.StreamReader.ReadToEnd%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="4af61-125">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="4af61-126">Kod w `finally` bloku sprawdza, czy obiekt, który implementuje <xref:System.IDisposable> nie `null` przed wywołaniem <xref:System.IDisposable.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4af61-126">The code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="4af61-127">Niewykonanie tej czynności może spowodować wyjątek w <xref:System.NullReferenceException> czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4af61-127">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>

[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]

<span data-ttu-id="4af61-128">Możesz użyć tego podstawowego wzorca, jeśli zdecydujesz się zaimplementować lub musi zaimplementować `try/finally` blok, ponieważ język programowania nie obsługuje `using` instrukcji, ale zezwala na bezpośrednie wywołania <xref:System.IDisposable.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4af61-128">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span>

## <a name="idisposable-instance-members"></a><span data-ttu-id="4af61-129">Elementy członkowskie wystąpienia IDisposable</span><span class="sxs-lookup"><span data-stu-id="4af61-129">IDisposable instance members</span></span>

<span data-ttu-id="4af61-130">Jeśli klasa przechowuje <xref:System.IDisposable> implementację jako element członkowski wystąpienia, pole lub właściwość, należy również zaimplementować klasę <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="4af61-130">If a class holds an <xref:System.IDisposable> implementation as an instance member, either a field or a property, the class should also implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="4af61-131">Aby uzyskać więcej informacji, zobacz [implementacja kaskadowego usuwania](implementing-dispose.md#cascade-dispose-calls).</span><span class="sxs-lookup"><span data-stu-id="4af61-131">For more information, see [implement a cascade dispose](implementing-dispose.md#cascade-dispose-calls).</span></span>

## <a name="see-also"></a><span data-ttu-id="4af61-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4af61-132">See also</span></span>

- [<span data-ttu-id="4af61-133">Oczyszczanie zasobów niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="4af61-133">Cleaning up unmanaged resources</span></span>](unmanaged.md)
- [<span data-ttu-id="4af61-134">using — Instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4af61-134">using Statement (C# Reference)</span></span>](../../csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="4af61-135">Using — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4af61-135">Using Statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/using-statement.md)
