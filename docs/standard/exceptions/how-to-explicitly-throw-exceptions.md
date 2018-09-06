---
title: 'Porady: jawne zgłaszanie wyjątków'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a1a8658999f08d295e76afc9df6ec8acd146abe2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863229"
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="ed567-102">Jak jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="ed567-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="ed567-103">Można jawnie zgłosić wyjątek za pomocą `throw` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ed567-103">You can explicitly throw an exception using the `throw` statement.</span></span> <span data-ttu-id="ed567-104">Może również zgłosić wyjątek zgłoszony ponownie, używając `throw` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ed567-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="ed567-105">Jest dobrą praktyką, aby dodać informacje do wyjątek, który jest zgłoszony ponownie, aby dostarczyć dodatkowych informacji podczas debugowania kodu.</span><span class="sxs-lookup"><span data-stu-id="ed567-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="ed567-106">Poniższy przykład kodu wykorzystuje `try` / `catch` bloku catch możliwe <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="ed567-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="ed567-107">Następujące `try` blok `catch` blok, który przechwytuje <xref:System.IO.FileNotFoundException> i zapisuje komunikat w konsoli, jeśli nie można odnaleźć pliku danych.</span><span class="sxs-lookup"><span data-stu-id="ed567-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="ed567-108">Następna instrukcja znajduje się `throw` instrukcji generującej nową <xref:System.IO.FileNotFoundException> i dodaje informacje tekstowe do wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ed567-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="ed567-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed567-109">See also</span></span>

- [<span data-ttu-id="ed567-110">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="ed567-110">Exceptions</span></span>](index.md)
