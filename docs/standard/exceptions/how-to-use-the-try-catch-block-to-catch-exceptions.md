---
title: 'Porady: umożliwia przechwytywanie wyjątków w bloku Try-Catch'
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
ms.openlocfilehash: b169353752f6e6483a056cdc9dd8c3227b9ebeb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="cb66c-102">Przechwytywanie wyjątków przy użyciu bloku try/catch</span><span class="sxs-lookup"><span data-stu-id="cb66c-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="cb66c-103">Umieść fragmentów kodu, który może zgłaszać wyjątki w `try` bloku i umieść kod, który obsługuje wyjątki w `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="cb66c-103">Place the sections of code that might throw exceptions in a `try` block and place code that handles exceptions in a `catch` block.</span></span> <span data-ttu-id="cb66c-104">`catch` Blok jest serię instrukcji rozpoczynające się od słowa kluczowego `catch`, a następnie typ wyjątku i akcji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="cb66c-104">The `catch` block is a series of statements beginning with the keyword `catch`, followed by an exception type and an action to be taken.</span></span>

<span data-ttu-id="cb66c-105">Poniższy przykład kodu wykorzystuje `try` / `catch` bloku catch dopuszczalnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="cb66c-105">The following code example uses a `try`/`catch` block to catch a possible exception.</span></span> <span data-ttu-id="cb66c-106">`Main` Metoda zawiera `try` zablokować z <xref:System.IO.StreamReader> instrukcji, która otwiera plik danych o nazwie `data.txt` i zapisuje ciąg z pliku.</span><span class="sxs-lookup"><span data-stu-id="cb66c-106">The `Main` method contains a `try` block with a <xref:System.IO.StreamReader> statement that opens a data file called `data.txt` and writes a string from the file.</span></span> <span data-ttu-id="cb66c-107">Po `try` blok `catch` bloku, który przechwytuje wszystkie wyjątki, będącą wynikiem `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="cb66c-107">Following the `try` block is a `catch` block that catches any exception that results from the `try` block.</span></span>

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

<span data-ttu-id="cb66c-108">Środowisko uruchomieniowe języka wspólnego przechwytuje wyjątki, które nie są objęte bloku catch.</span><span class="sxs-lookup"><span data-stu-id="cb66c-108">The common language runtime catches exceptions that are not caught by a catch block.</span></span> <span data-ttu-id="cb66c-109">W zależności od sposobu skonfigurowania środowiska uruchomieniowego zostanie wyświetlone okno dialogowe debugowania, program zatrzymuje wykonywanie i pojawi się okno dialogowe z informacji o wyjątkach lub błąd jest drukowany stderr.</span><span class="sxs-lookup"><span data-stu-id="cb66c-109">Depending on how the runtime is configured, a debug dialog box appears, or the program stops executing and a dialog box with exception information appears, or an error is printed out to STDERR.</span></span>

> [!NOTE] 
> <span data-ttu-id="cb66c-110">Prawie każdego wiersza kodu może spowodować wyjątek, szczególnie wyjątki, które są generowane przez środowisko uruchomieniowe języka wspólnego, takich jak <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="cb66c-110">Almost any line of code can cause an exception, particularly exceptions that are thrown by the common language runtime itself, such as <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="cb66c-111">Większość aplikacji, nie trzeba uwzględniać z następującymi wyjątkami, ale należy zwrócić uwagę tej możliwości podczas zapisywania bibliotek, które mają być używane przez innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="cb66c-111">Most applications don't have to deal with these exceptions, but you should be aware of this possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="cb66c-112">Sugestie o tym, kiedy można ustawić kodu w bloku Try, zobacz [najlepsze praktyki dotyczące wyjątków](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="cb66c-112">For suggestions on when to set code in a Try block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cb66c-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb66c-113">See Also</span></span>  
[<span data-ttu-id="cb66c-114">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="cb66c-114">Exceptions</span></span>](index.md)
