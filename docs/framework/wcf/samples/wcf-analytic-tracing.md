---
title: Śledzenie danych analitycznych programu WCF
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: 99b28dcc1cfb32f5f6835eadee1bded14375c216
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-analytic-tracing"></a>Śledzenie danych analitycznych programu WCF
W tym przykładzie pokazano, jak dodać własne zdarzenia śledzenia do strumienia śladów analityczne, które zapisuje Windows Communication Foundation (WCF) ETW w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Śledzenie analityczne są przeznaczone do ułatwiają pobrać widoczność do usług bez płatności kar wysokiej wydajności. Ten przykład przedstawia sposób użycia <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> interfejsy API w celu zapisu zdarzenia, które integrują się z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> interfejsów API, zobacz <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>.  
  
 Aby dowiedzieć się więcej na temat śledzenia zdarzeń w systemie Windows, zobacz [poprawy debugowania i dostrajania wydajności za pomocą funkcji ETW](http://go.microsoft.com/fwlink/?LinkId=166488).  
  
## <a name="disposing-eventprovider"></a>Usuwanie EventProvider  
 W przykładzie użyto <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> klasy, która implementuje <xref:System.IDisposable?displayProperty=nameWithType>. Podczas implementowania śledzenia dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, prawdopodobnie można także użyć <xref:System.Diagnostics.Eventing.EventProvider>dla zasobów przez czas ich istnienia usługi. Z tego powodu i czytelności, w tym przykładzie nigdy nie usuwa opakowany <xref:System.Diagnostics.Eventing.EventProvider>. Jeśli zaistnieje usługa ma różne wymagania dotyczące śledzenia i użytkownik musi dysponować tego zasobu, a następnie należy modyfikować tego przykładu zgodnie z najlepszych rozwiązań dotyczących usuwania niezarządzanych zasobów. Aby uzyskać więcej informacji na temat usuwania zasoby niezarządzane, zobacz [implementacja metody Dispose](http://go.microsoft.com/fwlink/?LinkId=166436).  
  
## <a name="self-hosting-vs-web-hosting"></a>Własnym hostingu vs. Usługa hostingu sieci Web  
 W przypadku usług hostowanych w sieci Web analityczne dane śledzenia WCF w Podaj pola o nazwie "HostReference", który jest używany do identyfikowania usługi, która jest wysyłających dane śledzenia. Ślady extensible użytkownika mogą uczestniczyć w tym modelu i w tym przykładzie przedstawiono najlepsze rozwiązania w zakresie w ten sposób. Format hosta sieci Web odwołać, kiedy potoku "&#124;" znak nie są wyświetlane w wynikowym ciąg może być jednym z następujących czynności:  
  
-   Jeśli aplikacja nie jest w katalogu głównym.  
  
     \<Nazwa witryny >\<ApplicationVirtualPath >&#124;\<ServiceVirtualPath >&#124;\<ServiceName >  
  
-   Jeśli w katalogu głównym aplikacji.  
  
     \<Nazwa witryny >&#124;\<ServiceVirtualPath >&#124;\<ServiceName >  
  
 W przypadku usług hostowania samoobsługowego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]firmy analityczne dane śledzenia nie należy wypełniać pola "HostReference". `WCFUserEventProvider` Klasy w tym przykładzie zachowuje się spójnie, gdy jest używana przez siebie usługi.  
  
## <a name="custom-event-details"></a>Szczegóły zdarzenia niestandardowe  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]w manifeście dostawcy zdarzeń ETW definiuje trzy zdarzenia, które mają być wysyłany przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi autorów z kodem usługi. W poniższej tabeli przedstawiono podział trzech zdarzeń.  
  
|Zdarzenie|Opis|Identyfikator zdarzenia|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|Emituj to zdarzenie, gdy coś Uwaga odbywa się w usłudze nie stanowi to problemu. Na przykład może wysyłać zdarzenia po pomyślnym nawiązywania połączenia z bazą danych.|301|  
|UserDefinedWarningOccurred|Emituj to zdarzenie, gdy występuje problem może spowodować błąd w przyszłości. Na przykład może emitować zdarzenie ostrzeżenia, gdy połączenie z bazą danych nie powiedzie się, ale można było odzyskać, nastąpi powrót do magazynu nadmiarowych danych.|302|  
|UserDefinedErrorOccurred|Emituj tego zdarzenia, kiedy usługi nie powiedzie się działać zgodnie z oczekiwaniami. Może na przykład Emituj zdarzenie w przypadku połączenia z bazą danych nie powiedzie się i nie można pobrać danych z innej lokalizacji.|303|  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania WCFAnalyticTracingExtensibility.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
     W przeglądarce sieci Web, kliknij przycisk **Calculator.svc**. Identyfikator URI dokumentu WSDL dla usługi powinien zostać wyświetlony w przeglądarce. Skopiuj ten identyfikator URI.  
  
4.  Uruchom [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta testowego (WcfTestClient.exe).  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Klienta testowego (WcfTestClient.exe) znajduje się w \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] zainstalować Dir > \Common7\IDE\ WcfTestClient.exe (domyślny [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] dir instalacji to C:\Program Files\Microsoft Visual Studio 10.0).  
  
5.  W ramach [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Klient testowy, Dodaj usługę, wybierając **pliku**, a następnie **Dodaj usługę**.  
  
     Dodaj adres punktu końcowego w odpowiednim polu.  
  
6.  Kliknij przycisk **OK** aby zamknąć okno dialogowe.  
  
     Usługa ICalculator został dodany w lewym okienku w obszarze **Moje projekty usług**.  
  
7.  Otwórz aplikację Podgląd zdarzeń.  
  
     Przed wywołaniem usługi, Uruchom Podgląd zdarzeń i upewnij się, nasłuchują dziennika zdarzeń dla zdarzenia śledzenia wyemitowanego z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.  
  
8.  Z **Start** menu, wybierz opcję **narzędzia administracyjne**, a następnie **Podgląd zdarzeń**. Włącz **analityczne** i **debugowania** dzienniki.  
  
9. W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Aplikacji serwerowych aplikacji**. Kliknij prawym przyciskiem myszy **aplikacji serwerowych aplikacji**, wybierz pozycję **widoku**, a następnie **dzienniki Pokaż analityczne i debugowania**.  
  
     Upewnij się, że **dzienniki Pokaż analityczne i debugowania** zaznaczenia pola wyboru. Włącz **analityczne** dziennika.  
  
     W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera aplikacji**, a następnie **analityczne**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**.  
  
10. Przetestuj usługę za pomocą klienta testowego WCF.  
  
    1.  W kliencie testowym WCF, kliknij dwukrotnie **Add()** w węźle usługi ICalculator.  
  
         **Add()** metoda pojawia się w okienku po prawej stronie dwa parametry.  
  
    2.  Wpisz 2 dla pierwszego parametru i 3 dla drugiego parametru.  
  
    3.  Kliknij przycisk **Invoke** można wywołać metody.  
  
11. Przejdź do **Podgląd zdarzeń** okna, który został już otwarty. Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji Aplikacje serwera**.  
  
12. Kliknij prawym przyciskiem myszy **analityczne** a następnie wybierz węzeł **Odśwież**.  
  
     Zdarzenia wyświetlane w okienku po prawej stronie.  
  
13. Znajdź zdarzenie o identyfikatorze 303 i kliknij dwukrotnie, aby otworzyć go i przejrzyj jego zawartość.  
  
     To zdarzenie zostały wyemitowane przez `Add()` metody usługi ICalculator i ma ładunek równa "2 + 3 = 5".  
  
#### <a name="to-clean-up-optional"></a>Aby wyczyścić (opcjonalnie)  
  
1.  Otwórz **Podgląd zdarzeń**.  
  
2.  Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie  **Aplikacje serwera**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **wyłączyć dziennika**.  
  
3.  Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera**, a następnie **analityczne**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Wyczyść dziennik**.  
  
4.  Kliknij przycisk **wyczyść** Wyczyść zdarzenia.  
  
## <a name="known-issue"></a>Znany problem  
 Jest to znany problem w **Podgląd zdarzeń** Jeżeli nie może zdekodować zdarzenia ETW. Zobaczysz komunikat o błędzie z informacją: "opisu Identyfikatora zdarzenia \<id > ze źródła nie można odnaleźć aplikacji serwera firmy Microsoft-Windows-aplikacji. Składnik, który wywołuje to zdarzenie nie jest zainstalowany na komputerze lokalnym albo instalacja jest uszkodzona. Można zainstalować lub naprawić składnik na komputerze lokalnym." Jeśli ten błąd wystąpi, wybierz **Odśwież** z **akcje** menu. Zdarzenie następnie należy prawidłowo zdekodować.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
