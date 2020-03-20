---
title: Ulepszenia wydajności gniazda w wersji 3.5
ms.date: 03/30/2017
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
ms.openlocfilehash: 577c033fc5639f9d9f50e413fd2cb55a75d48f2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047244"
---
# <a name="socket-performance-enhancements-in-version-35"></a>Ulepszenia wydajności gniazda w wersji 3.5
Klasa <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> została ulepszona w wersji 3.5 do użytku przez aplikacje, które używają asynchroniicznych we/wy sieci w celu osiągnięcia najwyższej wydajności. Seria nowych klas zostały dodane jako część zestawu ulepszeń <xref:System.Net.Sockets.Socket> do klasy, które zapewniają alternatywny wzorzec asynchroniczne, które mogą być używane przez wyspecjalizowane aplikacje gniazd o wysokiej wydajności. Te ulepszenia zostały zaprojektowane specjalnie dla aplikacji serwera sieciowego, które wymagają wysokiej wydajności. Aplikacja może używać rozszerzonego wzorca asynchronicznego wyłącznie lub tylko w wybranych gorących obszarach ich aplikacji (na przykład podczas odbierania dużych ilości danych).  
  
## <a name="class-enhancements"></a>Ulepszenia klasy  
 Główną cechą tych ulepszeń jest unikanie powtarzanej alokacji i synchronizacji obiektów podczas asynchroniiowego gniazda we/wy o dużej objętości. Wzorzec projektu Begin/End obecnie <xref:System.Net.Sockets.Socket> zaimplementowany przez klasę dla asynchroniczną gniazdo we/wy wymaga, aby <xref:System.IAsyncResult?displayProperty=nameWithType> obiekt został przydzielony dla każdej operacji gniazda asynchroniczną.  
  
 W nowych <xref:System.Net.Sockets.Socket> ulepszeń klasy asynchroniczne operacje gniazda są <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> opisane przez obiekty klasy wielokrotnego użytku przydzielone i obsługiwane przez aplikację. Aplikacje gnieździe o wysokiej wydajności najlepiej znają ilość nakładających się operacji gniazda, które muszą być podtrzymywane. Aplikacja może utworzyć dowolną <xref:System.Net.Sockets.SocketAsyncEventArgs> liczbę obiektów, których potrzebuje. Na przykład jeśli aplikacja serwera musi mieć 15 gniazdo zaakceptować operacje zaległe przez cały czas <xref:System.Net.Sockets.SocketAsyncEventArgs> do obsługi przychodzących stawek połączenia klienta, można przydzielić 15 obiektów wielokrotnego użytku z wyprzedzeniem w tym celu.  
  
 Wzorzec do wykonywania operacji gniazda asynchroniiowego z tej klasy składa się z następujących kroków:  
  
1. Przydziel <xref:System.Net.Sockets.SocketAsyncEventArgs> nowy obiekt kontekstu lub uzyskaj wolny obiekt z puli aplikacji.  
  
2. Ustaw właściwości obiektu kontekstu do operacji, która ma zostać wykonana (na przykład metoda delegowania wywołania zwrotnego i bufor danych).  
  
3. Wywołanie odpowiedniej metody gniazda (xxxAsync), aby zainicjować operację asynchronicznej.  
  
4. Jeśli metoda gniazda asynchronicznego (xxxAsync) zwraca wartość true w wywołaniu zwrotnym, kwerenda właściwości kontekstu dla stanu ukończenia.  
  
5. Jeśli metoda gniazda asynchronicznego (xxxAsync) zwraca false w wywołaniu zwrotnym, operacja została ukończona synchronicznie. Właściwości kontekstu mogą być wyszukiwane dla wyniku operacji.  
  
6. Ponownie użyć kontekstu dla innej operacji, umieścić go z powrotem w puli lub odrzucić go.  
  
 Okres istnienia nowego obiektu kontekstu operacji asynchroniiowego gniazda jest określany przez odwołania w kodzie aplikacji i asynchroniczne odwołania we/wy. Nie jest konieczne dla aplikacji zachować odwołanie do obiektu kontekstu kontekstu operacji asynchroniiowego gniazda po jego przesłaniu jako parametr do jednej z metod operacji gniazda asynchronii. Pozostanie odwołuje się do zakończenia wywołania zwrotnego zwraca. Jednak jest korzystne dla aplikacji zachować odwołanie do obiektu kontekstu, dzięki czemu może być ponownie wykorzystany do przyszłej operacji gniazda asynchroniiowego.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>
- [Przykłady programowania sieciowego](network-programming-samples.md)
- [Przykłady kodu gniazd](socket-code-examples.md)
