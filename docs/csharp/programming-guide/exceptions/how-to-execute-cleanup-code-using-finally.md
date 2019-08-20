---
title: 'Instrukcje: Wykonaj czyszczenie kodu przy użyciu przewodnika finally C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: e6adbb864b0450cdd1dbfcc56abdbad2034c5c7a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590246"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Instrukcje: Wykonaj oczyszczanie kodu za pomocąC# finally (Przewodnik programowania)
Celem `finally` instrukcji jest upewnienie się, że konieczne jest oczyszczenie obiektów, zwykle obiektów, które są zasobami zewnętrznymi, występuje natychmiast, nawet jeśli zostanie zgłoszony wyjątek. Przykładem takiego oczyszczania jest wywoływanie <xref:System.IO.Stream.Close%2A> <xref:System.IO.FileStream> natychmiast po użyciu zamiast oczekiwania na odrzucanie obiektu przez środowisko uruchomieniowe języka wspólnego w następujący sposób:  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a>Przykład  
 Aby przekształcić poprzedni kod do `try-catch-finally` instrukcji, kod czyszczący jest oddzielony od kodu roboczego w następujący sposób.  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 Ponieważ wyjątek może wystąpić w dowolnym momencie w `try` bloku `OpenWrite()` przed wywołaniem lub `OpenWrite()` samo wywołanie może się nie powieść, nie gwarantujemy, że plik jest otwarty, gdy spróbujemy go zamknąć. Blok dodaje zaznaczenie <xref:System.IO.FileStream> , aby upewnić się, że obiekt <xref:System.IO.Stream.Close%2A> nie `null` jest przed wywołaniem metody. `finally` Bez sprawdzania, blok może zgłosić <xref:System.NullReferenceException>swój własny, ale jeśli jest to możliwe, `finally` należy unikać zgłaszania wyjątków w blokach. `finally` `null`  
  
 Połączenie z bazą danych jest kolejnym odpowiednim kandydatem do zamknięcia w `finally` bloku. Ponieważ liczba połączeń dozwolonych dla serwera bazy danych jest czasami ograniczona, należy zamknąć połączenia z bazą danych tak szybko, jak to możliwe. Jeśli wyjątek jest zgłaszany przed zamknięciem połączenia, jest to kolejny przypadek, w `finally` którym użycie bloku jest lepsze niż oczekiwanie na wyrzucanie elementów bezużytecznych.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Wyjątki i obsługa wyjątków](./index.md)
- [Obsługa wyjątków](./exception-handling.md)
- [using, instrukcja](../../language-reference/keywords/using-statement.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
