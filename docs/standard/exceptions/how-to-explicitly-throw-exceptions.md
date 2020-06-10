---
title: 'Porady: jawne zgłaszanie wyjątków'
description: Dowiedz się, jak zgłosić wyjątek jawnie w programie .NET przy użyciu instrukcji throw języka C# lub instrukcji Visual Basic throw.
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
ms.openlocfilehash: 2dd939f9edd58ba91ea74df5d6930087849f0560
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662787"
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="87b97-103">Jak jawnie zgłosić wyjątki</span><span class="sxs-lookup"><span data-stu-id="87b97-103">How to explicitly throw exceptions</span></span>

<span data-ttu-id="87b97-104">Wyjątek można jawnie zgłosić przy użyciu języka C# [`throw`](../../csharp/language-reference/keywords/throw.md) lub [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) instrukcji Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="87b97-104">You can explicitly throw an exception using the C# [`throw`](../../csharp/language-reference/keywords/throw.md) or the Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) statement.</span></span> <span data-ttu-id="87b97-105">Można również zgłosić przechwycony wyjątek ponownie, używając `throw` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="87b97-105">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="87b97-106">Dobrym sposobem kodowania jest dodanie informacji do wyjątku, który został ponownie wygenerowany, aby uzyskać więcej informacji podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="87b97-106">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="87b97-107">Poniższy przykład kodu używa bloku, `try` / `catch` Aby przechwycić możliwe <xref:System.IO.FileNotFoundException> .</span><span class="sxs-lookup"><span data-stu-id="87b97-107">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="87b97-108">Po `try` bloku jest `catch` blok, który przechwytuje <xref:System.IO.FileNotFoundException> i zapisuje komunikat w konsoli, jeśli plik danych nie zostanie znaleziony.</span><span class="sxs-lookup"><span data-stu-id="87b97-108">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="87b97-109">Następna instrukcja to `throw` instrukcja, która zgłasza nowe <xref:System.IO.FileNotFoundException> i dodaje do wyjątku informacje tekstowe.</span><span class="sxs-lookup"><span data-stu-id="87b97-109">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="87b97-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87b97-110">See also</span></span>

- [<span data-ttu-id="87b97-111">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="87b97-111">Exceptions</span></span>](index.md)
