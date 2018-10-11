---
title: Usługi i śledzenie zdarzeń programu WCF dla systemu Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: 6684f6415fa6ee82a59fc9b54911b5c65d6dadb2
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086586"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>Usługi i śledzenie zdarzeń programu WCF dla systemu Windows
Ten przykład pokazuje sposób użycia śledzenia danych analitycznych w Windows Communication Foundation (WCF) aby emitować zdarzenia w śledzenie zdarzeń dla Windows (ETW). Śledzenie analityczne są zdarzenia emitowane w kluczowych punktach w stosie usługi WCF, które umożliwiają rozwiązywanie problemów z usług WCF w środowisku produkcyjnym.

 Śledzenie jest śledzenia analitycznego w usługach WCF, która może zostać włączona w środowisku produkcyjnym przy minimalnym wpływie na wydajność. Ślady te są emitowane jako zdarzenia do sesji funkcji ETW.

 W tym przykładzie zawiera podstawowe usługi WCF, w której zdarzenia są emitowane z usługi w dzienniku zdarzeń, które można przeglądać za pomocą Podglądu zdarzeń. Jest również możliwe do uruchomienia w dedykowanym sesji ETW, który nasłuchuje zdarzeń z usługi WCF. Przykład obejmuje skrypt służący do tworzenia dedykowanych sesja funkcji ETW, który przechowuje zdarzenia w pliku binarnym, który może zostać odczytany za pomocą Podglądu zdarzeń.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1.  Za pomocą programu Visual Studio 2012, otwórz plik rozwiązania EtwAnalyticTraceSample.sln.

2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.

     W przeglądarce internetowej kliknij **Calculator.svc**. Identyfikator URI dokumentu WSDL usługi powinna zostać wyświetlona w przeglądarce. Skopiuj ten identyfikator URI.

     Domyślnie usługa rozpoczyna nasłuchiwanie żądań na porcie 1378 (http://localhost:1378/Calculator.svc).

4.  Uruchom klienta testowego WCF (WcfTestClient.exe).

     Testowy klient WCF (WcfTestClient.exe) znajduje się w \<Visual Studio 2012 zainstalować Dir > \Common7\IDE\ WcfTestClient.exe (katalog domyślny program Visual Studio 2012 to C:\Program Files\Microsoft Visual Studio 10.0).

5.  W kliencie testowym WCF, należy dodać usługę, wybierając **pliku**, a następnie **Dodaj usługę**.

     W polu wejściowym, należy dodać adres punktu końcowego. Wartość domyślna to `http://localhost:1378/Calculator.svc`.

6.  Otwórz aplikację Podgląd zdarzeń.

     Przed wywołaniem usługi, Uruchom Podgląd zdarzeń i upewnij się, że w dzienniku zdarzeń nasłuchuje śledzenia zdarzeń wysyłanego z usługi WCF.

7.  Z **Start** menu, wybierz opcję **narzędzia administracyjne**, a następnie **Podgląd zdarzeń**.  Włącz **analityczne** i **debugowania** dzienniki.

8.  W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy **aplikacje serwera aplikacji**, wybierz opcję **widoku**, a następnie **Pokaż analityczne i debugowania dzienniki**.

     Upewnij się, że **Pokaż analityczne i debugowania dzienniki** opcja jest zaznaczona.

9. Włącz **analityczne** dziennika.

     W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**.

#### <a name="to-test-the-service"></a>Aby przetestować usługę

1.  Przejdź z powrotem do klienta testowego WCF, a następnie kliknij dwukrotnie ikonę `Divide` i Zachowaj wartości domyślne, które określają mianownik 0.

     Jeżeli mianownik wynosi 0, usługa zgłasza błąd.

2.  Sprawdź zdarzenia wysyłanego z usługi.

     Przejdź z powrotem do programu Podgląd zdarzeń i przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Odśwież**.

     Zdarzenia śledzenia analitycznego WCF są wyświetlane w Podglądzie zdarzeń. Zauważ, że ponieważ błąd został zgłoszony przez usługę, którą zdarzenie śledzenia błędu jest wyświetlana w zdarzeniu podglądu.

3.  Powtórz kroki 1 i 2, ale z prawidłowych danych wejściowych. Wartość `N2` parametr może być dowolna liczba innych niż 0.

     Odśwież kanał analityczne, aby wyświetlić WCF zdarzeń nie ma żadnych zdarzeń błędu.

 W przykładzie pokazano zdarzenia śledzenia analitycznego wysyłanego z usługi WCF.

#### <a name="to-cleanup-optional"></a>Aby oczyścić (opcjonalnie)

1.  Otwórz Podgląd zdarzeń.

2.  Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie  **Aplikacje serwera**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **wyłączanie dziennika**.

3.  Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie  **Aplikacje serwera**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Wyczyść dziennik**.

4.  Wybierz **wyczyść** możliwość wyczyszczenia zdarzeń.

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
