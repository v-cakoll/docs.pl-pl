---
title: Scenariusze asynchroniczne z zastosowaniem protokołu HTTP lub TCP albo potoku nazwanego
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 6ae96c0aac5010adf37eb78ed57d1549885ece58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185787"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>Scenariusze asynchroniczne z zastosowaniem protokołu HTTP lub TCP albo potoku nazwanego
W tym temacie opisano działania i transfery dla różnych scenariuszy asynchronicznych żądań/odpowiedzi, z żądaniami wielowątkowymi przy użyciu protokołu HTTP, TCP lub nazwanego potoku.  
  
## <a name="asynchronous-requestreply-without-errors"></a>Asynchroniczne żądanie/odpowiedź bez błędów  
 W tej sekcji opisano działania i transfery dla asynchroniczny scenariusz żądania/odpowiedzi, z klientami wielowątkowymi.  
  
 Działanie wywołującego kończy `beginCall` się po `endCall` powrocie i zwraca. Jeśli wywołane jest wywołanie wywołania zwrotnego, zwraca wywołanie zwrotne.  
  
 Wywoływane działanie kończy `beginCall` się, gdy zwraca, `endCall` zwraca lub gdy wywołanie zwrotne zwraca, jeśli został wywołany z tego działania.  
  
### <a name="asynchronous-client-without-callback"></a>Klient asynchroniczne bez wywołania zwrotnego  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>Propagacja jest włączona po obu stronach, przy użyciu protokołu HTTP  
 ![Klient asynchroniczne bez wywołania zwrotnego, gdzie propagateActivity jest ustawiona na true po obu stronach.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)
  
 Jeśli `propagateActivity=true`, ProcessMessage wskazuje, do którego działania ProcessAction należy przenieść.  
  
 W przypadku scenariuszy opartych na protokonacie HTTP ReceiveBytes jest wywoływana w pierwszej wiadomości do wysłania i istnieje przez cały okres istnienia żądania.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>Propagacja jest wyłączona po obu stronach, przy użyciu protokołu HTTP  
 Jeśli `propagateActivity=false` po obu stronach ProcessMessage nie wskazuje, które działanie ProcessAction przenieść do. W związku z tym wywoływane jest nowe tymczasowe działanie ProcessAction o nowym identyfikatorze. Gdy odpowiedź asynchroniza jest dopasowywać do żądania w kodzie ServiceModel, identyfikator działania można pobrać z kontekstu lokalnego. Rzeczywiste działanie ProcessAction można przenieść do tego identyfikatora.  
  
 ![Klient asynchroniczne bez wywołania zwrotnego, gdzie propagateActivity jest ustawiona na false po obu stronach.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  

 W przypadku scenariuszy opartych na protokonacie HTTP ReceiveBytes jest wywoływana w pierwszej wiadomości do wysłania i istnieje przez cały okres istnienia żądania.  
  
 Działanie akcji procesu jest tworzony na kliencie `propagateActivity=false` asynchroniiowym, gdy w wywołującym lub wywołującym, a gdy komunikat odpowiedzi nie zawiera nagłówek akcji.  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>Propagacja jest włączona po obu stronach, przy użyciu TCP lub nazwanego potoku  
 ![Klient asynchroniczne bez wywołania zwrotnego, gdzie propagateActivity jest ustawiona na true po obu stronach i nazwany potok/TCP.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 W przypadku scenariusza opartego na potoku nazwanym lub TCP ReceiveBytes jest wywoływany po otwarciu klienta i istnieje przez cały okres istnienia połączenia.  
  
 Podobnie jak na pierwszym `propagateActivity=true`obrazie, if , ProcessMessage wskazuje, do którego działania ProcessAction należy przenieść.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>Propagacja jest wyłączona po obu stronach, przy użyciu protokołu TCP lub nazwanego potoku  
 W przypadku scenariusza opartego na potoku nazwanym lub TCP ReceiveBytes jest wywoływany po otwarciu klienta i istnieje przez cały okres istnienia połączenia.  
  
 Podobnie jak na drugim `propagateActivity=false` obrazie, jeśli po obu stronach ProcessMessage nie wskazuje, do którego działania ProcessAction należy przenieść. W związku z tym wywoływane jest nowe tymczasowe działanie ProcessAction o nowym identyfikatorze. Gdy odpowiedź asynchroniza jest dopasowywać do żądania w kodzie ServiceModel, identyfikator działania można pobrać z kontekstu lokalnego. Rzeczywiste działanie ProcessAction można przenieść do tego identyfikatora.  
  
 ![Klient asynchroniczne bez wywołania zwrotnego, gdzie propagateActivity jest ustawiona na false po obu stronach i nazwany potok/TCP.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  

### <a name="asynchronous-client-with-callback"></a>Klient asynchroniczne z wywołaniem zwrotnym  
 W tym scenariuszu dodaje działania G i `endCall`A', dla wywołania zwrotnego i , i ich transfery in/out.  
  
 W tej sekcji pokazano `propagateActivity` = `true`tylko użycie protokołu HTTP z plikem . Jednak dodatkowe działania i transfery mają również zastosowanie do `propagateActivity` = `false`innych przypadków (czyli za pomocą TCP lub Named-Pipe).  
  
 Wywołanie zwrotne tworzy nowe działanie (G), gdy klient wywołuje kod użytkownika, aby powiadomić, że wyniki są gotowe. Kod użytkownika `endCall` następnie wywołuje w wywołaniu zwrotnym (jak pokazano na rysunku 5) lub poza wywołaniem zwrotnym (Rysunek 6). Ponieważ nie wiadomo, z `endCall` której aktywności użytkownika jest wywoływana, to działanie jest oznaczone etykietą `A’`. Możliwe, że A' może być identyczna lub inna niż A.  
  
 ![Pokazuje klienta asynchronicznie z wywołaniem zwrotnym, endcall w wywołaniu zwrotnym.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  

 ![Pokazuje klienta asynchronicznie z wywołaniem zwrotnym, endcall poza wywołaniem zwrotnym.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  

### <a name="asynchronous-server-with-callback"></a>Serwer asynchroniczne z wywołaniem zwrotnym  
 ![Pokazuje serwer asynchroniczne z wywołaniem zwrotnym.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  

 Stos kanału wywołuje klienta na message receive: ślady dla tego przetwarzania są emitowane w ProcessRequest działania.  
  
## <a name="asynchronous-requestreply-with-errors"></a>Asynchroniczne żądanie/odpowiedź z błędami  
 Podczas `endCall`. W przeciwnym razie działania i transfery są podobne do poprzednich scenariuszy.  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>Asynchroniczne w jedną stronę z błędami lub bez  
 Żadna odpowiedź lub usterka nie jest zwracana do klienta.
