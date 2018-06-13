---
title: Scenariusze asynchroniczne z zastosowaniem protokołu HTTP lub TCP albo potoku nazwanego
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: d08f70186a59b8717c4441167ee720ba1c20b9dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474711"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>Scenariusze asynchroniczne z zastosowaniem protokołu HTTP lub TCP albo potoku nazwanego
W tym temacie opisano działania i transferów w scenariuszach różnych asynchroniczne żądanie/odpowiedź z żądaniami wielowątkowe przy użyciu protokołu HTTP, TCP, lub nazwany potok.  
  
## <a name="asynchronous-requestreply-without-errors"></a>Asynchroniczne żądanie/odpowiedź bez błędów  
 W tej sekcji opisano działania i transferów scenariusz asynchroniczne żądanie/odpowiedź, klientom wielowątkowych.  
  
 Działanie wywołującego kończy kiedy `beginCall` zwraca, i `endCall` zwraca. Jeśli wywołanie zwrotne po wywołaniu zwraca wywołania zwrotnego.  
  
 Kończy działanie o nazwie, kiedy `beginCall` zwraca, `endCall` zwróci wartość, lub gdy wywołanie zwrotne zwraca, jeśli została wywołana z tego działania.  
  
### <a name="asynchronous-client-without-callback"></a>Asynchroniczne klienta bez wywołania zwrotnego  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>Propagacja jest włączona na obie strony przy użyciu protokołu HTTP  
 ![Scenariusze asynchroniczne](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")  
  
 Rysunek 1. Asynchroniczne klienta, bez wywołania zwrotnego `propagateActivity` = `true` po obu stronach HTTP  
  
 Jeśli `propagateActivity` = `true`, ProcessMessage wskazuje ProcessAction działanie (activity) na transfer do.  
  
 W przypadku scenariuszy oparte na protokole HTTP ReceiveBytes jest wywoływana na pierwszy komunikat do wysłania i czy istnieje dla okresu istnienia żądania.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>Propagacja jest wyłączona na stronach albo przy użyciu protokołu HTTP  
 Jeśli `propagateActivity` = `false` po obu stronach ProcessMessage nie wskazuje ProcessAction działanie (activity) na transfer do. W związku z tym wywołaniu nowego, tymczasowego działania ProcessAction z nowym Identyfikatorem. Po dopasowaniu asynchroniczne odpowiedzi na żądanie w kodzie ServiceModel, identyfikator działania można pobrać z kontekstu lokalnego. Rzeczywiste działania ProcessAction mogą zostać przeniesione do o tym identyfikatorze.  
  
 ![Scenariusze asynchroniczne z zastosowaniem protokołu HTTP&#47;TCP&#47;nazwanego potoku](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")  
  
 Rysunek 2. Asynchroniczne klienta, bez wywołania zwrotnego `propagateActivity` = `false` po obu stronach HTTP  
  
 W przypadku scenariuszy oparte na protokole HTTP ReceiveBytes jest wywoływana na pierwszy komunikat do wysłania i czy istnieje dla okresu istnienia żądania.  
  
 Działanie procesu akcji jest tworzony na kliencie asynchronicznych po `propagateActivity` = `false` na wywołujący lub wywoływany i gdy komunikat odpowiedzi nie zawiera nagłówka Action.  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>Propagacja jest włączona na obie strony przy użyciu protokołu TCP lub nazwanego potoku  
 ![Scenariusze asynchroniczne z zastosowaniem protokołu HTTP&#47;TCP&#47;nazwanego potoku](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")  
  
 Rysunek 3. Asynchroniczne klienta, bez wywołania zwrotnego `propagateActivity` = `true` po obu stronach nazwanego-potoku/TCP  
  
 W scenariuszu potoków nazwanych lub opartych na protokole TCP ReceiveBytes jest wywoływane, gdy klient jest otwarty i istnieje przez czas ich istnienia połączenia.  
  
 Podobnie jak rysunek 1, jeśli `propagateActivity` = `true`, ProcessMessage wskazuje ProcessAction działanie (activity) na transfer do.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>Propagacja jest wyłączona na stronach albo przy użyciu protokołu TCP lub nazwanego potoku  
 W scenariuszu potoków nazwanych lub opartych na protokole TCP ReceiveBytes jest wywoływane, gdy klient jest otwarty i istnieje przez czas ich istnienia połączenia.  
  
 Podobnie jak Fig.2, jeśli `propagateActivity` = `false` po obu stronach ProcessMessage nie wskazuje ProcessAction działanie (activity) na transfer do. W związku z tym wywołaniu nowego, tymczasowego działania ProcessAction z nowym Identyfikatorem. Po dopasowaniu asynchroniczne odpowiedzi na żądanie w kodzie ServiceModel, identyfikator działania można pobrać z kontekstu lokalnego. Rzeczywiste działania ProcessAction mogą zostać przeniesione do o tym identyfikatorze.  
  
 ![Scenariusze asynchroniczne z zastosowaniem protokołu HTTP&#47;TCP&#47; potoków nazwanych](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")  
  
 Rysunek 4. Asynchroniczne klienta, bez wywołania zwrotnego `propagateActivity` = `false` po obu stronach nazwanego-potoku/TCP  
  
### <a name="asynchronous-client-with-callback"></a>Asynchroniczne klienta z wywołania zwrotnego  
 W tym scenariuszu dodaje działań, G i A ", dla wywołania zwrotnego i `endCall`i ich transferów we/wy.  
  
 W tej sekcji przedstawiono tylko przy użyciu protokołu HTTP z `propragateActivity` = `true`. Jednak dodatkowe działania i transferów dotyczą również innych przypadkach (to znaczy `propagateActivity` = `false`, przy użyciu lub TCP albo potoku nazwanego).  
  
 Wywołanie zwrotne tworzy nowe działanie (G), kiedy klient wywołuje kod użytkownika w celu powiadomienia, że wyniki są gotowe. Kod użytkownika wywołuje `endCall` wewnątrz wywołania zwrotnego (jak pokazano na rysunku 5) lub na zewnątrz wywołania zwrotnego (rysunek 6). Ponieważ nie wiadomo, które aktywności użytkownika `endCall` jest wywoływana z etykietą tego działania `A’`. Istnieje możliwość, A "może być taki sam jak lub inny niż A.  
  
 ![Scenariusze asynchroniczne](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")  
  
 Rysunek 5. Asynchroniczne klienta z wywołania zwrotnego, `endCall` w wywołania zwrotnego  
  
 ![Scenariusze asynchroniczne](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")  
  
 Rysunek 6. Asynchroniczne klienta z wywołania zwrotnego, `endCall` poza wywołania zwrotnego  
  
### <a name="asynchronous-server-with-callback"></a>Asynchroniczne serwera z wywołania zwrotnego  
 ![Scenariusze asynchroniczne z zastosowaniem protokołu HTTP&#47;TCP&#47; nazwane&#45;potoku](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")  
  
 Rysunek 7. Serwer asynchroniczne wywołanie zwrotne  
  
 Stos kanału wywołuje klienta na odbieranie komunikatu: danych śledzenia dla tego przetwarzania są emitowane w działaniu ProcessRequest dla samej siebie.  
  
## <a name="asynchronous-requestreply-with-errors"></a>Asynchroniczne żądanie/odpowiedź z błędami  
 Błędy wiadomości są odbierane podczas `endCall`. W przeciwnym razie działań i transferów są podobne do poprzednich scenariuszach.  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>Asynchroniczne jednokierunkowe z lub bez błędów  
 Nie odpowiedzi lub fault jest zwracana do klienta.
