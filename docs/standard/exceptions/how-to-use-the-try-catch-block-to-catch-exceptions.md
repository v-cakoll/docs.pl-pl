---
title: 'Instrukcje: Użyj bloku Try / Catch do przechwytywania wyjątków'
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
ms.openlocfilehash: 5183a854ee2b7462ecc27786a5fc0697565194c0
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092751"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="c9c3f-102">Jak przechwytywać wyjątki za pomocą bloku try/catch</span><span class="sxs-lookup"><span data-stu-id="c9c3f-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="c9c3f-103">Umieść wszystkie instrukcje kodu, które mogą zgłosić lub zgłosić wyjątek w `try` bloku i instrukcje miejsce używane do obsługi wyjątków lub wyjątków w co najmniej jeden `catch` poniższych bloków `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="c9c3f-103">Place any code statements that might raise or throw an exception in a `try` block, and place statements used to handle the exception or exceptions in one or more `catch` blocks below the `try` block.</span></span> <span data-ttu-id="c9c3f-104">Każdy `catch` blok zawiera typ wyjątku i może zawierać dodatkowe instrukcje niezbędne do obsługi tego typu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c9c3f-104">Each `catch` block includes the exception type and can contain additional statements needed to handle that exception type.</span></span>

<span data-ttu-id="c9c3f-105">W poniższym przykładzie <xref:System.IO.StreamReader> otwiera plik o nazwie *data.txt* i pobiera wiersz z pliku.</span><span class="sxs-lookup"><span data-stu-id="c9c3f-105">In the following example, a <xref:System.IO.StreamReader> opens a file called *data.txt* and retrieves a line from the file.</span></span> <span data-ttu-id="c9c3f-106">Ponieważ kod może zgłosić żadnego z trzema wyjątkami, jest umieszczany w `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="c9c3f-106">Since the code might throw any of three exceptions, it's placed in a `try` block.</span></span> <span data-ttu-id="c9c3f-107">Trzy `catch` bloków rejestrować wyjątki i je obsłużyć, wyświetlając wyniki do konsoli.</span><span class="sxs-lookup"><span data-stu-id="c9c3f-107">Three `catch` blocks catch the exceptions and handle them by displaying the results to the console.</span></span>

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

<span data-ttu-id="c9c3f-108">Środowisko uruchomieniowe języka wspólnego (CLR) przechwytuje wyjątki, które nie są obsługiwane przez `catch` bloków.</span><span class="sxs-lookup"><span data-stu-id="c9c3f-108">The Common Language Runtime (CLR) catches exceptions not handled by `catch` blocks.</span></span> <span data-ttu-id="c9c3f-109">Jeśli wyjątek zostaje przechwycony przez środowisko CLR, może wystąpić jeden z następujących wyników w zależności od konfiguracji środowiska CLR:</span><span class="sxs-lookup"><span data-stu-id="c9c3f-109">If an exception is caught by the CLR, one of the following results may occur depending on your CLR configuration:</span></span>

- <span data-ttu-id="c9c3f-110">A **debugowania** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="c9c3f-110">A **Debug** dialog box appears.</span></span>
- <span data-ttu-id="c9c3f-111">Program zatrzymuje wykonywanie i pojawi się okno dialogowe, za pomocą informacji o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c9c3f-111">The program stops execution and a dialog box with exception information appears.</span></span>
- <span data-ttu-id="c9c3f-112">Błąd do drukowania do [błędu standardowego strumienia wyjściowego](xref:System.Console.Error).</span><span class="sxs-lookup"><span data-stu-id="c9c3f-112">An error prints out to the [standard error output stream](xref:System.Console.Error).</span></span>

> [!NOTE]
> <span data-ttu-id="c9c3f-113">Większość kodu może zgłosić wyjątek, a niektóre wyjątki, takie jak <xref:System.OutOfMemoryException>, mogą być generowane przez środowisko CLR, sama w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="c9c3f-113">Most code can throw an exception, and some exceptions, like <xref:System.OutOfMemoryException>, can be thrown by the CLR itself at any time.</span></span> <span data-ttu-id="c9c3f-114">Gdy aplikacje nie są wymagane do czynienia z uwzględnieniem poniższych wyjątków, należy pamiętać o możliwości podczas zapisywania biblioteki ma być używany przez inne osoby.</span><span class="sxs-lookup"><span data-stu-id="c9c3f-114">While applications aren't required to deal with these exceptions, be aware of the possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="c9c3f-115">Sugestie, gdy można ustawić kodu w `try` blokowania, zobacz [najlepsze praktyki dotyczące wyjątków](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="c9c3f-115">For suggestions on when to set code in a `try` block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c9c3f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9c3f-116">See also</span></span>

[<span data-ttu-id="c9c3f-117">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="c9c3f-117">Exceptions</span></span>](index.md)  
[<span data-ttu-id="c9c3f-118">Obsługa błędów operacji We/Wy na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="c9c3f-118">Handling I/O errors in .NET</span></span>](../io/handling-io-errors.md)
