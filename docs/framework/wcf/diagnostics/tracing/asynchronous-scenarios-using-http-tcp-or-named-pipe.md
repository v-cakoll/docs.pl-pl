---
title: Scenariusze asynchroniczne z zastosowaniem protokołu HTTP lub TCP albo potoku nazwanego
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: d08f70186a59b8717c4441167ee720ba1c20b9dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998293"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>Scenariusze asynchroniczne z zastosowaniem protokołu HTTP lub TCP albo potoku nazwanego
W tym temacie opisano działania i transferów w scenariuszach różnych asynchroniczne żądanie/nietypizowana odpowiedź z żądaniami wielowątkowe przy użyciu protokołu HTTP, TCP, lub nazwany potok.  
  
## <a name="asynchronous-requestreply-without-errors"></a>Asynchroniczne żądanie/nietypizowana odpowiedź bez błędów  
 W tej sekcji opisano działania i transferów w scenariuszu asynchroniczne żądanie/nietypizowana odpowiedź z klientami wielowątkowych.  
  
 Działanie obiekt wywołujący skończy się, gdy `beginCall` zwróci wartość, a `endCall` zwraca. Jeśli wywołanie zwrotne jest wywoływana, zwraca wartość wywołania zwrotnego.  
  
 Działania o nazwie skończy się, gdy `beginCall` zwraca, `endCall` zwróci wartość, lub gdy wywołania zwrotnego zwraca, jeśli została wywołana z danego działania.  
  
