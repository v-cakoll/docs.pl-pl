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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3da35dae374018f0695f79022e83ad397e98cb88
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874787"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="18fa9-102">Jak używać określonych wyjątków w bloku catch</span><span class="sxs-lookup"><span data-stu-id="18fa9-102">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="18fa9-103">Ogólnie rzecz biorąc, jest dobrą praktyką catch konkretny typ wyjątku, zamiast używać podstawowego programowania `catch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="18fa9-103">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="18fa9-104">Po wystąpieniu wyjątku jest przekazywany górę stosu, a każdy blok catch jest możliwość go obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="18fa9-104">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="18fa9-105">Kolejność instrukcji catch jest ważna.</span><span class="sxs-lookup"><span data-stu-id="18fa9-105">The order of catch statements is important.</span></span> <span data-ttu-id="18fa9-106">Umieść bloki catch przeznaczone dla określonych wyjątków, przed blokiem catch ogólny wyjątek lub kompilator może wydać błąd.</span><span class="sxs-lookup"><span data-stu-id="18fa9-106">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="18fa9-107">Blok catch właściwej jest określany przez dopasowanie typu wyjątku do nazwy wystąpienia wyjątku określonego w bloku catch.</span><span class="sxs-lookup"><span data-stu-id="18fa9-107">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="18fa9-108">W przypadku nie blok catch określonych wyjątek zostaje przechwycony przez ogólnego bloku catch, jeśli taka istnieje.</span><span class="sxs-lookup"><span data-stu-id="18fa9-108">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="18fa9-109">Poniższy przykład kodu wykorzystuje `try` / `catch` bloku catch <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="18fa9-109">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="18fa9-110">Przykładowa aplikacja tworzy klasę o nazwie `Employee` z tylko jedną właściwość poziom pracownika (`Emlevel`).</span><span class="sxs-lookup"><span data-stu-id="18fa9-110">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="18fa9-111">Metoda `PromoteEmployee`, przyjmuje obiekt i zwiększa poziom pracownika.</span><span class="sxs-lookup"><span data-stu-id="18fa9-111">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="18fa9-112"><xref:System.InvalidCastException> Występuje, gdy <xref:System.DateTime> wystąpienia jest przekazywany do `PromoteEmployee` metody.</span><span class="sxs-lookup"><span data-stu-id="18fa9-112">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a><span data-ttu-id="18fa9-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18fa9-113">See also</span></span>

- [<span data-ttu-id="18fa9-114">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="18fa9-114">Exceptions</span></span>](index.md)
