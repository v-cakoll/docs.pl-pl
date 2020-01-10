---
title: 'Porady: użycie określonych wyjątków w bloku CATCH'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
ms.openlocfilehash: 6f0956c6418d894a5768463861151f86a1948850
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708584"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="d7605-102">Jak używać określonych wyjątków w bloku catch</span><span class="sxs-lookup"><span data-stu-id="d7605-102">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="d7605-103">Ogólnie rzecz biorąc, dobrym sposobem programowania jest przechwycenie określonego typu wyjątku zamiast używania podstawowej instrukcji `catch`.</span><span class="sxs-lookup"><span data-stu-id="d7605-103">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="d7605-104">Gdy wystąpi wyjątek, zostanie przekazany stos, a każdy blok catch otrzymuje szansę na jego obsługę.</span><span class="sxs-lookup"><span data-stu-id="d7605-104">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="d7605-105">Kolejność instrukcji catch jest ważna.</span><span class="sxs-lookup"><span data-stu-id="d7605-105">The order of catch statements is important.</span></span> <span data-ttu-id="d7605-106">Umieść bloki catch skierowane do określonych wyjątków przed ogólnym blokiem catch wyjątku lub kompilator może wydać błąd.</span><span class="sxs-lookup"><span data-stu-id="d7605-106">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="d7605-107">Odpowiedni blok catch jest określany przez dopasowanie typu wyjątku do nazwy wyjątku określonego w bloku catch.</span><span class="sxs-lookup"><span data-stu-id="d7605-107">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="d7605-108">Jeśli nie ma określonego bloku catch, wyjątek jest przechwytywany przez ogólny blok catch, jeśli taki istnieje.</span><span class="sxs-lookup"><span data-stu-id="d7605-108">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="d7605-109">Poniższy przykład kodu używa bloku `try`/`catch` do przechwytywania <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="d7605-109">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="d7605-110">Przykład tworzy klasę o nazwie `Employee` z pojedynczą właściwością na poziomie pracownika (`Emlevel`).</span><span class="sxs-lookup"><span data-stu-id="d7605-110">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="d7605-111">Metoda `PromoteEmployee`, przyjmuje obiekt i zwiększa poziom pracownika.</span><span class="sxs-lookup"><span data-stu-id="d7605-111">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="d7605-112"><xref:System.InvalidCastException> występuje, gdy wystąpienie <xref:System.DateTime> zostanie przesłane do metody `PromoteEmployee`.</span><span class="sxs-lookup"><span data-stu-id="d7605-112">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a><span data-ttu-id="d7605-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7605-113">See also</span></span>

- [<span data-ttu-id="d7605-114">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="d7605-114">Exceptions</span></span>](index.md)
