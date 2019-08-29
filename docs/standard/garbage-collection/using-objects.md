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
ms.openlocfilehash: 9f165ab5b79abbc2b5464f40a27a580d26af163a
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106952"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="56e49-102">Używanie obiektów implementujących interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="56e49-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="56e49-103">Moduł zbierający elementy bezużyteczne środowiska uruchomieniowego języka wspólnego ponownie przejmuje pamięć używaną przez zarządzane obiekty, ale typy korzystające z zasobów niezarządzanych implementują <xref:System.IDisposable> interfejs, aby umożliwić odzyskanie pamięci przydzielonej do tych niezarządzanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="56e49-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the memory allocated to these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="56e49-104">Po zakończeniu korzystania z obiektu, który implementuje <xref:System.IDisposable>, należy wywołać <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementację obiektu.</span><span class="sxs-lookup"><span data-stu-id="56e49-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="56e49-105">Można to zrobić na jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="56e49-105">You can do this in one of two ways:</span></span>  
  
- <span data-ttu-id="56e49-106">C# `Using` Za pomocą instrukcjilub`using` instrukcji Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="56e49-106">With the C# `using` statement or the Visual Basic `Using` statement.</span></span>  
  
- <span data-ttu-id="56e49-107">Przez implementację `try/finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="56e49-107">By implementing a `try/finally` block.</span></span>  

## <a name="the-using-statement"></a><span data-ttu-id="56e49-108">Instrukcja using</span><span class="sxs-lookup"><span data-stu-id="56e49-108">The using statement</span></span>

<span data-ttu-id="56e49-109">Instrukcja w C# i`Using` instrukcji w Visual Basic upraszcza kod, który należy napisać, aby utworzyć i oczyścić obiekt. `using`</span><span class="sxs-lookup"><span data-stu-id="56e49-109">The `using` statement in C# and the `Using` statement in Visual Basic simplify the code that you must write to create and clean up an object.</span></span> <span data-ttu-id="56e49-110">`using` Instrukcja uzyskuje jeden lub więcej zasobów, wykonuje określone instrukcje i automatycznie usuwa obiekt.</span><span class="sxs-lookup"><span data-stu-id="56e49-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="56e49-111">`using` Jednak instrukcja jest przydatna tylko w przypadku obiektów, które są używane w zakresie metody, w której są zbudowane.</span><span class="sxs-lookup"><span data-stu-id="56e49-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>  
  
<span data-ttu-id="56e49-112">Poniższy przykład używa `using` instrukcji w celu utworzenia i <xref:System.IO.StreamReader?displayProperty=nameWithType> zwolnienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="56e49-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<span data-ttu-id="56e49-113">Należy zauważyć, że <xref:System.IO.StreamReader> mimo że Klasa <xref:System.IDisposable> implementuje interfejs, który wskazuje, że używa niezarządzanego zasobu, <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> przykład nie wywołuje jawnie metody.</span><span class="sxs-lookup"><span data-stu-id="56e49-113">Note that although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="56e49-114">Gdy kompilator C# lub Visual Basic napotka `using` instrukcję, emituje języka pośredniego (IL), który jest równoważny do poniższego kodu `try/finally` , który jawnie zawiera blok.</span><span class="sxs-lookup"><span data-stu-id="56e49-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
<span data-ttu-id="56e49-115">Instrukcja umożliwia także uzyskanie wielu zasobów w pojedynczej instrukcji, która jest wewnętrznie odpowiednikiem zagnieżdżonych `using` instrukcji. C# `using`</span><span class="sxs-lookup"><span data-stu-id="56e49-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="56e49-116">Poniższy przykład tworzy wystąpienie dwóch <xref:System.IO.StreamReader> obiektów w celu odczytania zawartości dwóch różnych plików.</span><span class="sxs-lookup"><span data-stu-id="56e49-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="56e49-117">Blok try/finally</span><span class="sxs-lookup"><span data-stu-id="56e49-117">Try/finally block</span></span>

<span data-ttu-id="56e49-118">Zamiast zawijać `try/finally` blok `using` w instrukcji, możesz wybrać opcję bezpośredniego wdrożenia `try/finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="56e49-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="56e49-119">Może to wynikać z osobistego stylu kodowania albo mieć jedną z następujących przyczyn:</span><span class="sxs-lookup"><span data-stu-id="56e49-119">This may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>  
  
- <span data-ttu-id="56e49-120">Aby dołączyć `catch` blok obsługujący wyjątki zgłoszone `try` w bloku.</span><span class="sxs-lookup"><span data-stu-id="56e49-120">To include a `catch` block to handle any exceptions thrown in the `try` block.</span></span> <span data-ttu-id="56e49-121">W przeciwnym razie wszelkie wyjątki zgłoszone `using` przez instrukcję są nieobsługiwane, ponieważ są to wyjątki zgłoszone `using` w bloku, jeśli `try/catch` blok nie jest obecny.</span><span class="sxs-lookup"><span data-stu-id="56e49-121">Otherwise, any exceptions thrown by the `using` statement are unhandled, as are any exceptions thrown within the `using` block if a `try/catch` block isn't present.</span></span>  
  
- <span data-ttu-id="56e49-122">Aby utworzyć wystąpienie obiektu, który <xref:System.IDisposable> implementuje, którego zakres nie jest lokalny dla bloku, w którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="56e49-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>  
  
<span data-ttu-id="56e49-123">Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że `try/catch/finally` używa bloku do tworzenia wystąpienia, używania i usuwania <xref:System.IO.StreamReader> obiektu oraz do obsługi <xref:System.IO.StreamReader> wszelkich wyjątków zgłoszonych przez konstruktora i jego <xref:System.IO.StreamReader.ReadToEnd%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="56e49-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="56e49-124">Należy zauważyć, że kod w `finally` bloku sprawdza, czy obiekt, który <xref:System.IDisposable> implementuje `null` , <xref:System.IDisposable.Dispose%2A> nie jest przed wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="56e49-124">Note that the code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="56e49-125">Niewykonanie tej czynności może spowodować <xref:System.NullReferenceException> wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="56e49-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
<span data-ttu-id="56e49-126">Możesz użyć tego podstawowego wzorca, jeśli zdecydujesz się zaimplementować lub musi zaimplementować `try/finally` blok, ponieważ język programowania nie `using` obsługuje instrukcji, ale <xref:System.IDisposable.Dispose%2A> zezwala na bezpośrednie wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="56e49-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="56e49-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56e49-127">See also</span></span>

- [<span data-ttu-id="56e49-128">Oczyszczanie zasobów niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="56e49-128">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
- [<span data-ttu-id="56e49-129">using — instrukcjaC# (Reference)</span><span class="sxs-lookup"><span data-stu-id="56e49-129">using Statement (C# Reference)</span></span>](../../csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="56e49-130">Using — instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56e49-130">Using Statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/using-statement.md)
