---
title: Ulepszenia wydajności gniazda w wersji 3.5
description: Dowiedz się więcej o ulepszeniach wydajności klasy System .NET. Sockets. Socket w wersji 3,5 w .NET Framework.
ms.date: 03/30/2017
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
ms.openlocfilehash: 5a640c58e47bf1630a3a551aed72b9bc9d4fd6fe
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502148"
---
# <a name="socket-performance-enhancements-in-version-35"></a>Ulepszenia wydajności gniazda w wersji 3.5
<xref:System.Net.Sockets.Socket?displayProperty=nameWithType>Klasa została ulepszona w wersji 3,5 do użycia przez aplikacje korzystające z operacji we/wy sieci asynchronicznej w celu osiągnięcia najwyższej wydajności. Seria nowych klas została dodana jako część zestawu ulepszeń <xref:System.Net.Sockets.Socket> klasy, która zapewnia alternatywny wzorzec asynchroniczny, który może być używany przez wyspecjalizowane aplikacje gniazd o wysokiej wydajności. Te ulepszenia zostały zaprojektowane specjalnie dla aplikacji serwer sieci, które wymagają wysokiej wydajności. Aplikacja może używać rozszerzonego wzorca asynchronicznego wyłącznie lub tylko w przeznaczonych na gorąco obszarach aplikacji (na przykład w przypadku otrzymywania dużej ilości danych).  
  
## <a name="class-enhancements"></a>Udoskonalenia klas  
 Główną funkcją tych ulepszeń jest unikanie powtarzania alokacji i synchronizacji obiektów w przypadku operacji we/wy na wysokim poziomie. Wzorzec projektowy Begin/End aktualnie zaimplementowany przez <xref:System.Net.Sockets.Socket> klasę dla operacji wejścia/wyjścia gniazda asynchronicznego wymaga, <xref:System.IAsyncResult?displayProperty=nameWithType> Aby obiekt został przydzielony dla każdej asynchronicznej obsługi gniazda.  
  
 W nowych <xref:System.Net.Sockets.Socket> udoskonaleniach klas asynchroniczne operacje gniazd są opisane przez obiekty klasy wielokrotnego użytku <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> przydzielone i utrzymywane przez aplikację. Aplikacje gniazd o wysokiej wydajności zapewniają najlepszą ilość nakładających się operacji gniazda, które muszą być utrzymywane. Aplikacja może utworzyć dowolną liczbę <xref:System.Net.Sockets.SocketAsyncEventArgs> obiektów, których potrzebuje. Na przykład, jeśli aplikacja serwera musi mieć 15 gniazd operacji akceptujących przez cały czas do obsługi przychodzących połączeń klienta, może przydzielić 15 obiektów wielokrotnego użytku do <xref:System.Net.Sockets.SocketAsyncEventArgs> tego celu.  
  
 Wzorzec wykonywania asynchronicznej operacji gniazda z tą klasą składa się z następujących kroków:  
  
1. Przydziel nowy <xref:System.Net.Sockets.SocketAsyncEventArgs> obiekt kontekstu lub uzyskaj bezpłatnie jeden z puli aplikacji.  
  
2. Ustaw właściwości obiektu kontekstu na operację, która ma zostać wykonana (na przykład metodę delegata wywołania zwrotnego i bufor danych).  
  
3. Wywołaj odpowiednią metodę Socket (xxxAsync) w celu zainicjowania operacji asynchronicznej.  
  
4. Jeśli asynchroniczna metoda Socket (xxxAsync) zwraca wartość true w wywołaniu zwrotnym, zbadaj właściwości kontekstu pod kątem stanu ukończenia.  
  
5. Jeśli asynchroniczne gniazdo Metoda (xxxAsync) zwróci wartość false w wywołaniu zwrotnym, operacja została zakończona synchronicznie. Właściwości kontekstu mogą być zapytania dla wyniku operacji.  
  
6. Ponownie Użyj kontekstu dla innej operacji, umieść go ponownie w puli lub Odrzuć.  
  
 Okres istnienia nowego obiektu kontekstu operacji gniazda asynchronicznego jest określany przez odwołania w kodzie aplikacji i asynchronicznych odwołaniach we/wy. Nie jest konieczne, aby aplikacja zachowała odwołanie do obiektu kontekstu operacji gniazda asynchronicznego po przesłaniu go jako parametru do jednej z asynchronicznych metod operacji gniazda. Pozostanie przywoływany do momentu wywołania zwrotnego zakończenia. Jest to jednak korzystne dla aplikacji, aby zachować odwołanie do obiektu kontekstu, dzięki czemu można go ponownie użyć do przyszłej asynchronicznej operacji na gnieździe.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>
- [Przykłady programowania sieciowego](network-programming-samples.md)
- [Przykłady kodu gniazd](socket-code-examples.md)
