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
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Porady: wykonywanie czyszczenia kodu za pomocą instrukcji finally (Przewodnik programowania w języku C#)
Celem `finally` instrukcji ma upewnij się, że niezbędne obiektów, zwykle obiektów, które są zawierający zasobów zewnętrznych, przeprowadzane jest oczyszczanie natychmiast, nawet wtedy, gdy jest zgłaszany wyjątek. Przykładem takich oczyszczania powoduje wywołanie <xref:System.IO.Stream.Close%2A> na <xref:System.IO.FileStream> natychmiast po użyciu zamiast czekać na obiekt jako bezużytecznych przez środowisko uruchomieniowe języka wspólnego, w następujący sposób:  
  
 [!code-csharp[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]  
  
## <a name="example"></a>Przykład  
 Aby włączyć poprzedni kod do `try-catch-finally` instrukcji, oczyszczanie kodu jest oddzielony od kodu pracy w następujący sposób.  
  
 [!code-csharp[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]  
  
 Ponieważ wyjątek może wystąpić w dowolnym momencie w obrębie `try` blokować przed `OpenWrite()` wywołać, lub `OpenWrite()` samo w sobie może zakończyć się niepowodzeniem, firma Microsoft nie ma gwarancji, że plik jest otwarty przy próbie go zamknąć. `finally` Bloku dodaje wyboru, aby upewnić się, że <xref:System.IO.FileStream> obiekt nie jest `null` przed wywołaniem <xref:System.IO.Stream.Close%2A> metody. Bez `null` sprawdzić, `finally` bloku może wywoływać własną <xref:System.NullReferenceException>, ale zgłaszanie wyjątków `finally` bloki należy unikać, jeśli jest to możliwe.  
  
 Połączenie z bazą danych jest inny odpowiednimi kandydatami do zamykania `finally` bloku. Czasami jest dozwoloną liczbę połączeń z serwerem bazy danych, należy zamknąć połączenia bazy danych tak szybko jak to możliwe. Jeśli przed zamknięciem połączenie, jest zgłaszany wyjątek, jest inny przypadek w przypadku, gdy przy użyciu `finally` blok jest lepsze niż czekanie, aż wyrzucanie elementów bezużytecznych.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wyjątki i obsługa wyjątków](../../../csharp/programming-guide/exceptions/index.md)  
 [Obsługa wyjątków](../../../csharp/programming-guide/exceptions/exception-handling.md)  
 [using, instrukcja](../../../csharp/language-reference/keywords/using-statement.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)
