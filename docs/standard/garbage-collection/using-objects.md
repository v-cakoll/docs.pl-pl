---
title: Używanie obiektów implementujących interfejs IDisposable
ms.date: 04/07/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25c5ffa89e6ce4e589b8f12a7b8518272426c9e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597804"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="751e8-102">Używanie obiektów implementujących interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="751e8-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="751e8-103">Moduł wyrzucania elementów bezużytecznych wykonywalnych języka wspólnego odzyskuje pamięć używaną przez zarządzane obiekty, ale typy używające niezarządzanych zasobów implementują <xref:System.IDisposable> interfejsu, aby umożliwić pamięci przydzielonych do tych niezarządzanych zasobów, które można odzyskać.</span><span class="sxs-lookup"><span data-stu-id="751e8-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the memory allocated to these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="751e8-104">Po zakończeniu używania obiektu, który implementuje <xref:System.IDisposable>, należy wywołać obiektu <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji.</span><span class="sxs-lookup"><span data-stu-id="751e8-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="751e8-105">Można to zrobić na jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="751e8-105">You can do this in one of two ways:</span></span>  
  
* <span data-ttu-id="751e8-106">Za pomocą języka C# `using` instrukcji lub Visual Basic `Using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="751e8-106">With the C# `using` statement or the Visual Basic `Using` statement.</span></span>  
  
* <span data-ttu-id="751e8-107">Implementując `try/finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="751e8-107">By implementing a `try/finally` block.</span></span>  

## <a name="the-using-statement"></a><span data-ttu-id="751e8-108">Instrukcja using</span><span class="sxs-lookup"><span data-stu-id="751e8-108">The using statement</span></span>

<span data-ttu-id="751e8-109">`using` Instrukcji w języku C# i `Using` instrukcji w języku Visual Basic upraszczają kod, który trzeba napisać, aby utworzyć i oczyścić obiekt.</span><span class="sxs-lookup"><span data-stu-id="751e8-109">The `using` statement in C# and the `Using` statement in Visual Basic simplify the code that you must write to create and clean up an object.</span></span> <span data-ttu-id="751e8-110">`using` Instrukcji uzyskuje co najmniej jeden zasób, wykonuje instrukcje określone przez użytkownika, a następnie automatycznie usuwa obiekt.</span><span class="sxs-lookup"><span data-stu-id="751e8-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="751e8-111">Jednak `using` instrukcja jest użyteczna tylko w przypadku obiektów używanych zakresie metody, w której zostały skonstruowane.</span><span class="sxs-lookup"><span data-stu-id="751e8-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>  
  
<span data-ttu-id="751e8-112">W poniższym przykładzie użyto `using` instrukcję w celu utworzenia i zwolnienia <xref:System.IO.StreamReader?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="751e8-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<span data-ttu-id="751e8-113">Należy pamiętać, że chociaż <xref:System.IO.StreamReader> klasy implementuje <xref:System.IDisposable> interfejs, który wskazuje, że używa niezarządzany zasób, nie jest jawnie wywoływana przykład <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="751e8-113">Note that although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="751e8-114">Gdy kompilator języka C# lub Visual Basic napotyka `using` instrukcji, emituje języka pośredniego (IL), który jest odpowiednikiem następujący kod, który jawnie zawiera `try/finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="751e8-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
<span data-ttu-id="751e8-115">C# `using` instrukcji umożliwia również nabywanie wielu zasobów w pojedynczej instrukcji, co stanowi wewnętrzny odpowiednik zagnieżdżonych `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="751e8-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="751e8-116">Poniższy przykład tworzy dwie <xref:System.IO.StreamReader> obiektów w celu odczytania zawartości dwóch różnych plikach.</span><span class="sxs-lookup"><span data-stu-id="751e8-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="751e8-117">Blok try/finally</span><span class="sxs-lookup"><span data-stu-id="751e8-117">Try/finally block</span></span>

<span data-ttu-id="751e8-118">Zamiast umieszczać `try/finally` bloku `using` instrukcji może zadecydować o stosowaniu `try/finally` zablokować bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="751e8-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="751e8-119">Może to wynikać z osobistego stylu kodowania albo mieć jedną z następujących przyczyn:</span><span class="sxs-lookup"><span data-stu-id="751e8-119">This may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>  
  
* <span data-ttu-id="751e8-120">Aby uwzględnić `catch` bloku w celu obsługi wszystkich wyjątków zgłaszanych `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="751e8-120">To include a `catch` block to handle any exceptions thrown in the `try` block.</span></span> <span data-ttu-id="751e8-121">W przeciwnym razie wyjątki zgłaszane przez `using` instrukcji są obsługiwane, podobnie jak wyjątki zgłaszane w `using` zablokować, jeśli `try/catch` blok nie jest obecny.</span><span class="sxs-lookup"><span data-stu-id="751e8-121">Otherwise, any exceptions thrown by the `using` statement are unhandled, as are any exceptions thrown within the `using` block if a `try/catch` block isn't present.</span></span>  
  
* <span data-ttu-id="751e8-122">Aby utworzyć wystąpienie obiektu, który implementuje <xref:System.IDisposable> którego zakres nie jest lokalnym bloku, w którym jest zdeklarowana.</span><span class="sxs-lookup"><span data-stu-id="751e8-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>  
  
<span data-ttu-id="751e8-123">Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że używa `try/catch/finally` bloku, aby utworzyć wystąpienie, używanie i usuwanie <xref:System.IO.StreamReader> obiekt oraz do obsługi wszystkich wyjątków zgłaszanych przez <xref:System.IO.StreamReader> Konstruktor i jego <xref:System.IO.StreamReader.ReadToEnd%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="751e8-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="751e8-124">Należy pamiętać, że kod w `finally` bloku sprawdza, czy obiekt implementujący <xref:System.IDisposable> nie jest `null` przed wywołaniem <xref:System.IDisposable.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="751e8-124">Note that the code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="751e8-125">Niewykonanie tej czynności to może spowodować <xref:System.NullReferenceException> wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="751e8-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
<span data-ttu-id="751e8-126">Możesz wykonać tego podstawowego wzorca, jeśli zadecydować o stosowaniu lub musi implementować `try/finally` zablokować, ponieważ nie obsługuje języka programowania `using` instrukcji, ale zezwala na bezpośrednie wywołania do <xref:System.IDisposable.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="751e8-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="751e8-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="751e8-127">See also</span></span>

- [<span data-ttu-id="751e8-128">Oczyszczanie zasobów niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="751e8-128">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
- [<span data-ttu-id="751e8-129">Using — instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="751e8-129">using Statement (C# Reference)</span></span>](~/docs/csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="751e8-130">Using — instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="751e8-130">Using Statement (Visual Basic)</span></span>](~/docs/visual-basic/language-reference/statements/using-statement.md)
