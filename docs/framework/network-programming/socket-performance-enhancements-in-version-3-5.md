---
title: Ulepszenia wydajności gniazda w wersji 3.5
ms.date: 03/30/2017
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0570241fa81b0870500daa9d6e94b45c28042737
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43255383"
---
# <a name="socket-performance-enhancements-in-version-35"></a>Ulepszenia wydajności gniazda w wersji 3.5
<xref:System.Net.Sockets.Socket?displayProperty=nameWithType> Klasa została rozszerzona w wersji 3.5 do użycia przez aplikacje, które używają sieci asynchronicznych operacji We/Wy, aby osiągnąć najwyższą wydajność. Szereg nowych klas zostały dodane jako część zbioru ulepszeń klasy <xref:System.Net.Sockets.Socket> klasy, która zapewnia alternatywny wzorzec asynchroniczny, które mogą być używane przez aplikacje specjalistyczne gniazda o wysokiej wydajności. Te ulepszenia zostały zaprojektowane specjalnie dla sieci serwer aplikacji, które wymagają wysokiej wydajności. Aplikację można użyć wyłącznie rozszerzone wzorca asynchronicznego lub tylko w docelowej gorąca obszarów aplikacji (w przypadku odbierania dużej ilości danych, na przykład).  
  
## <a name="class-enhancements"></a>Klasa rozszerzenia  
 Główna funkcja te rozszerzenia funkcjonalności jest unikanie powtarzanych alokacji i synchronizacji obiektów w trakcie gniazda asynchronicznego dużej liczby operacji We/Wy. Wzorzec projektowy początek/koniec, które są obecnie implementowane przez <xref:System.Net.Sockets.Socket> klasy dla gniazda asynchronicznych operacji We/Wy wymaga <xref:System.IAsyncResult?displayProperty=nameWithType> obiektu można przydzielić dla każdej operacji asynchronicznych gniazda.  
  
 W nowym <xref:System.Net.Sockets.Socket> klasy rozszerzenia asynchronicznego gniazda operacje są opisane przez wielokrotnego użytku, do <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> klasy obiekty przydzielone i utrzymywane przez aplikację. Aplikacji wykorzystujących gniazda o wysokiej wydajności najlepiej znać ilości operacji nachodzące gniazda, które muszą być utrzymywane. Aplikację można utworzyć dowolną liczbę z <xref:System.Net.Sockets.SocketAsyncEventArgs> obiekty, których potrzebuje. Na przykład jeśli aplikacja serwera musi mieć 15 gniazda zaakceptować oczekujących operacji przez cały czas do obsługi przychodzących szybkości połączenia klienta, go przydzielić 15 wielokrotnego użytku <xref:System.Net.Sockets.SocketAsyncEventArgs> obiektów z wyprzedzeniem do tego celu.  
  
 Wzorzec do wykonywania operacji asynchronicznej gniazda z tą klasą składa się z następujących czynności:  
  
1.  Przydziel nowej <xref:System.Net.Sockets.SocketAsyncEventArgs> kontekst obiektu lub pobrać za darmo z puli aplikacji.  
  
2.  Ustawianie właściwości w kontekście obiektu do operacji o być wykonana (wywołanie zwrotne delegata metody i danych buforu, na przykład).  
  
3.  Wywołaj metodę odpowiednią gniazda (xxxAsync), aby zainicjować operację asynchroniczną.  
  
4.  Jeśli metoda asynchronicznego gniazda (xxxAsync) zwraca wartość true, podczas wywołania zwrotnego, tworzenie zapytań o właściwości kontekstu dla stanu ukończenia.  
  
5.  Jeśli metoda asynchronicznego gniazda (xxxAsync) zwraca wartość false podczas wywołania zwrotnego, operacja została ukończona synchronicznie. Właściwości kontekstu może być badane wyniku operacji.  
  
6.  Ponowne użycie w kontekście innej operacji, umieścić go w puli lub go odrzucić.  
  
 Okres istnienia nowy obiekt kontekstu operację asynchronicznego gniazda zależy od odwołania w kodzie aplikacji i odwołania do asynchronicznego We/Wy. Nie jest wymagane dla aplikacji, aby zachować odwołanie do obiektu kontekstu operację asynchronicznego gniazda dopiero po przesłaniu go jako parametr do jednej z metod operację asynchronicznego gniazda. Pozostanie on odwołania do momentu ukończenia wywołania zwrotnego zwraca. Jednak jest korzystna dla aplikacji, aby zachować odwołanie do obiektu context, dzięki czemu mogą być ponownie używane dla operacji przyszłych asynchronicznego gniazda.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>  
 [Przykłady programowania sieciowego](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Przykłady kodu gniazd](socket-code-examples.md)
