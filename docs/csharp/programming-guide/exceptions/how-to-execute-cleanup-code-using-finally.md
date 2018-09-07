---
title: 'Porady: wykonywanie czyszczenia kodu za pomocą instrukcji finally (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 47e9bb368deb077ef10ce474683d81e0cb56cef8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44046812"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Porady: wykonywanie czyszczenia kodu za pomocą instrukcji finally (Przewodnik programowania w języku C#)
Celem `finally` instrukcji jest zapewnienie, niezbędne czyszczenia obiektów, zazwyczaj te obiekty, które są zawierający zasoby zewnętrzne, następuje natychmiast, nawet wtedy, gdy zostanie zgłoszony wyjątek. Przykładem takiego oczyszczania jest wywołanie <xref:System.IO.Stream.Close%2A> na <xref:System.IO.FileStream> natychmiast po ich użyciu, zamiast czekać, aż obiekt jest bezużyteczne przez środowisko uruchomieniowe języka wspólnego, w następujący sposób:  
  
 [!code-csharp[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]  
  
## <a name="example"></a>Przykład  
 Aby włączyć poprzedni kod do `try-catch-finally` instrukcji, kod porządkujący jest oddzielony od kodu, pracy, w następujący sposób.  
  
 [!code-csharp[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]  
  
 Ponieważ wyjątek może występować w dowolnym momencie, w ramach `try` blokować przed `OpenWrite()` wywołać, lub `OpenWrite()` wywołanie może się nie powieść, firma Microsoft nie ma gwarancji, plik jest otwarty, gdy podejmowane są próby zamknij go. `finally` Bloku dodaje wyboru, aby upewnić się, że <xref:System.IO.FileStream> obiekt nie jest `null` przed wywołaniem <xref:System.IO.Stream.Close%2A> metody. Bez `null` sprawdzić, `finally` bloku można zgłosić swój własny <xref:System.NullReferenceException>, ale zgłaszanie wyjątków `finally` unikać bloki, jeśli jest to możliwe.  
  
 Połączenia z bazą danych jest zamykana innym dobrym kandydatem `finally` bloku. Ponieważ liczba połączeń z serwerem bazy danych, czasami jest ograniczona, tak szybko, jak to możliwe należy zamknąć połączenia z bazą danych. Jeśli jest zgłaszany wyjątek, zanim zamkniesz połączenie, jest to inny przypadek w przypadku, gdy za pomocą `finally` bloku jest lepsze niż czekanie, aż wyrzucania elementów bezużytecznych.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Wyjątki i obsługa wyjątków](../../../csharp/programming-guide/exceptions/index.md)  
- [Obsługa wyjątków](../../../csharp/programming-guide/exceptions/exception-handling.md)  
- [using, instrukcja](../../../csharp/language-reference/keywords/using-statement.md)  
- [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
- [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
- [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)
