---
title: "Ulepszenia wydajności gniazda w wersji 3.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1d4746e2303949ddeabee36e4875e7480467f33e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="socket-performance-enhancements-in-version-35"></a>Ulepszenia wydajności gniazda w wersji 3.5
<xref:System.Net.Sockets.Socket?displayProperty=nameWithType> Klasa została rozszerzona w wersji 3.5 do użycia przez aplikacje używające sieci asynchroniczne We/Wy, aby osiągnąć najwyższą wydajność. Dodano szereg nowych klas jako część zestawu rozszerzeń <xref:System.Net.Sockets.Socket> klasy, która zapewnić alternatywne wzorca asynchronicznego, które mogą być używane przez aplikacje specjalistyczne gniazda wysokiej wydajności. Te ulepszenia zostały zaprojektowane specjalnie dla aplikacji serwera sieci, które wymagają wysokiej wydajności. Aplikację można używać wyłącznie rozszerzone wzorca asynchronicznego lub tylko w docelowe gorących obszary aplikacji (w przypadku odbierania dużej ilości danych, na przykład).  
  
## <a name="class-enhancements"></a>Rozszerzenia klasy  
 Funkcja głównego tych rozszerzeń jest unikanie powtarzane alokacji i synchronizacji obiektów w trakcie dużych gniazda asynchroniczne We/Wy. Wzorzec projektowy początek i koniec obecnie implementowane przez <xref:System.Net.Sockets.Socket> klasy dla gniazda asynchroniczne We/Wy wymaga <xref:System.IAsyncResult?displayProperty=nameWithType> obiektu przydzielone dla każdej operacji asynchronicznej gniazda.  
  
 W nowym <xref:System.Net.Sockets.Socket> klasy rozszerzenia gniazda asynchroniczne operacje, których dotyczą wielokrotnego użytku <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> klasy obiektów przydzielone i obsługiwane przez aplikację. Aplikacje wysokiej wydajności gniazda najlepiej znać ilość operacji nakładających się gniazda, które muszą być przez dłuższy czas. Aplikację można utworzyć dowolną liczbę z <xref:System.Net.Sockets.SocketAsyncEventArgs> obiektów, które są wymagane. Na przykład jeśli aplikacja serwera wymaga się 15 gniazda zaakceptować oczekujące operacje przez cały czas do obsługi przychodzących szybkości połączenia klienta, go przydzielić 15 wielokrotnego użytku <xref:System.Net.Sockets.SocketAsyncEventArgs> obiektów wcześniej w tym celu.  
  
 Wzorzec do wykonywania asynchroniczna Operacja gniazda z tą klasą składa się z następujących czynności:  
  
1.  Przydziel nowej <xref:System.Net.Sockets.SocketAsyncEventArgs> kontekst obiektu lub uzyskać bezpłatne od puli aplikacji.  
  
2.  Ustawianie właściwości w kontekście obiektu do operacji o należy wykonać (wywołanie zwrotne obiektu delegowanego — metoda i danych buforu, na przykład).  
  
3.  Wywołaj metodę odpowiednie gniazda (xxxAsync) można zainicjować operacji asynchronicznej.  
  
4.  Jeśli metoda asynchroniczne gniazda (xxxAsync) zwraca wartość true, podczas wywołania zwrotnego, zapytania właściwości kontekstu stan ukończenia.  
  
5.  Jeśli metoda asynchroniczne gniazda (xxxAsync) zwraca wartość false w wywołania zwrotnego, operacja została wykonana synchronicznie. Właściwości kontekstu może żądać dla wyniku operacji.  
  
6.  Ponowne użycie w kontekście innej operacji, umieść ją w puli lub odrzucić go.  
  
 Okres istnienia nowy obiekt kontekstu operacji asynchronicznych gniazda jest określana przez odwołań w kodzie aplikacji i odwołania do asynchronicznego We/Wy. Nie jest niezbędna dla aplikacji, aby zachować odwołanie do obiektu kontekstu operacji asynchronicznych gniazda po przesłaniu go jako parametr do jednej z metod operacji asynchronicznych gniazda. Pozostanie do którego istnieje odwołanie do momentu ukończenia wywołania zwrotnego zwraca. Jednak jest korzystne dla aplikacji, aby zachować odwołanie do obiektu context, dzięki czemu mogą być ponownie używane dla przyszłych asynchroniczna Operacja gniazda.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>  
 [Przykłady programowania w języku sieci](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Próbka technologii wydajności gniazda](http://go.microsoft.com/fwlink/?LinkID=179570)
