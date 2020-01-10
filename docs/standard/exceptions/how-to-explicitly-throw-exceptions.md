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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708865"
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="8e305-102">Jak jawnie zgłosić wyjątki</span><span class="sxs-lookup"><span data-stu-id="8e305-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="8e305-103">Wyjątek można jawnie zgłosić przy użyciu C# [`throw`](../../csharp/language-reference/keywords/throw.md) lub instrukcji Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="8e305-103">You can explicitly throw an exception using the C# [`throw`](../../csharp/language-reference/keywords/throw.md) or the Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) statement.</span></span> <span data-ttu-id="8e305-104">Przechwycony wyjątek można również zgłosić ponownie, używając instrukcji `throw`.</span><span class="sxs-lookup"><span data-stu-id="8e305-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="8e305-105">Dobrym sposobem kodowania jest dodanie informacji do wyjątku, który został ponownie wygenerowany, aby uzyskać więcej informacji podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="8e305-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="8e305-106">Poniższy przykład kodu używa bloku `try`/`catch`, aby przechwycić możliwe <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="8e305-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="8e305-107">Następujący blok `try` jest blokiem `catch`, który przechwytuje <xref:System.IO.FileNotFoundException> i zapisuje komunikat w konsoli, jeśli plik danych nie zostanie znaleziony.</span><span class="sxs-lookup"><span data-stu-id="8e305-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="8e305-108">Następną instrukcją jest instrukcja `throw`, która zgłasza nowy <xref:System.IO.FileNotFoundException> i dodaje do wyjątku informacje tekstowe.</span><span class="sxs-lookup"><span data-stu-id="8e305-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="8e305-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e305-109">See also</span></span>

- [<span data-ttu-id="8e305-110">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="8e305-110">Exceptions</span></span>](index.md)
