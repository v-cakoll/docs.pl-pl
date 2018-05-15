---
title: 'Porady: użycie bloków finally'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- exceptions, finally blocks
- try/catch blocks
- finally blocks
- ArgumentOutOfRangeException class
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dff1083256e24a35b7238ee5e8af6cb5743bc0ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="618c4-102">Jak użycie bloków finally</span><span class="sxs-lookup"><span data-stu-id="618c4-102">How to use finally blocks</span></span>

<span data-ttu-id="618c4-103">Po wystąpieniu wyjątku, zatrzymuje wykonywanie i kontroli podano do obsługi odpowiednich wyjątków.</span><span class="sxs-lookup"><span data-stu-id="618c4-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="618c4-104">Często oznacza to, że wiersze kodu, który może być wykonywane są pomijane.</span><span class="sxs-lookup"><span data-stu-id="618c4-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="618c4-105">Porządkowanie zasobów, np. zamknięcie pliku, należy wykonać, nawet jeśli jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="618c4-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="618c4-106">Aby to zrobić, można użyć `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="618c4-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="618c4-107">A `finally` bloku zawsze wykonywana, niezależnie od tego, czy jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="618c4-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="618c4-108">Poniższy przykład kodu wykorzystuje `try` / `catch` bloku catch <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="618c4-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="618c4-109">`Main` Metoda tworzy dwie tablice i próbuje skopiować je do innych.</span><span class="sxs-lookup"><span data-stu-id="618c4-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="618c4-110">Akcja generuje <xref:System.ArgumentOutOfRangeException> i jest on zapisywany do konsoli.</span><span class="sxs-lookup"><span data-stu-id="618c4-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="618c4-111">`finally` Bloku wykonuje niezależnie od wyniku akcji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="618c4-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="618c4-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="618c4-112">See Also</span></span>  
[<span data-ttu-id="618c4-113">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="618c4-113">Exceptions</span></span>](index.md)   
