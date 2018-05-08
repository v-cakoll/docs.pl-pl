---
title: Propagacja identyfikatora działania
ms.date: 03/30/2017
ms.assetid: cd1c1ae5-cc8a-4f51-90c9-f7b476bcfe70
ms.openlocfilehash: e51970f693d9ca2d2f81bf4efc97969896de4828
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="activity-id-propagation"></a>Propagacja identyfikatora działania
Propagacja odbywa się podczas ServiceModel czynność śledzenia jest włączona (ServiceModel propagacji) lub wyłączona (propagowania działań użytkownika).  
  
## <a name="servicemodel-activity-tracing-is-enabled"></a>Jest włączone śledzenie działania ServiceModel  
 Po włączeniu ServiceModel ActivityTracing propagacji odbywa się między działaniami ProcessAction.  
  
### <a name="server"></a>Serwer  
 Gdy `propagateActivity` atrybut ma ustawioną `true` na kliencie i serwerze identyfikator `ProcessAction` działania na serwerze jest taki sam jak identyfikator w propagowany `ActivityId` nagłówek komunikatu.  
  
 Gdy nie `ActivityId` nagłówka znajduje się w komunikacie (to znaczy `propagateActivity` = `false` na kliencie), lub gdy `propagateActivity` = `false` na serwerze, serwer generuje nowy identyfikator działania.  
  
### <a name="client"></a>Klient  
 Jeśli klient jest synchronicznie pojedynczego wątku, klient pomija wszelkie ustawienia `propagateActivity` na klienta lub serwera. Zamiast tego odpowiedzi jest obsługiwany w działaniu żądania. Jeśli klient jest asynchroniczne i synchroniczne wielowątkowe, `propagateActivity` = `true` w kliencie i brak nagłówka Identyfikatora aktywności w komunikacie wysyłane przez serwer, klient pobiera identyfikator działania z komunikatu i przesyła do Działanie akcji procesu, który zawiera identyfikator propagowany działania. W przeciwnym razie klient przesyła z działania procesu komunikatu do nowego działania procesu akcji. To dodatkowe przeniesienie do nowego działania procesu akcji odbywa się dla spójności. Wewnątrz tego działania klient pobiera identyfikator działania działania BeginCall w kontekście lokalnego wątku po wątek został przydzielony do przetwarzania komunikatów odpowiedzi. Następnie przesyła początkowej działania procesu akcji.  
  
 Jeśli klient jest dupleksowy, klient działa jako serwer po otrzymaniu komunikatu.  
  
### <a name="propagation-in-fault-messages"></a>Propagacją komunikatów "Fault"  
 Nie ma żadnej różnicy w Obsługa prawidłowe i komunikaty o błędach. Jeśli `propagateActivity` = `true`, identyfikator działania ma nagłówki komunikatów SOAP błędów jest identyczna jak działanie otoczenia.  
  
## <a name="servicemodel-activity-tracing-is-disabled"></a>Śledzenie działania ServiceModel jest wyłączona.  
 Po wyłączeniu ServiceModel ActivityTracing propagacji występuje między działaniami kodu użytkownika bezpośrednio, bez pośrednictwa ServiceModel działań. Identyfikator działania zdefiniowane przez użytkownika również są propagowane do nagłówka Identyfikatora aktywności wiadomości.  
  
 Jeśli `propagateActivity` = `true` i `ActivityTracing` = `off` dla odbiornika śledzenia ServiceModel (niezależnie od tego, czy śledzenie jest włączone w modelu ServiceModel), następujące się zdarzyć, klienta lub serwera:  
  
-   Na żądanie operacji lub wysyłania odpowiedzi identyfikator działania w protokole TLS są propagowane z kodu użytkownika, dopóki nie jest sformatowany komunikat. Nagłówka Identyfikatora aktywności również jest wstawiany komunikat przed ich wysłaniem.  
  
-   Na żądania odbierania lub odbieranie odpowiedzi, identyfikator działania są pobierane z nagłówka wiadomości natychmiast po utworzeniu obiektu odebranego komunikatu. Identyfikator działania w protokole TLS są propagowane jak komunikat zniknie z zakresu, aż do osiągnięcia kodu użytkownika.  
  
 Te akcje gwarantuje, że śladów użytkownika pojawi się w to samo działanie, jeśli propagację znajduje się na. Jej nie udostępnia jednak żadnej gwarancji na śladów ServiceModel. Ślady ServiceModel wystąpić w działaniu kodu użytkownika tylko wtedy, gdy przetwarzanie tych danych śledzenia jest wykonywane na tym samym wątku, w którym działanie kodu użytkownika została ustawiona.  
  
 Ogólnie rzecz biorąc można zaobserwować śladów ServiceModel w następujących miejscach:  
  
-   Jeśli ServiceModel śledzenie jest wyłączone, wszystkie ślady emitowany wyświetlana działań użytkownika. Po włączeniu serwera i klienta propagacji te operacje śledzenia będą w tym samym działaniu.  
  
-   Jeśli ServiceModel śledzenie jest włączone, ale ActivityTracing jest wyłączona, dane śledzenia użytkownika są wyświetlane w to samo działanie, jeśli Propagacja jest włączona po obu stronach. Ślady ServiceModel wyświetlana domyślne działanie 0000, jeśli występują one w tym samym wątku, co przetwarzania kodu użytkownika, gdy działanie jest początkowo ustawiona.  
  
-   Jeśli zarówno śledzenie ServiceModel i ActivityTracing są włączone, śledzenie użytkowników są wyświetlane w zdefiniowanych przez użytkownika działań i ślady ServiceModel pojawiają się w zdefiniowanych ServiceModel działań. Propagacja odbywa się na poziomie modelu ServiceModel.
