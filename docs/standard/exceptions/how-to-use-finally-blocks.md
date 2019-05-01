---
title: 'Instrukcje: Użycie bloków finally'
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
ms.openlocfilehash: 213ab53c68a37ac0ba5f337a1d6fc32bfe6f8989
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970914"
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="f9a82-102">Jak użycie bloków finally</span><span class="sxs-lookup"><span data-stu-id="f9a82-102">How to use finally blocks</span></span>

<span data-ttu-id="f9a82-103">Gdy wystąpi wyjątek, zatrzymuje wykonywanie i kontrola otrzymuje do obsługi odpowiednich wyjątków.</span><span class="sxs-lookup"><span data-stu-id="f9a82-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="f9a82-104">Często oznacza to, że są pomijane wiersze kodu, których oczekujesz, że do wykonania.</span><span class="sxs-lookup"><span data-stu-id="f9a82-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="f9a82-105">Niektóre czyszczenie zasobów, takich jak zamykania pliku musi odbywać się nawet wtedy, gdy wyjątek jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="f9a82-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="f9a82-106">Aby to zrobić, można użyć `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="f9a82-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="f9a82-107">A `finally` blok zawsze jest wykonywany, niezależnie od tego, czy wyjątek jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="f9a82-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="f9a82-108">Poniższy przykład kodu wykorzystuje `try` / `catch` bloku catch <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="f9a82-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="f9a82-109">`Main` Metoda tworzy dwie tablice i próbuje skopiować jednego do drugiego.</span><span class="sxs-lookup"><span data-stu-id="f9a82-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="f9a82-110">Akcja generuje <xref:System.ArgumentOutOfRangeException> i jest on zapisywany w konsoli.</span><span class="sxs-lookup"><span data-stu-id="f9a82-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="f9a82-111">`finally` Blok jest wykonywany niezależnie od tego, w wyniku akcji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="f9a82-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="f9a82-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9a82-112">See also</span></span>

- [<span data-ttu-id="f9a82-113">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="f9a82-113">Exceptions</span></span>](index.md)
