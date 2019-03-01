---
title: 'Instrukcje: Wykonywanie czyszczenia kodu za pomocą instrukcji finally - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 0ec661e5fb0e13eaf8c3c8e4a7b274ab58853f58
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978088"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="b28b3-102">Instrukcje: Wykonywanie czyszczenia kodu za pomocą instrukcji finally (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="b28b3-102">How to: Execute Cleanup Code Using finally (C# Programming Guide)</span></span>
<span data-ttu-id="b28b3-103">Celem `finally` instrukcji jest zapewnienie, niezbędne czyszczenia obiektów, zazwyczaj te obiekty, które są zawierający zasoby zewnętrzne, następuje natychmiast, nawet wtedy, gdy zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b28b3-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="b28b3-104">Przykładem takiego oczyszczania jest wywołanie <xref:System.IO.Stream.Close%2A> na <xref:System.IO.FileStream> natychmiast po ich użyciu, zamiast czekać, aż obiekt jest bezużyteczne przez środowisko uruchomieniowe języka wspólnego, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b28b3-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a><span data-ttu-id="b28b3-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="b28b3-105">Example</span></span>  
 <span data-ttu-id="b28b3-106">Aby włączyć poprzedni kod do `try-catch-finally` instrukcji, kod porządkujący jest oddzielony od kodu, pracy, w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="b28b3-106">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 <span data-ttu-id="b28b3-107">Ponieważ wyjątek może występować w dowolnym momencie, w ramach `try` blokować przed `OpenWrite()` wywołać, lub `OpenWrite()` wywołanie może się nie powieść, firma Microsoft nie ma gwarancji, plik jest otwarty, gdy podejmowane są próby zamknij go.</span><span class="sxs-lookup"><span data-stu-id="b28b3-107">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="b28b3-108">`finally` Bloku dodaje wyboru, aby upewnić się, że <xref:System.IO.FileStream> obiekt nie jest `null` przed wywołaniem <xref:System.IO.Stream.Close%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b28b3-108">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="b28b3-109">Bez `null` sprawdzić, `finally` bloku można zgłosić swój własny <xref:System.NullReferenceException>, ale zgłaszanie wyjątków `finally` unikać bloki, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="b28b3-109">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="b28b3-110">Połączenia z bazą danych jest zamykana innym dobrym kandydatem `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="b28b3-110">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="b28b3-111">Ponieważ liczba połączeń z serwerem bazy danych, czasami jest ograniczona, tak szybko, jak to możliwe należy zamknąć połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="b28b3-111">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="b28b3-112">Jeśli jest zgłaszany wyjątek, zanim zamkniesz połączenie, jest to inny przypadek w przypadku, gdy za pomocą `finally` bloku jest lepsze niż czekanie, aż wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b28b3-112">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b28b3-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b28b3-113">See also</span></span>

- [<span data-ttu-id="b28b3-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b28b3-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b28b3-115">Wyjątki i obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="b28b3-115">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)
- [<span data-ttu-id="b28b3-116">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="b28b3-116">Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/exception-handling.md)
- [<span data-ttu-id="b28b3-117">using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b28b3-117">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="b28b3-118">try-catch</span><span class="sxs-lookup"><span data-stu-id="b28b3-118">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)
- [<span data-ttu-id="b28b3-119">try-finally</span><span class="sxs-lookup"><span data-stu-id="b28b3-119">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)
- [<span data-ttu-id="b28b3-120">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="b28b3-120">try-catch-finally</span></span>](../../../csharp/language-reference/keywords/try-catch-finally.md)
