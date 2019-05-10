---
title: Propagacja identyfikatora działania
ms.date: 03/30/2017
ms.assetid: cd1c1ae5-cc8a-4f51-90c9-f7b476bcfe70
ms.openlocfilehash: 642d4da49f90d3fc6f2b0dfc9896d724acb075b5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651807"
---
# <a name="activity-id-propagation"></a>Propagacja identyfikatora działania
Propagacja występuje, gdy ServiceModel działania śledzenie jest włączone (ServiceModel propagacji) lub wyłączony (Propagacja działania użytkownika do użytkownika).  
  
## <a name="servicemodel-activity-tracing-is-enabled"></a>Włączone jest śledzenie aktywności modelu ServiceModel  
 Po włączeniu ServiceModel ActivityTracing propagacji odbywa się między działaniami ProcessAction.  
  
### <a name="server"></a>Serwer  
 Gdy `propagateActivity` ma ustawioną wartość atrybutu `true` na kliencie i serwerze identyfikator `ProcessAction` aktywności na serwerze jest taka sama jak identyfikator w propagowany `ActivityId` nagłówka komunikatu.  
  
 Gdy nie `ActivityId` nagłówka znajduje się w komunikacie (oznacza to, że `propagateActivity` = `false` na kliencie), lub gdy `propagateActivity` = `false` na serwerze, serwer generuje nowy identyfikator działania.  
  
### <a name="client"></a>Klient  
 Jeśli klient znajduje się synchronicznie pojedynczego wątku, klient pomija wszelkie ustawienia `propagateActivity` u klienta lub serwera. Zamiast tego odpowiedzi jest obsługiwany w działaniu żądania. Jeśli klient znajduje się asynchronicznego lub synchronicznego wielowątkowych, `propagateActivity` = `true` w kliencie i brak nagłówka Identyfikatora aktywności w wiadomości wysłanych przez serwer, klient pobiera identyfikator działania z komunikatu i przesyła do Działania akcji procesu, który zawiera identyfikator propagowany działania. W przeciwnym razie klient przesyła z działania procesu komunikatu do nowego działania procesu akcji. Ten dodatkowy przesyłanie danych do nowego działania procesu akcji odbywa się w celu zachowania spójności. Wewnątrz tego działania klient pobiera identyfikator działania działania BeginCall w kontekście wątku lokalnego, gdy wątek jest przydzielany do przetwarzania komunikatów odpowiedzi. Następnie przekazuje początkowe działanie procesu akcji.  
  
 Jeśli klient jest dupleksowy, klient działa jako serwer po odebraniu wiadomości.  
  
### <a name="propagation-in-fault-messages"></a>Propagacji komunikaty o błędach  
 Nie ma różnic w obsłudze prawidłowe i komunikaty o błędach. Jeśli `propagateActivity` = `true`, identyfikator działania dodane do nagłówków wiadomości błędu protokołu SOAP jest taka sama jak działanie otoczenia.  
  
## <a name="servicemodel-activity-tracing-is-disabled"></a>Śledzenie działań ServiceModel jest wyłączona  
 Wyłączenie ServiceModel ActivityTracing propagacji odbywa się między działania kodu użytkownika bezpośrednio, bez przechodzenia przez działania elementu ServiceModel. Identyfikator działania zdefiniowane przez użytkownika jest również powielana nagłówka Identyfikatora aktywności wiadomości.  
  
 Jeśli `propagateActivity` = `true` i `ActivityTracing` = `off` dla odbiornika śledzenia elementu ServiceModel (niezależnie od tego, czy śledzenie jest włączone w modelu ServiceModel), następujące powinny być wykonywane dla klienta lub serwera:  
  
- Na żądanie operacji lub wysyłania odpowiedzi identyfikator działania w protokole TLS są propagowane z kodu użytkownika, dopóki nie jest sformułowany komunikat. Nagłówka Identyfikatora aktywności również zostaną wstawione do wiadomości, przed ich wysłaniem.  
  
- Odbiera żądania lub odbiera odpowiedź, identyfikator działania są pobierane z nagłówka wiadomości, zaraz po utworzeniu obiektu odebranego komunikatu. Identyfikator działania w protokole TLS są propagowane tak szybko, jak długo komunikat zniknie z zakresu, aż do osiągnięcia kod użytkownika.  
  
 Te akcje gwarantuje, że ślady użytkownika pojawi się w tym samym działaniu, jeśli propagację znajduje się na. Jednak to sprawia, że żadnej gwarancji na ślady elementu ServiceModel. Ślady ServiceModel wystąpić w działaniu kodu użytkownika tylko wtedy, gdy przetwarzanie tych danych śledzenia jest wykonywane na tym samym wątku, w którym działanie kodu użytkownika została ustawiona.  
  
 Ogólnie rzecz biorąc można zaobserwować ServiceModel ślady w następujących miejscach:  
  
- Jeśli ServiceModel śledzenie jest wyłączone, wszystkie ślady emitowany pojawiają się w aktywność użytkowników. Po włączeniu propagacji na serwer i klient ślady te będą w ramach tego samego działania.  
  
- Jeśli włączone jest śledzenie elementu ServiceModel, ale ActivityTracing jest wyłączona, ślady użytkownika są wyświetlane w tym samym działaniu, jeśli Propagacja jest włączona na obu końcach. Ślady ServiceModel wyświetlana domyślne działanie 0000, jeśli występują one w tym samym wątku, ponieważ przetwarzanie kodu użytkownika, których działanie początkowo ma wartość.  
  
- Włączenie śledzenia modelu ServiceModel i ActivityTracing są ślady użytkownika są wyświetlane w działaniach użytkownika i ślady ServiceModel pojawiają się w działania zdefiniowane w modelu ServiceModel. Propagacja odbywa się na poziomie elementu ServiceModel.
