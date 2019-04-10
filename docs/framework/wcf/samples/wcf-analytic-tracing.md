---
title: Śledzenie danych analitycznych programu WCF
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: 3c9f878a22c928daa9c7dbc142efb3958b1657c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229176"
---
# <a name="wcf-analytic-tracing"></a>Śledzenie danych analitycznych programu WCF
W tym przykładzie przedstawiono sposób dodawania własnych zdarzeń śledzenia w strumieniu analityczne śladów, które zapisuje ETW w Windows Communication Foundation (WCF) [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Śledzenie analityczne są przeznaczone do ułatwiają Uzyskaj wgląd w swoje usługi bez konieczności płacenia spadek wysokiej wydajności. Ten przykład ilustruje sposób używania <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> interfejsy API w celu zapisu zdarzenia, które integrują się z usługi WCF.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> interfejsów API, zobacz <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>.  
  
 Aby dowiedzieć się więcej na temat śledzenia zdarzeń w Windows, zobacz [poprawić debugowania i dostrajania wydajności za pomocą funkcji ETW](https://go.microsoft.com/fwlink/?LinkId=166488).  
  
## <a name="disposing-eventprovider"></a>Usuwanie EventProvider  
 W tym przykładzie użyto <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> klasy, która implementuje <xref:System.IDisposable?displayProperty=nameWithType>. Podczas implementowania śledzenia dla usługi WCF, jest prawdopodobne, że możesz korzystać z <xref:System.Diagnostics.Eventing.EventProvider>firmy zasoby dotyczące okresu istnienia usługi. Z tego powodu i czytelności, w tym przykładzie nigdy nie usuwa opakowany <xref:System.Diagnostics.Eventing.EventProvider>. Jeśli zaistnieje usługa ma różne wymagania dotyczące śledzenia i użytkownik musi dysponować tego zasobu, a następnie należy zmodyfikować w tym przykładzie, zgodnie z najlepszymi rozwiązaniami do usuwania niezarządzanych zasobów. Aby uzyskać więcej informacji dotyczących usuwania niezarządzanych zasobów, zobacz [Implementing a Dispose Method](https://go.microsoft.com/fwlink/?LinkId=166436).  
  
## <a name="self-hosting-vs-web-hosting"></a>Hostingu samodzielnego programu vs. Hosting sieci Web  
 W przypadku usług hostowanych w sieci Web śledzenia analitycznego usługi WCF w zapewniają polem o nazwie "HostReference", który jest używany do identyfikowania usługi, która jest emitowanie danych śledzenia. Ślady rozszerzonego użytkownika mogą uczestniczyć w tym modelu, a w tym przykładzie przedstawiono najlepsze rozwiązania, aby to zrobić. Format hosta sieci Web odwołać, kiedy potoku "&#124;" znaków nie są wyświetlane w wynikowym ciągu może być jednym z następujących czynności:  
  
-   Jeśli aplikacja nie znajduje się w katalogu głównym.  
  
     \<SiteName>\<ApplicationVirtualPath>&#124;\<ServiceVirtualPath>&#124;\<ServiceName>  
  
-   Jeśli aplikacja znajduje się w katalogu głównym.  
  
     \<SiteName>&#124;\<ServiceVirtualPath>&#124;\<ServiceName>  
  
 Samodzielnie hostowany usług ślady analitycznych programu WCF na nie wypełnić pole "HostReference". `WCFUserEventProvider` Klasy, w tym przykładzie działa spójne, gdy jest używane przez usługę samodzielnie hostowanej.  
  
## <a name="custom-event-details"></a>Szczegóły zdarzenia niestandardowego  
 Manifest dostawcy zdarzeń funkcji ETW firmy WCF definiuje trzy zdarzenia, które mają być emitowane przez autorów usługi WCF z kodem usługi. W poniższej tabeli przedstawiono podział trzy zdarzenia.  
  
|Zdarzenie|Opis|Identyfikator zdarzenia|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|Emituj tego zdarzenia, kiedy coś Uwaga odbywa się w Twojej usługi, która nie jest problemem. Na przykład może emitować zdarzenia po pomyślnym nawiązywania połączenia z bazą danych.|301|  
|UserDefinedWarningOccurred|Emituj to zdarzenie, gdy wystąpi problem, który może spowodować awarię w przyszłości. Na przykład może emitować zdarzenia ostrzeżenia, gdy połączenie z bazą danych nie powiedzie się, ale udało Ci się odzyskać, nastąpi powrót do magazynu nadmiarowego danych.|302|  
|UserDefinedErrorOccurred|Emituj tego zdarzenia, kiedy usługi nie powiedzie się działać zgodnie z oczekiwaniami. Na przykład wyemituj zdarzenie, jeśli połączenie z bazą danych nie powiedzie się i nie można pobrać danych z innych miejscach.|303|  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą programu Visual Studio 2012, otwórz plik rozwiązania WCFAnalyticTracingExtensibility.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
     W przeglądarce internetowej kliknij **Calculator.svc**. Identyfikator URI dokumentu WSDL usługi powinna zostać wyświetlona w przeglądarce. Skopiuj ten identyfikator URI.  
  
4.  Uruchom klienta testowego WCF (WcfTestClient.exe).  
  
     Testowy klient WCF (WcfTestClient.exe) znajduje się w `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`. Katalog instalacji programu Visual Studio 2012 domyślny jest `C:\Program Files\Microsoft Visual Studio 10.0`.  
  
5.  W kliencie testowym WCF, należy dodać usługę, wybierając **pliku**, a następnie **Dodaj usługę**.  
  
     W polu wejściowym, należy dodać adres punktu końcowego.  
  
6.  Kliknij przycisk **OK** aby zamknąć okno dialogowe.  
  
     Usługa ICalculator zostanie dodany do okienka po lewej stronie w obszarze **Moje projekty usług**.  
  
7.  Otwórz aplikację Podgląd zdarzeń.  
  
     Przed wywołaniem usługi, Uruchom Podgląd zdarzeń i upewnij się, że w dzienniku zdarzeń nasłuchuje śledzenia zdarzeń wysyłanego z usługi WCF.  
  
8.  Z **Start** menu, wybierz opcję **narzędzia administracyjne**, a następnie **Podgląd zdarzeń**. Włącz **analityczne** i **debugowania** dzienniki.  
  
9. W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy **aplikacje serwera aplikacji**, wybierz opcję **widoku**, a następnie **Pokaż analityczne i debugowania dzienniki**.  
  
     Upewnij się, że **Pokaż analityczne i debugowania dzienniki** opcja jest zaznaczona. Włącz **analityczne** dziennika.  
  
     W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera aplikacji**, a następnie **analityczne**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**.  
  
10. Przetestuj usługę za pomocą klienta testowego WCF.  
  
    1.  W kliencie testowym WCF, kliknij dwukrotnie **Add()** węźle ICalculator usługi.  
  
         **Add()** metoda pojawia się w okienku po prawej stronie, z dwoma parametrami.  
  
    2.  Wpisz 2 jako pierwszy parametr i 3 dla drugiego parametru.  
  
    3.  Kliknij przycisk **Invoke** było wywołanie metody.  
  
11. Przejdź do **Podgląd zdarzeń** okna, w którym jest już otwarte. Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji Aplikacje serwera**.  
  
12. Kliknij prawym przyciskiem myszy **analityczne** a następnie wybierz węzeł **Odśwież**.  
  
     Zdarzenia są wyświetlane w okienku po prawej stronie.  
  
13. Znajdź zdarzenie o identyfikatorze 303 i go dwukrotnie, aby otworzyć go i sprawdź jego zawartość.  
  
     To zdarzenie zostały wyemitowane przez `Add()` metody usługi ICalculator i ma ładunek równa "2 + 3 = 5".  
  
#### <a name="to-clean-up-optional"></a>Aby wyczyścić (opcjonalnie)  
  
1.  Otwórz **Podgląd zdarzeń**.  
  
2.  Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie  **Aplikacje serwera**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **wyłączanie dziennika**.  
  
3.  Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera**, a następnie **analityczne**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Wyczyść dziennik**.  
  
4.  Kliknij przycisk **wyczyść** można wyczyścić zdarzenia.  
  
## <a name="known-issue"></a>Znany problem  
 Jest to znany problem w **Podgląd zdarzeń** go mogą spowodować awarię zdekodować zdarzenia ETW. Może zostać wyświetlony komunikat o błędzie informujący, że: "Opisu Identyfikatora zdarzenia \<id > ze źródła, nie można odnaleźć aplikacji serwera firmy Microsoft-Windows-aplikacji. Składnik, który wywołuje to zdarzenie nie jest zainstalowany na komputerze lokalnym albo instalacja jest uszkodzona. Można zainstalować lub naprawić składnik na komputerze lokalnym." Jeśli wystąpi ten błąd, wybierz **Odśwież** z **akcje** menu. Następnie należy się poprawnie dekodowane zdarzenia.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady monitorowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
