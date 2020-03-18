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
ms.openlocfilehash: 44fbb53437c4c8f19a424227a167e2e268b77057
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708835"
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="851c7-102">Jak używać wreszcie bloków</span><span class="sxs-lookup"><span data-stu-id="851c7-102">How to use finally blocks</span></span>

<span data-ttu-id="851c7-103">W przypadku wystąpienia wyjątku, wykonywanie zatrzymuje się i kontroli jest podana do obsługi wyjątków odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="851c7-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="851c7-104">Często oznacza to, że wiersze kodu, które mają być wykonywane są pomijane.</span><span class="sxs-lookup"><span data-stu-id="851c7-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="851c7-105">Niektóre oczyszczania zasobów, takich jak zamknięcie pliku, musi być wykonane, nawet jeśli wyjątek.</span><span class="sxs-lookup"><span data-stu-id="851c7-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="851c7-106">Aby to zrobić, można `finally` użyć bloku.</span><span class="sxs-lookup"><span data-stu-id="851c7-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="851c7-107">Blok `finally` zawsze jest wykonywany, niezależnie od tego, czy wyjątek jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="851c7-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="851c7-108">Poniższy przykład kodu `try` / `catch` używa bloku <xref:System.ArgumentOutOfRangeException>do połowu .</span><span class="sxs-lookup"><span data-stu-id="851c7-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="851c7-109">Metoda `Main` tworzy dwie tablice i próbuje skopiować jedną do drugiej.</span><span class="sxs-lookup"><span data-stu-id="851c7-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="851c7-110">Akcja generuje i <xref:System.ArgumentOutOfRangeException> błąd jest zapisywany w konsoli.</span><span class="sxs-lookup"><span data-stu-id="851c7-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="851c7-111">Blok `finally` jest wykonywany niezależnie od wyniku akcji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="851c7-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="851c7-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="851c7-112">See also</span></span>

- [<span data-ttu-id="851c7-113">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="851c7-113">Exceptions</span></span>](index.md)
