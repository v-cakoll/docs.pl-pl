---
title: 'Porady: Użyj bloku Try / Catch do przechwytywania wyjątków'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 852df5cb3eeea2ee5fa44ddce2f97e9c4f8d8b5a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47236981"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="c42f9-102">Jak przechwytywać wyjątki za pomocą bloku try/catch</span><span class="sxs-lookup"><span data-stu-id="c42f9-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="c42f9-103">Umieszczenie fragmentów kodu, który może zgłaszać wyjątki w `try` bloku i umieść kod, który obsługuje wyjątki w `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="c42f9-103">Place the sections of code that might throw exceptions in a `try` block and place code that handles exceptions in a `catch` block.</span></span> <span data-ttu-id="c42f9-104">`catch` Blok jest szereg instrukcji rozpoczynające się od słowa kluczowego `catch`, a następnie typ wyjątku i akcję do wykonania.</span><span class="sxs-lookup"><span data-stu-id="c42f9-104">The `catch` block is a series of statements beginning with the keyword `catch`, followed by an exception type and an action to be taken.</span></span>

<span data-ttu-id="c42f9-105">Poniższy przykład kodu wykorzystuje `try` / `catch` bloku catch możliwym wyjątkiem.</span><span class="sxs-lookup"><span data-stu-id="c42f9-105">The following code example uses a `try`/`catch` block to catch a possible exception.</span></span> <span data-ttu-id="c42f9-106">`Main` Metoda zawiera `try` blokowania z <xref:System.IO.StreamReader> instrukcję, która otwiera plik danych o nazwie `data.txt` i zapisuje ciąg z pliku.</span><span class="sxs-lookup"><span data-stu-id="c42f9-106">The `Main` method contains a `try` block with a <xref:System.IO.StreamReader> statement that opens a data file called `data.txt` and writes a string from the file.</span></span> <span data-ttu-id="c42f9-107">Następujące `try` blok `catch` blok, który przechwytuje wszystkie wyjątki, które powstały na skutek `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="c42f9-107">Following the `try` block is a `catch` block that catches any exception that results from the `try` block.</span></span>

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

<span data-ttu-id="c42f9-108">Środowisko uruchomieniowe języka wspólnego przechwytuje wyjątki, które nie są przechwytywane przez blok catch.</span><span class="sxs-lookup"><span data-stu-id="c42f9-108">The common language runtime catches exceptions that are not caught by a catch block.</span></span> <span data-ttu-id="c42f9-109">W zależności od sposobu skonfigurowania środowiska uruchomieniowego pojawi się okno dialogowe debugowania, program zatrzymuje wykonywanie i pojawia się okno dialogowe z informacjami o wyjątek lub błąd jest drukowany stderr.</span><span class="sxs-lookup"><span data-stu-id="c42f9-109">Depending on how the runtime is configured, a debug dialog box appears, or the program stops executing and a dialog box with exception information appears, or an error is printed out to STDERR.</span></span>

> [!NOTE] 
> <span data-ttu-id="c42f9-110">Prawie w każdym wierszu kodu może spowodować wyjątek, szczególnie te wyjątki, które są generowane przez środowisko uruchomieniowe języka wspólnego, takich jak <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="c42f9-110">Almost any line of code can cause an exception, particularly exceptions that are thrown by the common language runtime itself, such as <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="c42f9-111">Większość aplikacji nie ma do czynienia z uwzględnieniem poniższych wyjątków, ale należy pamiętać o to martwić, podczas zapisywania biblioteki ma być używany przez inne osoby.</span><span class="sxs-lookup"><span data-stu-id="c42f9-111">Most applications don't have to deal with these exceptions, but you should be aware of this possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="c42f9-112">Aby uzyskać sugestie, kiedy należy ustawić możesz pisać kod w bloku Try, zobacz [najlepsze praktyki dotyczące wyjątków](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="c42f9-112">For suggestions on when to set code in a Try block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c42f9-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c42f9-113">See also</span></span>

- [<span data-ttu-id="c42f9-114">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="c42f9-114">Exceptions</span></span>](index.md)
