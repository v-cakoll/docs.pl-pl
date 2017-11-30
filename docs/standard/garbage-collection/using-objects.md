---
title: "Używanie obiektów implementujących interfejs IDisposable"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fd78c2f99ca5c8ffe3c753e158ceba3e0c458c5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="cd3d7-102">Używanie obiektów implementujących interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="cd3d7-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="cd3d7-103">Środowisko uruchomieniowe języka wspólnego przez moduł Garbage Collector zwraca pamięć używana przez obiekty zarządzane, ale implementuje typów, które używają zasoby niezarządzane <xref:System.IDisposable> interfejs umożliwia pamięć przydzielona do tych zasobów niezarządzanych. można odzyskać.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the memory allocated to these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="cd3d7-104">Po zakończeniu przy użyciu obiektu implementującego <xref:System.IDisposable>, należy wywołać obiektu <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="cd3d7-105">Można to zrobić na jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="cd3d7-105">You can do this in one of two ways:</span></span>  
  
* <span data-ttu-id="cd3d7-106">Z języka C# `using` instrukcji lub Visual Basic `Using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-106">With the C# `using` statement or the Visual Basic `Using` statement.</span></span>  
  
* <span data-ttu-id="cd3d7-107">Zaimplementowanie `try/finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-107">By implementing a `try/finally` block.</span></span>  

## <a name="the-using-statement"></a><span data-ttu-id="cd3d7-108">Instrukcja using</span><span class="sxs-lookup"><span data-stu-id="cd3d7-108">The using statement</span></span>

<span data-ttu-id="cd3d7-109">`using` Instrukcji w języku C# i `Using` instrukcji w języku Visual Basic uprościć kod, który musi być zapisana do tworzenia i wyczyścić obiektu.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-109">The `using` statement in C# and the `Using` statement in Visual Basic simplify the code that you must write to create and clean up an object.</span></span> <span data-ttu-id="cd3d7-110">`using` Instrukcji uzyskuje jeden lub więcej zasobów, wykonuje instrukcje, które określają i automatycznie usuwa obiektu.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="cd3d7-111">Jednak `using` instrukcji przydaje się tylko dla obiektów, które są używane w zakresie metody, w których są wykonane.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>  
  
<span data-ttu-id="cd3d7-112">W poniższym przykładzie użyto `using` instrukcji, aby utworzyć i zwolnij <xref:System.IO.StreamReader?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<span data-ttu-id="cd3d7-113">Należy pamiętać, że chociaż <xref:System.IO.StreamReader> klasa implementuje <xref:System.IDisposable> interfejs, który wskazuje, że używa niezarządzanym zasobem przykładzie nie jawnie wywołać <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-113">Note that although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cd3d7-114">Gdy wystąpi kompilatora C# lub Visual Basic `using` instrukcji, emituje język pośredni (IL), który jest odpowiednikiem następujący kod, który zawiera jawnie `try/finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
<span data-ttu-id="cd3d7-115">C# `using` instrukcji pozwala również uzyskać wiele zasobów w jednej instrukcji, który jest odpowiednikiem wewnętrznie zagnieżdżone `using` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="cd3d7-116">Poniższy przykład tworzy dwa <xref:System.IO.StreamReader> obiekty do odczytu treści dwóch różnych plików.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="cd3d7-117">Blok try/finally</span><span class="sxs-lookup"><span data-stu-id="cd3d7-117">Try/finally block</span></span>

<span data-ttu-id="cd3d7-118">Zamiast zawijania `try/finally` blok w `using` instrukcji, może zadecydować o stosowaniu `try/finally` zablokować bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="cd3d7-119">Może to wynikać z osobistego stylu kodowania albo mieć jedną z następujących przyczyn:</span><span class="sxs-lookup"><span data-stu-id="cd3d7-119">This may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>  
  
* <span data-ttu-id="cd3d7-120">Aby uwzględnić `catch` bloku do obsługi wszelkie wyjątki zgłaszane `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-120">To include a `catch` block to handle any exceptions thrown in the `try` block.</span></span> <span data-ttu-id="cd3d7-121">W przeciwnym razie wartość, wszelkie wyjątki zgłaszane przez `using` instrukcji są nieobsługiwany, ponieważ są wszelkie wyjątki zgłaszane w `using` zablokować, jeśli `try/catch` bloku nie jest obecny.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-121">Otherwise, any exceptions thrown by the `using` statement are unhandled, as are any exceptions thrown within the `using` block if a `try/catch` block isn't present.</span></span>  
  
* <span data-ttu-id="cd3d7-122">Można utworzyć wystąpienia obiektu implementującego <xref:System.IDisposable> którego zakres nie jest lokalny blok, w którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>  
  
<span data-ttu-id="cd3d7-123">Poniższy przykład jest podobny do poprzedniego przykładu, z wyjątkiem tego, że używa `try/catch/finally` blok do tworzenia wystąpienia, używanie i usuwanie <xref:System.IO.StreamReader> obiektu i do obsługi wszelkie wyjątki zgłaszane przez <xref:System.IO.StreamReader> Konstruktor i jego <xref:System.IO.StreamReader.ReadToEnd%2A> — metoda.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="cd3d7-124">Należy pamiętać, że kod w `finally` bloku sprawdza, czy obiekt z zaimplementowanym interfejsem <xref:System.IDisposable> nie jest `null` przed wywołaniem <xref:System.IDisposable.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-124">Note that the code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="cd3d7-125">Może spowodować niepowodzenie w tym celu <xref:System.NullReferenceException> wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
<span data-ttu-id="cd3d7-126">Możesz wykonać ten podstawowy wzorzec zadecydować o stosowaniu lub musi implementować `try/finally` zablokować, ponieważ nie obsługuje języka programowania `using` instrukcji, ale zezwala na bezpośrednie wywołania <xref:System.IDisposable.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cd3d7-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="cd3d7-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd3d7-127">See also</span></span>

<span data-ttu-id="cd3d7-128">[Oczyszczanie zasobów niezarządzanych](../../../docs/standard/garbage-collection/unmanaged.md) </span><span class="sxs-lookup"><span data-stu-id="cd3d7-128">[Cleaning Up Unmanaged Resources](../../../docs/standard/garbage-collection/unmanaged.md) </span></span>  
<span data-ttu-id="cd3d7-129">[Using — instrukcja (odwołanie w C#)](~/docs/csharp/language-reference/keywords/using-statement.md) </span><span class="sxs-lookup"><span data-stu-id="cd3d7-129">[using Statement (C# Reference)](~/docs/csharp/language-reference/keywords/using-statement.md) </span></span>  
[<span data-ttu-id="cd3d7-130">Using — instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd3d7-130">Using Statement (Visual Basic)</span></span>](~/docs/visual-basic/language-reference/statements/using-statement.md)
