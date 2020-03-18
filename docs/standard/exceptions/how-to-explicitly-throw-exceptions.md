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
ms.openlocfilehash: 750da20b8c1c40901cc363ac0eff8af888821ce9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708865"
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="d4fc1-102">Jak jawnie zgłaszać wyjątki</span><span class="sxs-lookup"><span data-stu-id="d4fc1-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="d4fc1-103">Jawnie można zgłosić wyjątek przy [`throw`](../../csharp/language-reference/keywords/throw.md) użyciu c# [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) lub Visual Basic instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d4fc1-103">You can explicitly throw an exception using the C# [`throw`](../../csharp/language-reference/keywords/throw.md) or the Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) statement.</span></span> <span data-ttu-id="d4fc1-104">Można również zgłosić przechwyconego wyjątku ponownie przy użyciu `throw` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d4fc1-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="d4fc1-105">Dobrą praktyką kodowania jest dodawanie informacji do wyjątku, który jest ponownie generowany, aby zapewnić więcej informacji podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="d4fc1-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="d4fc1-106">Poniższy przykład kodu `try` / `catch` używa bloku do <xref:System.IO.FileNotFoundException>połowu możliwe .</span><span class="sxs-lookup"><span data-stu-id="d4fc1-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="d4fc1-107">Po `try` bloku jest `catch` blok, <xref:System.IO.FileNotFoundException> który przechwytuje i zapisuje wiadomość do konsoli, jeśli plik danych nie zostanie znaleziony.</span><span class="sxs-lookup"><span data-stu-id="d4fc1-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="d4fc1-108">Następna instrukcja `throw` jest instrukcja, <xref:System.IO.FileNotFoundException> która zgłasza nowy i dodaje informacje tekstowe do wyjątku.</span><span class="sxs-lookup"><span data-stu-id="d4fc1-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="d4fc1-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4fc1-109">See also</span></span>

- [<span data-ttu-id="d4fc1-110">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="d4fc1-110">Exceptions</span></span>](index.md)
