---
title: Jak wykonać kod czyszczący za pomocą przewodnika finally C#
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: d1ba761e64053d656ad4cd004133fc455a57c6f6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705278"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="e1a60-102">Jak wykonać kod czyszczący za pomocą finallyC# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="e1a60-102">How to execute cleanup code using finally (C# Programming Guide)</span></span>
<span data-ttu-id="e1a60-103">Celem instrukcji `finally` jest upewnienie się, że konieczne jest oczyszczenie obiektów, zazwyczaj obiektów, które są zasobami zewnętrznymi, występuje natychmiast, nawet jeśli zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e1a60-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="e1a60-104">Przykładem takiego oczyszczania jest wywoływanie <xref:System.IO.Stream.Close%2A> na <xref:System.IO.FileStream> natychmiast po użyciu zamiast oczekiwania na odrzucanie obiektu przez środowisko uruchomieniowe języka wspólnego w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e1a60-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a><span data-ttu-id="e1a60-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1a60-105">Example</span></span>  
 <span data-ttu-id="e1a60-106">Aby przekształcić poprzedni kod w instrukcję `try-catch-finally`, kod czyszczący jest oddzielony od kodu roboczego w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="e1a60-106">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 <span data-ttu-id="e1a60-107">Ponieważ wyjątek może wystąpić w dowolnym momencie w bloku `try` przed wywołaniem `OpenWrite()` lub wywołaniem `OpenWrite()` może się nie powieść, nie gwarantujemy, że plik jest otwarty, gdy spróbujemy go zamknąć.</span><span class="sxs-lookup"><span data-stu-id="e1a60-107">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="e1a60-108">Blok `finally` dodaje sprawdzenie, aby upewnić się, że obiekt <xref:System.IO.FileStream> nie jest `null` przed wywołaniem metody <xref:System.IO.Stream.Close%2A>.</span><span class="sxs-lookup"><span data-stu-id="e1a60-108">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="e1a60-109">Bez sprawdzania `null`, blok `finally` może zgłosić swój własny <xref:System.NullReferenceException>, ale w razie możliwości należy wyeliminować wyjątki w blokach `finally`.</span><span class="sxs-lookup"><span data-stu-id="e1a60-109">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="e1a60-110">Połączenie z bazą danych jest kolejnym odpowiednim kandydatem do zamknięcia w bloku `finally`.</span><span class="sxs-lookup"><span data-stu-id="e1a60-110">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="e1a60-111">Ponieważ liczba połączeń dozwolonych dla serwera bazy danych jest czasami ograniczona, należy zamknąć połączenia z bazą danych tak szybko, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="e1a60-111">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="e1a60-112">Jeśli wyjątek jest zgłaszany przed zamknięciem połączenia, jest to kolejny przypadek, w którym użycie bloku `finally` jest lepsze niż oczekiwanie na wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e1a60-112">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1a60-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1a60-113">See also</span></span>

- [<span data-ttu-id="e1a60-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e1a60-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e1a60-115">Wyjątki i obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="e1a60-115">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="e1a60-116">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="e1a60-116">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="e1a60-117">using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e1a60-117">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="e1a60-118">try-catch</span><span class="sxs-lookup"><span data-stu-id="e1a60-118">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="e1a60-119">try-finally</span><span class="sxs-lookup"><span data-stu-id="e1a60-119">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="e1a60-120">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="e1a60-120">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
