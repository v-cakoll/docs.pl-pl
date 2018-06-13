---
title: 'Porady: wykonywanie czyszczenia kodu za pomocą instrukcji finally (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 948281af45d04714ed6fc308b60341e87abeb830
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331711"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="33978-102">Porady: wykonywanie czyszczenia kodu za pomocą instrukcji finally (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="33978-102">How to: Execute Cleanup Code Using finally (C# Programming Guide)</span></span>
<span data-ttu-id="33978-103">Celem `finally` instrukcji ma upewnij się, że niezbędne obiektów, zwykle obiektów, które są zawierający zasobów zewnętrznych, przeprowadzane jest oczyszczanie natychmiast, nawet wtedy, gdy jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="33978-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="33978-104">Przykładem takich oczyszczania powoduje wywołanie <xref:System.IO.Stream.Close%2A> na <xref:System.IO.FileStream> natychmiast po użyciu zamiast czekać na obiekt jako bezużytecznych przez środowisko uruchomieniowe języka wspólnego, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="33978-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="33978-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="33978-105">Example</span></span>  
 <span data-ttu-id="33978-106">Aby włączyć poprzedni kod do `try-catch-finally` instrukcji, oczyszczanie kodu jest oddzielony od kodu pracy w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="33978-106">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]  
  
 <span data-ttu-id="33978-107">Ponieważ wyjątek może wystąpić w dowolnym momencie w obrębie `try` blokować przed `OpenWrite()` wywołać, lub `OpenWrite()` samo w sobie może zakończyć się niepowodzeniem, firma Microsoft nie ma gwarancji, że plik jest otwarty przy próbie go zamknąć.</span><span class="sxs-lookup"><span data-stu-id="33978-107">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="33978-108">`finally` Bloku dodaje wyboru, aby upewnić się, że <xref:System.IO.FileStream> obiekt nie jest `null` przed wywołaniem <xref:System.IO.Stream.Close%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="33978-108">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="33978-109">Bez `null` sprawdzić, `finally` bloku może wywoływać własną <xref:System.NullReferenceException>, ale zgłaszanie wyjątków `finally` bloki należy unikać, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="33978-109">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="33978-110">Połączenie z bazą danych jest inny odpowiednimi kandydatami do zamykania `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="33978-110">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="33978-111">Czasami jest dozwoloną liczbę połączeń z serwerem bazy danych, należy zamknąć połączenia bazy danych tak szybko jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="33978-111">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="33978-112">Jeśli przed zamknięciem połączenie, jest zgłaszany wyjątek, jest inny przypadek w przypadku, gdy przy użyciu `finally` blok jest lepsze niż czekanie, aż wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="33978-112">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33978-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33978-113">See Also</span></span>  
 [<span data-ttu-id="33978-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="33978-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="33978-115">Wyjątki i obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="33978-115">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)  
 [<span data-ttu-id="33978-116">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="33978-116">Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/exception-handling.md)  
 [<span data-ttu-id="33978-117">using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="33978-117">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)  
 [<span data-ttu-id="33978-118">try-catch</span><span class="sxs-lookup"><span data-stu-id="33978-118">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="33978-119">try-finally</span><span class="sxs-lookup"><span data-stu-id="33978-119">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)  
 [<span data-ttu-id="33978-120">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="33978-120">try-catch-finally</span></span>](../../../csharp/language-reference/keywords/try-catch-finally.md)
