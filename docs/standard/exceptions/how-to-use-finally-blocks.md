---
title: "Porady: użycie bloków finally"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b303582a62f211091b1ebee0e88cf380da8b03d9
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="7bc7c-102">Jak użycie bloków finally</span><span class="sxs-lookup"><span data-stu-id="7bc7c-102">How to use finally blocks</span></span>

<span data-ttu-id="7bc7c-103">Po wystąpieniu wyjątku, zatrzymuje wykonywanie i kontroli podano do obsługi odpowiednich wyjątków.</span><span class="sxs-lookup"><span data-stu-id="7bc7c-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="7bc7c-104">Często oznacza to, że wiersze kodu, który może być wykonywane są pomijane.</span><span class="sxs-lookup"><span data-stu-id="7bc7c-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="7bc7c-105">Porządkowanie zasobów, np. zamknięcie pliku, należy wykonać, nawet jeśli jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7bc7c-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="7bc7c-106">Aby to zrobić, można użyć `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="7bc7c-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="7bc7c-107">A `finally` bloku zawsze wykonywana, niezależnie od tego, czy jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7bc7c-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="7bc7c-108">Poniższy przykład kodu wykorzystuje `try` / `catch` bloku catch <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="7bc7c-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="7bc7c-109">`Main` Metoda tworzy dwie tablice i próbuje skopiować je do innych.</span><span class="sxs-lookup"><span data-stu-id="7bc7c-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="7bc7c-110">Akcja generuje <xref:System.ArgumentOutOfRangeException> i jest on zapisywany do konsoli.</span><span class="sxs-lookup"><span data-stu-id="7bc7c-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="7bc7c-111">`finally` Bloku wykonuje niezależnie od wyniku akcji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="7bc7c-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="7bc7c-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7bc7c-112">See Also</span></span>  
[<span data-ttu-id="7bc7c-113">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="7bc7c-113">Exceptions</span></span>](index.md)   
