---
title: "Porady: jawne zgłaszanie wyjątków"
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
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 02576db4b9920a367ac3111f2c2c49989ea45149
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="9425f-102">Jak jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="9425f-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="9425f-103">Można jawne zgłaszanie wyjątków za pomocą `throw` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9425f-103">You can explicitly throw an exception using the `throw` statement.</span></span> <span data-ttu-id="9425f-104">Można również zgłosić wyjątek zgłoszony ponownie, używając `throw` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9425f-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="9425f-105">Jest dobrym rozwiązaniem, aby dodać informacje do wyjątek, który jest zgłoszony ponownie o podanie dodatkowych informacji podczas debugowania kodu.</span><span class="sxs-lookup"><span data-stu-id="9425f-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="9425f-106">Poniższy przykład kodu wykorzystuje `try` / `catch` bloku catch potencjalnie <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="9425f-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="9425f-107">Po `try` blok `catch` bloku, który przechwytuje <xref:System.IO.FileNotFoundException> i zapisuje komunikat w konsoli, jeśli nie znaleziono pliku danych.</span><span class="sxs-lookup"><span data-stu-id="9425f-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="9425f-108">Następna instrukcja jest `throw` instrukcji, która zwraca nową <xref:System.IO.FileNotFoundException> i dodaje informacje tekstowe wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9425f-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="9425f-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9425f-109">See Also</span></span>  
[<span data-ttu-id="9425f-110">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="9425f-110">Exceptions</span></span>](index.md)