### <a name="asynchronous-client-without-callback"></a>Asynchroniczne klienta bez wywołania zwrotnego  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>Propagacja jest włączona po obu stronach, przy użyciu protokołu HTTP  
 ![Scenariusze asynchroniczne](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")  
  
 Rysunek 1. Asynchroniczne klienta, bez wywołania zwrotnego `propagateActivity` = `true` po obu stronach, HTTP  
  
 Jeśli `propagateActivity` = `true`, ProcessMessage wskazuje, które działania ProcessAction przesyłać do.  
  
 W przypadku scenariuszy opartych na protokole HTTP ReceiveBytes jest wywoływane na pierwszy komunikat do wysłania i istnieje okres istnienia żądania.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>Propagacja jest wyłączona na stronach albo przy użyciu protokołu HTTP  
 Jeśli `propagateActivity` = `false` po obu stronach ProcessMessage nie wskazuje, które działania ProcessAction przesyłać do. W związku z tym nowe działanie ProcessAction tymczasowe z nowym Identyfikatorem jest wywoływana. Po dopasowaniu asynchronicznych odpowiedzi na żądanie w modelu ServiceModel kodu, identyfikator działania można pobrać z kontekstu lokalnego. Rzeczywiste działanie ProcessAction mogą zostać przeniesione do za pomocą tego identyfikatora.  
  
 ![Scenariusze asynchroniczne z zastosowaniem protokołu HTTP&#47;TCP&#47;nazwanego potoku](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")  
  
 Rysunek 2. Asynchroniczne klienta, bez wywołania zwrotnego `propagateActivity` = `false` po obu stronach HTTP  
  
 W przypadku scenariuszy opartych na protokole HTTP ReceiveBytes jest wywoływane na pierwszy komunikat do wysłania i istnieje okres istnienia żądania.  
  
 Działanie procesu akcji jest tworzony na komputerze klienckim asynchronicznego podczas `propagateActivity` = `false` wywołujący lub wywoływany i gdy komunikat odpowiedzi zawiera nagłówek akcji.  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>Propagacja jest włączona po obu stronach, przy użyciu protokołu TCP lub nazwanego potoku  
 ![Scenariusze asynchroniczne z zastosowaniem protokołu HTTP&#47;TCP&#47;nazwanego potoku](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")  
  
 Rysunek 3. Asynchroniczne klienta, bez wywołania zwrotnego `propagateActivity` = `true` po obu stronach nazwanych-potoku/TCP  
  
 W scenariuszu nazwanego lub oparte na protokole TCP ReceiveBytes jest wywoływane, gdy klient jest otwarty i istnieje okres istnienia połączenia.  
  
 Podobnie jak rysunek 1, jeśli `propagateActivity` = `true`, ProcessMessage wskazuje, które działania ProcessAction przesyłać do.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>Propagacja jest wyłączona na stronach albo przy użyciu protokołu TCP lub nazwanego potoku  
 W scenariuszu nazwanego lub oparte na protokole TCP ReceiveBytes jest wywoływane, gdy klient jest otwarty i istnieje okres istnienia połączenia.  
  
 Podobnie jak Fig.2, jeśli `propagateActivity` = `false` po obu stronach ProcessMessage nie wskazuje, które działania ProcessAction przesyłać do. W związku z tym nowe działanie ProcessAction tymczasowe z nowym Identyfikatorem jest wywoływana. Po dopasowaniu asynchronicznych odpowiedzi na żądanie w modelu ServiceModel kodu, identyfikator działania można pobrać z kontekstu lokalnego. Rzeczywiste działanie ProcessAction mogą zostać przeniesione do za pomocą tego identyfikatora.  
  
 ![Scenariusze asynchroniczne z zastosowaniem protokołu HTTP&#47;TCP&#47; potoków nazwanych](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")  
  
 Rysunek 4. Asynchroniczne klienta, bez wywołania zwrotnego `propagateActivity` = `false` po obu stronach nazwanych-potoku/TCP  
  
### <a name="asynchronous-client-with-callback"></a>Asynchroniczne klienta przy użyciu wywołania zwrotnego  
 W tym scenariuszu dodaje działań, G i A ", wywołania zwrotnego i `endCall`i ich transferu we/wy.  
  
 W tej sekcji przedstawiono tylko przy użyciu protokołu HTTP z `propragateActivity` = `true`. Jednak dodatkowe działania i transfery dotyczą również innych przypadkach (czyli `propagateActivity` = `false`, przy użyciu lub TCP albo potoku nazwanego).  
  
 Wywołanie zwrotne tworzy nowe działanie (G), gdy klient wywołuje kod użytkownika, aby powiadomić, że wyniki są gotowe. Kod użytkownika wywołuje `endCall` w ramach wywołania zwrotnego (jak pokazano na rysunku 5) lub poza wywołanie zwrotne (rysunek 6). Ponieważ nie jest znany aktywności użytkownika, które `endCall` jest wywoływana, to działanie jest oznaczona etykietą `A’`. Istnieje możliwość, A "może być taka sama jak lub różni się od A.  
  
 ![Scenariusze asynchroniczne](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")  
  
 Rysunek 5. Asynchroniczne klienta z wywołaniem zwrotnym, `endCall` w wywołania zwrotnego  
  
 ![Scenariusze asynchroniczne](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")  
  
 Rysunek 6. Asynchroniczne klienta z wywołaniem zwrotnym, `endCall` poza wywołania zwrotnego  
  
### <a name="asynchronous-server-with-callback"></a>Asynchroniczne serwera przy użyciu wywołania zwrotnego  
 ![Scenariusze asynchroniczne z zastosowaniem protokołu HTTP&#47;TCP&#47; nazwanych&#45;potoku](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")  
  
 Rysunek 7. Asynchroniczne serwera, za pomocą wywołania zwrotnego  
  
 Stos kanału wywołuje klienta na Message Receive: danych śledzenia dla tego przetwarzania są emitowane w ProcessRequest działania.  
  
## <a name="asynchronous-requestreply-with-errors"></a>Asynchroniczne żądanie/nietypizowana odpowiedź z błędami  
 Błędy wiadomości są odbierane podczas `endCall`. W przeciwnym razie działań i transfery są podobne do poprzednich scenariuszach.  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>Asynchroniczne jednokierunkowe, z lub bez błędów  
 Nie odpowiedzi lub błąd jest zwracany do klienta.
