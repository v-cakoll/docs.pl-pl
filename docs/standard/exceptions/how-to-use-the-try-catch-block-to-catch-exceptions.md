---
title: 'Instrukcje: używanie bloku try-catch do przechwytywania wyjątków'
ms.date: 02/06/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eaa389f461e70aae41f2e09437fd725a3bcefa5e
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696718"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="e3c85-102">Jak przechwytywać wyjątki przy użyciu bloku try/catch</span><span class="sxs-lookup"><span data-stu-id="e3c85-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="e3c85-103">Umieść wszystkie instrukcje Code, które mogą podnieść lub zgłosić wyjątek w bloku `try` i umieścić instrukcje używane do obsługi wyjątku lub wyjątków w co najmniej jednym bloku `catch` poniżej bloku `try`.</span><span class="sxs-lookup"><span data-stu-id="e3c85-103">Place any code statements that might raise or throw an exception in a `try` block, and place statements used to handle the exception or exceptions in one or more `catch` blocks below the `try` block.</span></span> <span data-ttu-id="e3c85-104">Każdy blok `catch` zawiera typ wyjątku i może zawierać dodatkowe instrukcje, które są konieczne do obsłużenia tego typu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="e3c85-104">Each `catch` block includes the exception type and can contain additional statements needed to handle that exception type.</span></span>

<span data-ttu-id="e3c85-105">W poniższym przykładzie <xref:System.IO.StreamReader> otwiera plik o nazwie *Data. txt* i pobiera wiersz z pliku.</span><span class="sxs-lookup"><span data-stu-id="e3c85-105">In the following example, a <xref:System.IO.StreamReader> opens a file called *data.txt* and retrieves a line from the file.</span></span> <span data-ttu-id="e3c85-106">Ponieważ kod może zgłosić którykolwiek z trzech wyjątków, zostanie umieszczony w bloku `try`.</span><span class="sxs-lookup"><span data-stu-id="e3c85-106">Since the code might throw any of three exceptions, it's placed in a `try` block.</span></span> <span data-ttu-id="e3c85-107">Trzy `catch` bloków przechwytują wyjątki i obsługują je, wyświetlając wyniki w konsoli.</span><span class="sxs-lookup"><span data-stu-id="e3c85-107">Three `catch` blocks catch the exceptions and handle them by displaying the results to the console.</span></span>

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

<span data-ttu-id="e3c85-108">Aparat plików wykonywalnych języka wspólnego (CLR) przechwytuje wyjątki, które nie są obsługiwane przez bloki `catch`.</span><span class="sxs-lookup"><span data-stu-id="e3c85-108">The Common Language Runtime (CLR) catches exceptions not handled by `catch` blocks.</span></span> <span data-ttu-id="e3c85-109">W przypadku przechwyconego wyjątku przez środowisko CLR może wystąpić jeden z następujących wyników w zależności od konfiguracji środowiska CLR:</span><span class="sxs-lookup"><span data-stu-id="e3c85-109">If an exception is caught by the CLR, one of the following results may occur depending on your CLR configuration:</span></span>

- <span data-ttu-id="e3c85-110">Zostanie wyświetlone okno dialogowe **debugowanie** .</span><span class="sxs-lookup"><span data-stu-id="e3c85-110">A **Debug** dialog box appears.</span></span>
- <span data-ttu-id="e3c85-111">Program przerywa wykonywanie i pojawia się okno dialogowe z informacjami o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="e3c85-111">The program stops execution and a dialog box with exception information appears.</span></span>
- <span data-ttu-id="e3c85-112">Wystąpił błąd podczas drukowania [strumienia wyjściowego błędu standardowego](xref:System.Console.Error).</span><span class="sxs-lookup"><span data-stu-id="e3c85-112">An error prints out to the [standard error output stream](xref:System.Console.Error).</span></span>

> [!NOTE]
> <span data-ttu-id="e3c85-113">Większość kodu może zgłosić wyjątek, a niektóre wyjątki, takie jak <xref:System.OutOfMemoryException>, mogą być zgłaszane przez samo środowisko CLR w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="e3c85-113">Most code can throw an exception, and some exceptions, like <xref:System.OutOfMemoryException>, can be thrown by the CLR itself at any time.</span></span> <span data-ttu-id="e3c85-114">Chociaż aplikacje nie są wymagane do obsługi tych wyjątków, należy pamiętać o możliwości, gdy pisanie bibliotek ma być używane przez inne osoby.</span><span class="sxs-lookup"><span data-stu-id="e3c85-114">While applications aren't required to deal with these exceptions, be aware of the possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="e3c85-115">Aby uzyskać sugestie dotyczące sposobu ustawiania kodu w bloku `try`, zobacz [najlepsze rozwiązania dotyczące wyjątków](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="e3c85-115">For suggestions on when to set code in a `try` block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3c85-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3c85-116">See also</span></span>

- [<span data-ttu-id="e3c85-117">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="e3c85-117">Exceptions</span></span>](index.md)
- [<span data-ttu-id="e3c85-118">Obsługa błędów we/wy w programie .NET</span><span class="sxs-lookup"><span data-stu-id="e3c85-118">Handling I/O errors in .NET</span></span>](../io/handling-io-errors.md)
