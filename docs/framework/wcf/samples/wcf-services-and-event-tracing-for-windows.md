---
title: Usługi i śledzenie zdarzeń programu WCF dla systemu Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: ea917ee87b598fc3ad01df70d9aedfadfd1396a4
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>Usługi i śledzenie zdarzeń programu WCF dla systemu Windows
W tym przykładzie przedstawiono sposób użycia śledzenie analityczne w systemie Windows Communication Foundation (WCF) do wysyłania zdarzeń w zdarzenia śledzenia zdarzeń systemu Windows (ETW). Śledzenie analityczne są zdarzenia emitowane na klucz wskazuje na stosie WCF, umożliwiających rozwiązywanie problemów z usług WCF w środowisku produkcyjnym.  
  
 Śledzenia analitycznego w usługach WCF jest śledzenie, które mogą być włączone w środowisku produkcyjnym z minimalnym wpływem na wydajność. Te operacje śledzenia są emitowane jako zdarzenia do sesji ETW.  
  
 Ten przykład zawiera podstawowe usługi WCF, w której zdarzenia są emitowane przez usługę w dzienniku zdarzeń, które można wyświetlić za pomocą Podglądu zdarzeń. Istnieje również możliwość rozpocząć sesję ETW dedykowanych nasłuchuje zdarzeń z usługi WCF. Przykład obejmuje skrypt służący do tworzenia dedykowanych sesji funkcji ETW, która zapisuje zdarzenia w pliku binarnego, który może zostać odczytany za pomocą Podglądu zdarzeń.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania EtwAnalyticTraceSample.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
     W przeglądarce sieci Web, kliknij przycisk **Calculator.svc**. Identyfikator URI dokumentu WSDL dla usługi powinien zostać wyświetlony w przeglądarce. Skopiuj ten identyfikator URI.  
  
     Domyślnie usługa rozpoczyna nasłuchiwanie na porcie 1378 żądań (http://localhost:1378/Calculator.svc).  
  
4.  Uruchomić klienta testowego WCF (WcfTestClient.exe).  
  
     Klienta testowego WCF (WcfTestClient.exe) znajduje się w \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] zainstalować Dir > \Common7\IDE\ WcfTestClient.exe (domyślny [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] dir instalacji to C:\Program Files\Microsoft Visual Studio 10.0).  
  
5.  W kliencie testowym WCF, Dodaj usługę, wybierając **pliku**, a następnie **Dodaj usługę**.  
  
     Dodaj adres punktu końcowego w odpowiednim polu. Wartość domyślna to http://localhost:1378/Calculator.svc.  
  
6.  Otwórz aplikację Podgląd zdarzeń.  
  
     Przed wywołaniem usługi, należy uruchomić Podgląd zdarzeń i upewnij się, czy dziennik zdarzeń nasłuchuje śledzenia zdarzeń wysyłanego z usługi WCF.  
  
7.  Z **Start** menu, wybierz opcję **narzędzia administracyjne**, a następnie **Podgląd zdarzeń**.  Włącz **analityczne** i **debugowania** dzienniki.  
  
8.  W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Aplikacji serwerowych aplikacji**. Kliknij prawym przyciskiem myszy **aplikacji serwerowych aplikacji**, wybierz pozycję **widoku**, a następnie **dzienniki Pokaż analityczne i debugowania**.  
  
     Upewnij się, że **dzienniki Pokaż analityczne i debugowania** zaznaczenia pola wyboru.  
  
9. Włącz **analityczne** dziennika.  
  
     W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Aplikacji serwerowych aplikacji**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**.  
  
#### <a name="to-test-the-service"></a>Aby przetestować usługę  
  
1.  Przełącza z powrotem do klienta testowego WCF, a następnie kliknij dwukrotnie ikonę `Divide` i Zachowaj wartości domyślne, które określają denominator 0.  
  
     Jeżeli dzielnik wynosi 0, usługa zgłasza błąd.  
  
2.  Sprawdź zdarzenia wysyłanego z usługi.  
  
     Wrócić do podglądu zdarzeń, a następnie przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Aplikacji serwerowych aplikacji**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Odśwież**.  
  
     Zdarzenia śledzenia analitycznego WCF są wyświetlane w Podglądzie zdarzeń. Zauważ, że ponieważ błąd został zgłoszony przez usługę zdarzenie śledzenia błędu jest wyświetlana w zdarzeniu podglądu.  
  
3.  Powtórz kroki 1 i 2, ale z prawidłowe wartości wejściowe. Wartość `N2` parametr może być dowolna liczba innych niż 0.  
  
     Odśwież analityczne kanału, aby wyświetlić usługi WCF zdarzeń nie ma zdarzenia błędów.  
  
 W przykładzie pokazano zdarzenia śledzenia analitycznego wyemitowanego z usługą WCF.  
  
#### <a name="to-cleanup-optional"></a>Do oczyszczania (opcjonalnie)  
  
1.  Otwórz Podgląd zdarzeń.  
  
2.  Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie  **Aplikacje serwera**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **wyłączyć dziennika**.  
  
3.  Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie  **Aplikacje serwera**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Wyczyść dziennik**.  
  
4.  Wybierz **wyczyść** opcję, aby wyczyścić zdarzenia.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
