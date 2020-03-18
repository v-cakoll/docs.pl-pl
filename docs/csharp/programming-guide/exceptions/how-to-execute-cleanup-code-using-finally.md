---
title: Jak wykonać kod oczyszczania przy użyciu finally - C# Programming Guide
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: d1ba761e64053d656ad4cd004133fc455a57c6f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705278"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Jak wykonać kod oczyszczania przy użyciu finally (C# Programming Guide)
Celem `finally` instrukcji jest zapewnienie, że niezbędne oczyszczanie obiektów, zwykle obiektów, które przechowują zasoby zewnętrzne, występuje natychmiast, nawet jeśli wyjątek. Jednym z przykładów takiego <xref:System.IO.Stream.Close%2A> oczyszczania <xref:System.IO.FileStream> jest wywołanie bezpośrednio po użyciu zamiast oczekiwania na obiekt, który ma być śmieciem zbieranym przez czas wykonywania języka wspólnego, w następujący sposób:  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a>Przykład  
 Aby przekształcić poprzedni kod `try-catch-finally` w instrukcję, kod oczyszczania jest oddzielony od kodu roboczego, w następujący sposób.  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 Ponieważ wyjątek może wystąpić w `try` dowolnym momencie `OpenWrite()` w bloku `OpenWrite()` przed wywołaniem lub samo wywołanie może zakończyć się niepowodzeniem, nie mamy gwarancji, że plik jest otwarty, gdy próbujemy go zamknąć. Blok `finally` dodaje czek, aby upewnić <xref:System.IO.FileStream> się, `null` że obiekt <xref:System.IO.Stream.Close%2A> nie jest przed wywołaniem metody. Bez `null` kontroli `finally` blok może rzucać <xref:System.NullReferenceException>własne , ale `finally` rzucanie wyjątków w blokach należy unikać, jeśli jest to możliwe.  
  
 Połączenie z bazą danych jest kolejnym `finally` dobrym kandydatem do zamknięcia w bloku. Ponieważ liczba połączeń dozwolonych na serwerze bazy danych jest czasami ograniczona, należy zamknąć połączenia bazy danych tak szybko, jak to możliwe. Jeśli wyjątek jest generowany przed zamknięciem połączenia, jest to `finally` inny przypadek, w którym przy użyciu bloku jest lepiej niż oczekiwanie na wyrzucanie elementów bezużytecznych.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Wyjątki i obsługa wyjątków](./index.md)
- [Obsługa wyjątków](./exception-handling.md)
- [za pomocą instrukcji](../../language-reference/keywords/using-statement.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
