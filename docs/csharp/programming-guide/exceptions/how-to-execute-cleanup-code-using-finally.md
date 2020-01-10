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
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Jak wykonać kod czyszczący za pomocą finallyC# (Przewodnik programowania)
Celem instrukcji `finally` jest upewnienie się, że konieczne jest oczyszczenie obiektów, zazwyczaj obiektów, które są zasobami zewnętrznymi, występuje natychmiast, nawet jeśli zostanie zgłoszony wyjątek. Przykładem takiego oczyszczania jest wywoływanie <xref:System.IO.Stream.Close%2A> na <xref:System.IO.FileStream> natychmiast po użyciu zamiast oczekiwania na odrzucanie obiektu przez środowisko uruchomieniowe języka wspólnego w następujący sposób:  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a>Przykład  
 Aby przekształcić poprzedni kod w instrukcję `try-catch-finally`, kod czyszczący jest oddzielony od kodu roboczego w następujący sposób.  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 Ponieważ wyjątek może wystąpić w dowolnym momencie w bloku `try` przed wywołaniem `OpenWrite()` lub wywołaniem `OpenWrite()` może się nie powieść, nie gwarantujemy, że plik jest otwarty, gdy spróbujemy go zamknąć. Blok `finally` dodaje sprawdzenie, aby upewnić się, że obiekt <xref:System.IO.FileStream> nie jest `null` przed wywołaniem metody <xref:System.IO.Stream.Close%2A>. Bez sprawdzania `null`, blok `finally` może zgłosić swój własny <xref:System.NullReferenceException>, ale w razie możliwości należy wyeliminować wyjątki w blokach `finally`.  
  
 Połączenie z bazą danych jest kolejnym odpowiednim kandydatem do zamknięcia w bloku `finally`. Ponieważ liczba połączeń dozwolonych dla serwera bazy danych jest czasami ograniczona, należy zamknąć połączenia z bazą danych tak szybko, jak to możliwe. Jeśli wyjątek jest zgłaszany przed zamknięciem połączenia, jest to kolejny przypadek, w którym użycie bloku `finally` jest lepsze niż oczekiwanie na wyrzucanie elementów bezużytecznych.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Wyjątki i obsługa wyjątków](./index.md)
- [Obsługa wyjątków](./exception-handling.md)
- [using, instrukcja](../../language-reference/keywords/using-statement.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
