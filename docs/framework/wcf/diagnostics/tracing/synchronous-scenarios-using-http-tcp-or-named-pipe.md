---
title: Scenariusze synchroniczne z zastosowaniem protokołu HTTP lub TCP albo potoku nazwanego
ms.date: 03/30/2017
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
ms.openlocfilehash: 11a5d8f43d12d35728c65c7a60ad8a4fa2fc1b3a
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a>Scenariusze synchroniczne z zastosowaniem protokołu HTTP lub TCP albo potoku nazwanego
W tym temacie opisano działania i transferów w scenariuszach różnych synchroniczne żądania/odpowiedzi, za pomocą klienta jednowątkowe, przy użyciu protokołu HTTP, TCP lub nazwany potok. Zobacz [scenariusze asynchroniczne z zastosowaniem protokołu HTTP lub TCP albo potoku nazwanego](../../../../../docs/framework/wcf/diagnostics/tracing/asynchronous-scenarios-using-http-tcp-or-named-pipe.md) uzyskać więcej informacji dotyczących żądań wielowątkowych.  
  
## <a name="synchronous-requestreply-without-errors"></a>Synchroniczne żądania/odpowiedzi bez błędów  
 W tej sekcji opisano działania i transferu dla scenariusza prawidłowy synchroniczne żądania/odpowiedzi z pojedynczym wątku klienta.  
  
### <a name="client"></a>Klient  
  
#### <a name="establishing-communication-with-service-endpoint"></a>Nawiązywania połączenia z punktem końcowym usługi  
 Klient jest tworzony i otworzyć. Dla każdego z tych kroków otoczenia działania (A) jest przekazywane "skonstruować" (B) oraz klienta "Otwórz" (C) działania odpowiednio. Dla każdego działania przesyłane do otoczenia działania jest wstrzymana, do momentu przekazania, oznacza to, aż wykonywany jest kod ServiceModel.  
  
#### <a name="making-a-request-to-service-endpoint"></a>Przesyłania do punktu końcowego usługi  
 Działanie otoczenia jest przekazywany do działania "ProcessAction" (D). W ramach tego działania jest wysyłany komunikat żądania, a odebraniu komunikatu odpowiedzi. Działanie kończy się, gdy formant zwraca do kodu użytkownika. Ponieważ jest to żądanie synchroniczne, działanie otoczenia zawiesza dopóki zwraca formantu.  
  
#### <a name="closing-communication-with-service-endpoint"></a>Zamykanie komunikacji z punktem końcowym usługi  
 Działanie Zamknij klienta (I) jest tworzony z otaczającym działania. Jest to identyczne nowych i otwarte.  
  
### <a name="server"></a>Serwer  
  
#### <a name="setting-up-a-service-host"></a>Konfigurowanie hosta usługi  
 ServiceHost nowych i otwarte działania (N i O) są tworzone z otaczającym działania (M).  
  
 Działanie odbiornika (P) jest tworzony z otwierania elementu ServiceHost dla każdego odbiornika. Działanie odbiornika oczekuje na otrzymywanie i przetwarzania danych.  
  
#### <a name="receiving-data-on-the-wire"></a>Odbieranie danych w sieci  
 Po odebraniu danych w sieci, jeśli nie istnieje już (Q), aby przetworzyć odebranych danych działania "ReceiveBytes" zostanie utworzony. To działanie można ponownie wiele komunikatów w ramach połączenia lub kolejki.  
  
 Działanie ReceiveBytes uruchamia działanie ProcessMessage (R), jeśli zawiera on za mało danych do utworzenia komunikatu akcji SOAP.  
  
 W działaniu R nagłówki komunikatów są przetwarzane i jest weryfikowany nagłówka identyfikatora. Jeśli ten nagłówek jest obecna, identyfikator działania ustawiono działania ProcessAction; w przeciwnym razie jest tworzony nowy identyfikator.  
  
 Działanie ProcessAction (S) jest tworzony i ich przesyłania, gdy wywołanie jest przetwarzany. To działanie kończy się po zakończeniu przetwarzania związanych z komunikatu przychodzącego tym wykonywanie kodu użytkownika (T) i wysyła komunikat odpowiedzi, jeśli ma to zastosowanie.  
  
#### <a name="closing-a-service-host"></a>Zamykanie hosta usługi  
 Zamknij działania ServiceHost (Z) jest tworzony z otaczającym działania.  
  
 ![Scenariusze synchroniczne z zastosowaniem protokołu HTTP&#47;TCP&#47; potoków nazwanych](../../../../../docs/framework/wcf/diagnostics/tracing/media/sync.gif "synchronizacji")  
  
 W \<A: name >, `A` to symbol skrótu, który opisuje działania poprzedniego tekstu i w tabeli 3. `Name` jest skróconą nazwę działania.  
  
 Jeśli `propagateActivity` = `true`, proces akcji na kliencie i usługi mają ten sam identyfikator działania.  
  
## <a name="synchronous-requestreply-with-errors"></a>Synchroniczne żądania/odpowiedzi z błędami  
 Jedyną różnicą z poprzednim scenariuszu jest, że komunikat o błędzie SOAP są zwracane jako komunikatu odpowiedzi. Jeśli `propagateActivity` = `true`, identyfikator działania komunikatu żądania jest dodawany do komunikatu błędu SOAP.  
  
## <a name="synchronous-one-way-without-errors"></a>Synchroniczne jednokierunkowe bez błędów  
 Jedyna różnica z pierwszego scenariusza polega na tym, że komunikat nie jest zwracana do serwera. Dla protokołów opartych na protokole HTTP, stan (nieprawidłowa lub błąd) nadal jest zwracana do klienta. Jest to spowodowane HTTP jest jedynym protokołem z semantyki żądanie odpowiedź, który jest częścią stosu protokołu WCF. Ponieważ przetwarzanie TCP jest ukryta WCF, bez potwierdzenia są wysyłane do klienta.  
  
## <a name="synchronous-one-way-with-errors"></a>Synchroniczne jednokierunkowe z błędami  
 Jeśli wystąpi błąd podczas przetwarzania komunikatu (Q lub nowszych), do klienta zwracany jest prezentowane żadne powiadomienie. To jest taka sama jak w scenariuszu "Synchronicznej One-Way bez błędów". Nie należy używać jednokierunkowe scenariusz, jeśli chcesz otrzymywać komunikat o błędzie.  
  
## <a name="duplex"></a>Dupleks  
 Różnica w stosunku do poprzednich scenariuszach jest, że klient działa jako usługa, w którym tworzy ReceiveBytes i ProcessMessage działania, podobnie jak scenariusze asynchroniczne.
