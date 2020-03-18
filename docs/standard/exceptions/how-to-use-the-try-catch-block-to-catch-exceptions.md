---
title: 'Instrukcje: Używanie bloku try/catch do przechwytywania wyjątków'
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
ms.openlocfilehash: 5a9218d394b76e897f4263708a10f1bc895ad4e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708469"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="40ad8-102">Jak używać bloku try/catch do wychwytywania wyjątków</span><span class="sxs-lookup"><span data-stu-id="40ad8-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="40ad8-103">Umieść wszelkie instrukcje kodu, które mogą `try` podnieść lub zgłosić wyjątek w bloku i umieścić instrukcje `catch` używane `try` do obsługi wyjątku lub wyjątków w jednym lub więcej bloków poniżej bloku.</span><span class="sxs-lookup"><span data-stu-id="40ad8-103">Place any code statements that might raise or throw an exception in a `try` block, and place statements used to handle the exception or exceptions in one or more `catch` blocks below the `try` block.</span></span> <span data-ttu-id="40ad8-104">Każdy `catch` blok zawiera typ wyjątku i może zawierać dodatkowe instrukcje potrzebne do obsługi tego typu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="40ad8-104">Each `catch` block includes the exception type and can contain additional statements needed to handle that exception type.</span></span>

<span data-ttu-id="40ad8-105">W poniższym przykładzie <xref:System.IO.StreamReader> otwiera plik o nazwie *data.txt* i pobiera wiersz z pliku.</span><span class="sxs-lookup"><span data-stu-id="40ad8-105">In the following example, a <xref:System.IO.StreamReader> opens a file called *data.txt* and retrieves a line from the file.</span></span> <span data-ttu-id="40ad8-106">Ponieważ kod może zgłosić jeden z trzech wyjątków, `try` jest umieszczony w bloku.</span><span class="sxs-lookup"><span data-stu-id="40ad8-106">Since the code might throw any of three exceptions, it's placed in a `try` block.</span></span> <span data-ttu-id="40ad8-107">Trzy `catch` bloki złapać wyjątki i obsługiwać je, wyświetlając wyniki do konsoli.</span><span class="sxs-lookup"><span data-stu-id="40ad8-107">Three `catch` blocks catch the exceptions and handle them by displaying the results to the console.</span></span>

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

<span data-ttu-id="40ad8-108">Common Language Runtime (CLR) przechwytuje wyjątki nie obsługiwane przez `catch` bloki.</span><span class="sxs-lookup"><span data-stu-id="40ad8-108">The Common Language Runtime (CLR) catches exceptions not handled by `catch` blocks.</span></span> <span data-ttu-id="40ad8-109">Jeśli wyjątek zostanie przechwycony przez clr, jeden z następujących wyników może wystąpić w zależności od konfiguracji CLR:</span><span class="sxs-lookup"><span data-stu-id="40ad8-109">If an exception is caught by the CLR, one of the following results may occur depending on your CLR configuration:</span></span>

- <span data-ttu-id="40ad8-110">Pojawi się okno dialogowe **Debugowania.**</span><span class="sxs-lookup"><span data-stu-id="40ad8-110">A **Debug** dialog box appears.</span></span>
- <span data-ttu-id="40ad8-111">Program zatrzymuje wykonywanie i pojawia się okno dialogowe z informacjami o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="40ad8-111">The program stops execution and a dialog box with exception information appears.</span></span>
- <span data-ttu-id="40ad8-112">Błąd jest drukowany do [standardowego strumienia wyjściowego błędu](xref:System.Console.Error).</span><span class="sxs-lookup"><span data-stu-id="40ad8-112">An error prints out to the [standard error output stream](xref:System.Console.Error).</span></span>

> [!NOTE]
> <span data-ttu-id="40ad8-113">Większość kodu może zgłosić wyjątek, a <xref:System.OutOfMemoryException>niektóre wyjątki, takie jak , mogą być generowane przez clr się w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="40ad8-113">Most code can throw an exception, and some exceptions, like <xref:System.OutOfMemoryException>, can be thrown by the CLR itself at any time.</span></span> <span data-ttu-id="40ad8-114">Chociaż aplikacje nie są wymagane do radzenia sobie z tymi wyjątkami, należy pamiętać o możliwości podczas pisania bibliotek, które mają być używane przez inne osoby.</span><span class="sxs-lookup"><span data-stu-id="40ad8-114">While applications aren't required to deal with these exceptions, be aware of the possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="40ad8-115">Aby uzyskać sugestie dotyczące ustawiania `try` kodu w bloku, zobacz [Najważniejsze wskazówki dotyczące wyjątków](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="40ad8-115">For suggestions on when to set code in a `try` block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="40ad8-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40ad8-116">See also</span></span>

- [<span data-ttu-id="40ad8-117">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="40ad8-117">Exceptions</span></span>](index.md)
- [<span data-ttu-id="40ad8-118">Obsługa błędów we/wy w .NET</span><span class="sxs-lookup"><span data-stu-id="40ad8-118">Handling I/O errors in .NET</span></span>](../io/handling-io-errors.md)
