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
ms.openlocfilehash: c5232aa89064c514e71f3a18bc754159e9c9b15b
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160287"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="0790a-102">Używanie obiektów implementujących interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="0790a-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="0790a-103">Moduł wyrzucania elementów bezużytecznych środowiska uruchomieniowego języka wspólnego nie przejmuje pamięci używanej przez zarządzane obiekty, ale typy korzystające z zasobów niezarządzanych implementują interfejs <xref:System.IDisposable>, aby umożliwić odzyskanie pamięci przydzielonej do tych niezarządzanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="0790a-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the memory allocated to these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="0790a-104">Po zakończeniu korzystania z obiektu, który implementuje <xref:System.IDisposable>, należy wywołać implementację <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0790a-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="0790a-105">Można to zrobić na jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="0790a-105">You can do this in one of two ways:</span></span>  
  
- <span data-ttu-id="0790a-106">Za pomocą C# instrukcji `using` lub instrukcji Visual Basic `Using`.</span><span class="sxs-lookup"><span data-stu-id="0790a-106">With the C# `using` statement or the Visual Basic `Using` statement.</span></span>  
  
- <span data-ttu-id="0790a-107">Implementując blok `try/finally`.</span><span class="sxs-lookup"><span data-stu-id="0790a-107">By implementing a `try/finally` block.</span></span>  

## <a name="the-using-statement"></a><span data-ttu-id="0790a-108">Instrukcja using</span><span class="sxs-lookup"><span data-stu-id="0790a-108">The using statement</span></span>

<span data-ttu-id="0790a-109">Instrukcja `using` w C# i instrukcji `Using` w Visual Basic upraszcza kod, który należy napisać, aby utworzyć i oczyścić obiekt.</span><span class="sxs-lookup"><span data-stu-id="0790a-109">The `using` statement in C# and the `Using` statement in Visual Basic simplify the code that you must write to create and clean up an object.</span></span> <span data-ttu-id="0790a-110">Instrukcja `using` uzyskuje jeden lub więcej zasobów, wykonuje określone instrukcje i automatycznie usuwa obiekt.</span><span class="sxs-lookup"><span data-stu-id="0790a-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="0790a-111">Jednakże instrukcja `using` jest przydatna tylko w przypadku obiektów, które są używane w zakresie metody, w której są zbudowane.</span><span class="sxs-lookup"><span data-stu-id="0790a-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>  
  
<span data-ttu-id="0790a-112">Poniższy przykład używa instrukcji `using` w celu utworzenia i zwolnienia obiektu <xref:System.IO.StreamReader?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0790a-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<span data-ttu-id="0790a-113">Należy zauważyć, że chociaż Klasa <xref:System.IO.StreamReader> implementuje interfejs <xref:System.IDisposable>, co oznacza, że używa niezarządzanego zasobu, przykład nie wywołuje jawnie metody <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0790a-113">Note that although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0790a-114">Gdy kompilator C# lub Visual Basic napotka instrukcję `using`, emituje języka pośredniego (IL), który jest odpowiednikiem poniższego kodu, który jawnie zawiera blok `try/finally`.</span><span class="sxs-lookup"><span data-stu-id="0790a-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
<span data-ttu-id="0790a-115">Instrukcja C# `using` umożliwia także uzyskanie wielu zasobów w pojedynczej instrukcji, która jest wewnętrznie odpowiednikiem zagnieżdżonych instrukcji `using`.</span><span class="sxs-lookup"><span data-stu-id="0790a-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="0790a-116">Poniższy przykład tworzy wystąpienie dwóch <xref:System.IO.StreamReader> obiektów w celu odczytania zawartości dwóch różnych plików.</span><span class="sxs-lookup"><span data-stu-id="0790a-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="0790a-117">Blok try/finally</span><span class="sxs-lookup"><span data-stu-id="0790a-117">Try/finally block</span></span>

<span data-ttu-id="0790a-118">Zamiast zawijać blok `try/finally` w instrukcji `using`, można wybrać opcję bezpośredniego wdrożenia bloku `try/finally`.</span><span class="sxs-lookup"><span data-stu-id="0790a-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="0790a-119">Może to wynikać z osobistego stylu kodowania albo mieć jedną z następujących przyczyn:</span><span class="sxs-lookup"><span data-stu-id="0790a-119">This may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>  
  
- <span data-ttu-id="0790a-120">Aby dołączyć blok `catch` do obsługi wyjątków zgłoszonych w bloku `try`.</span><span class="sxs-lookup"><span data-stu-id="0790a-120">To include a `catch` block to handle any exceptions thrown in the `try` block.</span></span> <span data-ttu-id="0790a-121">W przeciwnym razie wszelkie wyjątki zgłoszone przez instrukcję `using` są nieobsługiwane, ponieważ są to wyjątki zgłoszone w bloku `using`, jeśli blok `try/catch` nie jest obecny.</span><span class="sxs-lookup"><span data-stu-id="0790a-121">Otherwise, any exceptions thrown by the `using` statement are unhandled, as are any exceptions thrown within the `using` block if a `try/catch` block isn't present.</span></span>  
  
- <span data-ttu-id="0790a-122">Aby utworzyć wystąpienie obiektu, który implementuje <xref:System.IDisposable> którego zakres nie jest lokalny dla bloku, w którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="0790a-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>  
  
<span data-ttu-id="0790a-123">Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że używa bloku `try/catch/finally` do tworzenia wystąpienia, używania i usuwania obiektu <xref:System.IO.StreamReader> oraz do obsługi wyjątków zgłoszonych przez konstruktora <xref:System.IO.StreamReader> i jego metody <xref:System.IO.StreamReader.ReadToEnd%2A>.</span><span class="sxs-lookup"><span data-stu-id="0790a-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="0790a-124">Należy zauważyć, że kod w bloku `finally` sprawdza, czy obiekt implementujący <xref:System.IDisposable> nie jest `null` przed wywołaniem metody <xref:System.IDisposable.Dispose%2A>.</span><span class="sxs-lookup"><span data-stu-id="0790a-124">Note that the code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="0790a-125">Niewykonanie tej czynności może spowodować <xref:System.NullReferenceException> wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0790a-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
<span data-ttu-id="0790a-126">Ten podstawowy wzorzec można wykonać, jeśli zdecydujesz się zaimplementować lub zaimplementować blok `try/finally`, ponieważ język programowania nie obsługuje instrukcji `using`, ale zezwala na bezpośrednie wywołania metody <xref:System.IDisposable.Dispose%2A>.</span><span class="sxs-lookup"><span data-stu-id="0790a-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0790a-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0790a-127">See also</span></span>

- [<span data-ttu-id="0790a-128">Oczyszczanie zasobów niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="0790a-128">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
- [<span data-ttu-id="0790a-129">using — instrukcjaC# (Reference)</span><span class="sxs-lookup"><span data-stu-id="0790a-129">using Statement (C# Reference)</span></span>](../../csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="0790a-130">Using — instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0790a-130">Using Statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/using-statement.md)
