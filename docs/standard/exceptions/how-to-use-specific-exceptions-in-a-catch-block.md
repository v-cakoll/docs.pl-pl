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
ms.openlocfilehash: 48b450e579263876725f96e0adfc4c16aac1d869
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160160"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="844dd-102">Jak używać określonych wyjątków w bloku catch</span><span class="sxs-lookup"><span data-stu-id="844dd-102">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="844dd-103">Ogólnie rzecz biorąc jest dobrą praktyką programowania, aby przechwycić określony `catch` typ wyjątku, a nie użyć podstawowej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="844dd-103">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="844dd-104">Po wystąpieniu wyjątku jest przekazywana do stosu i każdy blok catch ma możliwość obsługi go.</span><span class="sxs-lookup"><span data-stu-id="844dd-104">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="844dd-105">Kolejność instrukcji połowowych jest ważna.</span><span class="sxs-lookup"><span data-stu-id="844dd-105">The order of catch statements is important.</span></span> <span data-ttu-id="844dd-106">Umieść catch bloki przeznaczone do określonych wyjątków przed ogólnym bloku catch wyjątku lub kompilator może wystawiać błąd.</span><span class="sxs-lookup"><span data-stu-id="844dd-106">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="844dd-107">Właściwy blok catch jest określana przez dopasowanie typu wyjątku do nazwy wyjątku określonego w bloku catch.</span><span class="sxs-lookup"><span data-stu-id="844dd-107">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="844dd-108">Jeśli nie ma żadnego określonego bloku catch, wyjątek jest przechwycone przez ogólny blok catch, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="844dd-108">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="844dd-109">Poniższy przykład kodu `try` / `catch` używa bloku <xref:System.InvalidCastException>do połowu .</span><span class="sxs-lookup"><span data-stu-id="844dd-109">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="844dd-110">Przykład tworzy klasę `Employee` o nazwie z jednej`Emlevel`właściwości, poziom pracownika ( ).</span><span class="sxs-lookup"><span data-stu-id="844dd-110">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="844dd-111">Metoda , `PromoteEmployee`przyjmuje obiekt i zwiększa poziom pracownika.</span><span class="sxs-lookup"><span data-stu-id="844dd-111">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="844dd-112">Występuje, <xref:System.InvalidCastException> gdy <xref:System.DateTime> wystąpienie jest `PromoteEmployee` przekazywane do metody.</span><span class="sxs-lookup"><span data-stu-id="844dd-112">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="844dd-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="844dd-113">See also</span></span>

- [<span data-ttu-id="844dd-114">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="844dd-114">Exceptions</span></span>](index.md)
