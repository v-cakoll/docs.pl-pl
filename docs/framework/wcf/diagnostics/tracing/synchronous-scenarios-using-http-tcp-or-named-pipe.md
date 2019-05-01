---
title: Scenariusze synchroniczne z zastosowaniem protokołu HTTP lub TCP albo potoku nazwanego
ms.date: 03/30/2017
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
ms.openlocfilehash: 28e612b190f4993e1ce7da0d1083c4e55f827d4a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784861"
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a>Scenariusze synchroniczne z zastosowaniem protokołu HTTP lub TCP albo potoku nazwanego
W tym temacie opisano działania i transferów w scenariuszach różnych synchroniczne żądanie/nietypizowana odpowiedź, za pomocą klienta jednowątkowe, przy użyciu protokołu HTTP, TCP lub nazwany potok. Zobacz [scenariusze asynchroniczne z zastosowaniem HTTP lub TCP albo potoku nazwanego](../../../../../docs/framework/wcf/diagnostics/tracing/asynchronous-scenarios-using-http-tcp-or-named-pipe.md) więcej informacji na temat żądań wielowątkowych.  
  
## <a name="synchronous-requestreply-without-errors"></a>Synchroniczne żądanie/nietypizowana odpowiedź bez błędów  
 W tej sekcji opisano działania i transferu dla scenariusza prawidłowe synchroniczne żądanie/nietypizowana odpowiedź, za pomocą klienta jednowątkowe.  
  
### <a name="client"></a>Klient  
  
#### <a name="establishing-communication-with-service-endpoint"></a>Ustanawianie komunikacji z punktu końcowego usługi  
 Klient jest tworzony i otwarty. Dla każdego z tych kroków otoczenia działania (A) jest przekazywana do "Konstruowania Client" (B) i "Otwarte Klienta" (C) działania odpowiednio. Dla każdego działania, przesyłane do otoczenia działania jest zawieszona do momentu przeniesienia, oznacza to, aż ServiceModel kod jest wykonywany.  
  
#### <a name="making-a-request-to-service-endpoint"></a>Zgłaszającą żądanie do punktu końcowego usługi  
 Działanie otoczenia jest przekazywana do działania "ProcessAction" (D). W ramach tego działania jest wysyłany komunikat żądania, a komunikat odpowiedzi są odbierane. Działanie kończy się, gdy sterowanie powraca do kodu użytkownika. Ponieważ żądań synchronicznych otoczenia działania wstrzymuje, aż formant powraca.  
  
#### <a name="closing-communication-with-service-endpoint"></a>Zamykanie komunikacji z punktu końcowego usługi  
 Zamknij działanie klienta, (I) jest tworzony z otoczenia działania. Jest to taka sama jak nowe i open.  
  
### <a name="server"></a>Serwer  
  
#### <a name="setting-up-a-service-host"></a>Konfigurowanie hosta usługi  
 ServiceHost nowych i otwórz działań (N i O) są tworzone na podstawie aktywności otoczenia (M).  
  
 Działanie odbiornika (P) jest tworzony z otwierania elementu ServiceHost dla każdego odbiornika. Działanie odbiornika oczekuje odbierania i przetwarzania danych.  
  
#### <a name="receiving-data-on-the-wire"></a>Odbieranie danych na potrzeby przesyłu  
 Po odebraniu danych na potrzeby przesyłu działania "ReceiveBytes" jest tworzony, jeśli go jeszcze nie istnieje (Q) do przetworzenia odebranych danych. To działanie można ponownie wielu komunikatów w ramach połączenia lub kolejki.  
  
 Działanie ReceiveBytes uruchamia czynnością ProcessMessage (R) ma wystarczającej ilości danych w celu utworzenia komunikatu działania protokołu SOAP.  
  
 W działaniu R nagłówków wiadomości są przetwarzane, a nagłówek activityID jest weryfikowany. Jeśli tego pliku nagłówkowego jest obecna, Identyfikator działania jest ustawiony na działanie ProcessAction; w przeciwnym razie jest tworzony nowy identyfikator.  
  
 Działanie ProcessAction (S) jest tworzone i przesyłane do, gdy wywołanie jest przetwarzany. To działanie kończy się po zakończeniu całego procesu przetwarzania związane z przychodzących wiadomości, łącznie z wykonywaniem kodu użytkownika (T) i wysyła komunikat odpowiedzi, jeśli ma to zastosowanie.  
  
#### <a name="closing-a-service-host"></a>Zamykanie hosta usługi  
 Zamknij działanie ServiceHost (Z) jest tworzony z otoczenia działania.  
  
 ![Diagram przedstawiający scenariusze synchroniczne: HTTP, TCP lub nazwanych potoków.](./media/synchronous-scenarios-using-http-tcp-or-named-pipe/synchronous-scenario-http-tcp-named-pipes.gif)  
  
 W \<A: name >, `A` to symbol skrótu opisujący działanie w poprzedni tekst i w tabeli 3. `Name` jest skróconą nazwę działania.  
  
 Jeśli `propagateActivity` = `true`, Proces Akcji klienta i usługi mają ten sam identyfikator działania.  
  
## <a name="synchronous-requestreply-with-errors"></a>Synchroniczne żądanie/nietypizowana odpowiedź z błędami  
 Jedyną różnicą w poprzednim scenariuszu jest to, że komunikatu błędu SOAP są zwracane w postaci komunikatu odpowiedzi. Jeśli `propagateActivity` = `true`, Identyfikator działania komunikat żądania zostanie dodany do komunikatu błędu SOAP.  
  
## <a name="synchronous-one-way-without-errors"></a>Synchroniczne jednokierunkowe bez błędów  
 Jedyna różnica z pierwszego scenariusza polega na tym, że żaden komunikat nie jest zwracana do serwera. Oparte na protokole HTTP protokołów stan (nieprawidłowy lub błędu) nadal jest zwracana do klienta. Jest to spowodowane HTTP jest jedynym protokołem z semantyką odpowiedź na żądanie, należącego do stosu protokołu WCF. Ponieważ przetwarzanie TCP jest ukryty dla usługi WCF, potwierdzenie nie są wysyłane do klienta.  
  
## <a name="synchronous-one-way-with-errors"></a>Synchroniczne jednokierunkowe z Błędami  
 Jeśli wystąpi błąd podczas przetwarzania komunikatu (Q lub nowszych), powiadomienia nie jest zwracana do klienta. Jest to taka sama jak w scenariuszu "One-Way bez błędów synchronicznych". Nie należy używać jednokierunkowe scenariusz, jeśli chcesz otrzymywać komunikat o błędzie.  
  
## <a name="duplex"></a>Dupleks  
 Różnica w poprzednich scenariuszach polega na tym, że klient działa jako usługa, w którym tworzy ReceiveBytes ProcessMessage działalności i, podobnie jak scenariusze asynchroniczne.
