---
title: Scenariusze synchroniczne z zastosowaniem protokołu HTTP lub TCP albo potoku nazwanego
ms.date: 03/30/2017
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
ms.openlocfilehash: 662067fc5564c9421ce24b28b291d06690b129ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589187"
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a>Scenariusze synchroniczne z zastosowaniem protokołu HTTP lub TCP albo potoku nazwanego
W tym temacie opisano działania i transfery dla różnych scenariuszy żądań synchronicznych/odpowiedzi z klientem jednowątkowym przy użyciu protokołu HTTP, TCP lub potoku nazwanego. Aby uzyskać więcej informacji na temat żądań wielowątkowych, zobacz [scenariusze asynchroniczne przy użyciu protokołu HTTP, TCP lub nazwanego potoku](asynchronous-scenarios-using-http-tcp-or-named-pipe.md) .  
  
## <a name="synchronous-requestreply-without-errors"></a>Synchroniczne żądanie/odpowiedź bez błędów  
 W tej sekcji opisano działania i transfery dla prawidłowego scenariusza synchronicznego żądania/odpowiedzi z klientem jednowątkowym.  
  
### <a name="client"></a>Klient  
  
#### <a name="establishing-communication-with-service-endpoint"></a>Ustanawianie komunikacji z punktem końcowym usługi  
 Klient został skonstruowany i otwarty. Dla każdego z tych kroków działanie otoczenia (A) jest przesyłane odpowiednio do działania "Konstruuj klienta" (B) i "Otwórz klienta" (C). W przypadku każdego przenoszonego działania do programu działanie otoczenia zostaje zawieszone do momentu przetransferowania, czyli do momentu wykonania kodu ServiceModel.  
  
#### <a name="making-a-request-to-service-endpoint"></a>Tworzenie żądania do punktu końcowego usługi  
 Działanie otoczenia jest przenoszone do działania "ProcessAction" (D). W ramach tego działania zostanie wysłany komunikat o żądaniu i zostanie wyświetlony komunikat z odpowiedzią. Działanie zostaje zakończone, gdy sterowanie powraca do kodu użytkownika. Ponieważ jest to żądanie synchroniczne, działanie otoczenia zawiesza się do momentu powracania kontroli.  
  
#### <a name="closing-communication-with-service-endpoint"></a>Zamykanie komunikacji z punktem końcowym usługi  
 Działanie zamknięcia klienta (I) jest tworzone na podstawie działania otoczenia. Ta nazwa jest taka sama jak w przypadku nowych i otwartych.  
  
### <a name="server"></a>Serwer  
  
#### <a name="setting-up-a-service-host"></a>Konfigurowanie hosta usługi  
 Nowe i otwarte działania usługi ServiceHost (N i O) są tworzone na podstawie działania otoczenia (M).  
  
 Działanie odbiornika (P) jest tworzone na podstawie otwierania ServiceHost dla każdego odbiornika. Działanie odbiornika czeka na odebranie i przetworzenie danych.  
  
#### <a name="receiving-data-on-the-wire"></a>Otrzymywanie danych w sieci  
 Gdy dane docierają do sieci, zostanie utworzone działanie "ReceiveBytes", jeśli jeszcze nie istnieje (Q) w celu przetworzenia odebranych danych. To działanie może być ponownie używane dla wielu komunikatów w ramach połączenia lub kolejki.  
  
 Działanie ReceiveBytes uruchamia działanie ProcessMessage (R), jeśli ma wystarczającą ilość danych do utworzenia komunikatu akcji protokołu SOAP.  
  
 W działaniu R nagłówki wiadomości są przetwarzane, a nagłówek activityID zostanie zweryfikowany. Jeśli ten nagłówek jest obecny, identyfikator działania jest ustawiany na działanie ProcessAction. w przeciwnym razie zostanie utworzony nowy identyfikator.  
  
 Działania ProcessAction są tworzone i przekazywane do, gdy wywołanie jest przetwarzane. To działanie kończy się, gdy zostanie wykonane wszystkie przetwarzanie związane z wiadomością przychodzącą, w tym wykonanie kodu użytkownika (T) i wysłanie komunikatu odpowiedzi, jeśli ma to zastosowanie.  
  
#### <a name="closing-a-service-host"></a>Zamykanie hosta usługi  
 Działanie zamknięcia elementu ServiceHost (Z) zostało utworzone na podstawie działania otoczenia.  
  
 ![Diagram przedstawiający scenariusze synchroniczne: HTTP, TCP lub nazwane potoki.](./media/synchronous-scenarios-using-http-tcp-or-named-pipe/synchronous-scenario-http-tcp-named-pipes.gif)  
  
 W \<A: name> programie `A` jest symbolem skrótu opisującym działanie w poprzednim tekście i w tabeli 3. `Name`to Skrócona nazwa działania.  
  
 Jeśli `propagateActivity` = `true` operacja przetwarzania na kliencie i w usłudze ma ten sam identyfikator działania.  
  
## <a name="synchronous-requestreply-with-errors"></a>Synchroniczne żądanie/odpowiedź z błędami  
 Jedyną różnicą w poprzednim scenariuszu jest zwrócenie komunikatu o błędzie protokołu SOAP jako komunikatu odpowiedzi. Jeśli `propagateActivity` = `true` identyfikator działania komunikatu żądania zostanie dodany do komunikatu o błędzie protokołu SOAP.  
  
## <a name="synchronous-one-way-without-errors"></a>Jednokierunkowa synchroniczna bez błędów  
 Jedyną różnicą w pierwszym scenariuszu jest to, że żaden komunikat nie jest zwracany do serwera. W przypadku protokołów opartych na protokole HTTP stan (prawidłowy lub błąd) jest nadal zwracany do klienta. Wynika to z faktu, że protokół HTTP jest jedynym protokołem z semantyką odpowiedzi na żądanie, która jest częścią stosu protokołu WCF. Ponieważ przetwarzanie protokołu TCP jest ukryte w programie WCF, do klienta nie jest wysyłane potwierdzenie.  
  
## <a name="synchronous-one-way-with-errors"></a>Synchroniczna synchronizacja z błędami  
 Jeśli wystąpi błąd podczas przetwarzania komunikatu (Q lub więcej), do klienta nie jest zwracane żadne powiadomienie. Jest to taka sama jak w przypadku scenariusza "synchronicznie jednokierunkowe bez błędów". Nie należy używać jednokierunkowego scenariusza, jeśli chcesz otrzymać komunikat o błędzie.  
  
## <a name="duplex"></a>Dupleks  
 Różnica z poprzednimi scenariuszami polega na tym, że klient działa jako usługa, w której tworzy działania ReceiveBytes i ProcessMessage, podobne do scenariuszy asynchronicznych.
