---
title: Śledzenie danych analitycznych programu WCF
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: 3ed9c5f08e89d978f8290dcda5ab1ecfd8b9c56c
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094829"
---
# <a name="wcf-analytic-tracing"></a>Śledzenie danych analitycznych programu WCF
Ten przykład pokazuje, jak dodać własne zdarzenia śledzenia do strumienia śladów analitycznych, które Windows Communication Foundation (WCF) zapisu w usłudze ETW w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Śledzenie analityczne ma na celu ułatwienie wglądu w swoje usługi bez konieczności ponoszenia dużej wydajności. Ten przykład pokazuje, jak używać interfejsów API <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> do zapisywania zdarzeń zintegrowanych z usługami WCF.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> interfejsów API, zobacz <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>.  
  
 Aby dowiedzieć się więcej na temat śledzenia zdarzeń w systemie Windows, zobacz [ulepszanie debugowania i dostrajania wydajności za pomocą funkcji ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw).  
  
## <a name="disposing-eventprovider"></a>EventProvider usuwania  
 Ten przykład używa klasy <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> implementującej <xref:System.IDisposable?displayProperty=nameWithType>. Podczas wdrażania śledzenia dla usługi WCF prawdopodobnie można używać zasobów <xref:System.Diagnostics.Eventing.EventProvider>przez okres istnienia usługi. Z tego powodu i dla czytelności ten przykład nigdy nie usuwa opakowanej <xref:System.Diagnostics.Eventing.EventProvider>. Jeśli z jakiegoś powodu usługa ma inne wymagania dotyczące śledzenia i musisz usunąć ten zasób, należy zmodyfikować ten przykład zgodnie z najlepszymi rozwiązaniami dotyczącymi usuwania niezarządzanych zasobów. Aby uzyskać więcej informacji o usuwaniu niezarządzanych zasobów, zobacz [implementowanie metody Dispose](https://docs.microsoft.com/dotnet/standard/garbage-collection/implementing-dispose).  
  
## <a name="self-hosting-vs-web-hosting"></a>Samodzielne hosting a hosting w sieci Web  
 W przypadku usług hostowanych w sieci Web dane śledzenia analityczne programu WCF zawierają pole o nazwie "HostReference", które służy do identyfikowania usługi emitującej dane śledzenia. Rozszerzone ślady użytkownika mogą uczestniczyć w tym modelu, a w tym przykładzie przedstawiono najlepsze rozwiązania w zakresie tego działania. Format odwołania do hosta sieci Web, gdy potoku "&#124;" rzeczywiście występuje w ciągu wynikiem może być jedną z następujących wartości:  
  
- Jeśli aplikacja nie znajduje się w katalogu głównym.  
  
     \<sitename >\<ApplicationVirtualPath >&#124;\<ServiceVirtualPath >&#124;\<ServiceName >  
  
- Jeśli aplikacja znajduje się w katalogu głównym.  
  
     \<sitename >&#124;\<ServiceVirtualPath >&#124;\<ServiceName >  
  
 W przypadku usług samodzielnych dane śledzenia analityczne WCF nie wypełniają pola "HostReference". Klasa `WCFUserEventProvider` w tym przykładzie działa spójnie, gdy jest używana przez usługę samodzielną.  
  
## <a name="custom-event-details"></a>Szczegóły zdarzenia niestandardowego  
 Manifest dostawcy zdarzeń ETW WCF definiuje trzy zdarzenia, które są przeznaczone do emitowania przez autorów usług WCF z poziomu kodu usługi. W poniższej tabeli przedstawiono podział trzech zdarzeń.  
  
|Wydarzenie|Opis|Identyfikator zdarzenia|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|Emituj to zdarzenie, gdy coś uwagi wystąpi w usłudze, która nie jest problemem. Na przykład można wyemitować zdarzenie po pomyślnym wykonaniu wywołania do bazy danych.|301|  
|UserDefinedWarningOccurred|Emituj to zdarzenie, gdy wystąpi problem, który może spowodować wystąpienie błędu w przyszłości. Można na przykład wyemitować zdarzenie ostrzeżenia, gdy wywołanie do bazy danych zakończy się niepowodzeniem, ale było możliwe odzyskanie ich przez powracanie do nadmiarowego magazynu danych.|302|  
|UserDefinedErrorOccurred|Emituj to zdarzenie, gdy usługa nie będzie działać zgodnie z oczekiwaniami. Można na przykład wyemitować zdarzenie, jeśli wywołanie do bazy danych zakończy się niepowodzeniem i nie można było pobrać danych z innych lokalizacji.|303|  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1. Za pomocą programu Visual Studio 2012 Otwórz plik rozwiązania WCFAnalyticTracingExtensibility. sln.  
  
2. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3. Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
     W przeglądarce sieci Web kliknij pozycję **Kalkulator. svc**. Identyfikator URI dokumentu WSDL dla usługi powinien pojawić się w przeglądarce. Skopiuj ten identyfikator URI.  
  
4. Uruchom klienta testowego WCF (WcfTestClient. exe).  
  
     Klient testowy WCF (WcfTestClient. exe) znajduje się w `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`. Domyślny katalog instalacji programu Visual Studio 2012 jest `C:\Program Files\Microsoft Visual Studio 10.0`.  
  
5. W ramach klienta testowego WCF Dodaj usługę, wybierając pozycję **plik**, a następnie **Dodaj usługę**.  
  
     Dodaj adres punktu końcowego w polu wejściowym.  
  
6. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
     Usługa ICalculator jest dodawana w lewym okienku w obszarze **Moje projekty usług**.  
  
7. Otwórz aplikację Podgląd zdarzeń.  
  
     Przed wywołaniem usługi Uruchom Podgląd zdarzeń i upewnij się, że dziennik zdarzeń nasłuchuje zdarzeń śledzenia emitowanych z usługi WCF.  
  
8. Z menu **Start** wybierz pozycję **Narzędzia administracyjne**, a następnie **Podgląd zdarzeń**. Włącz dzienniki **analityczne** i **debugowania** .  
  
9. W widoku drzewa w Podgląd zdarzeń przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy pozycję **serwer aplikacji — aplikacje**, wybierz polecenie **Widok**, a następnie **Pokaż dzienniki analityczne i debugowania**.  
  
     Upewnij się, że jest zaznaczona opcja **Pokaż dzienniki analityczne i debugowania** . Włącz dziennik **analityczny** .  
  
     W widoku drzewa w Podgląd zdarzeń przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **serwer aplikacji-aplikacje**, a następnie wybierz pozycję **analityczne**. Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz pozycję **Włącz dziennik**.  
  
10. Przetestuj usługę przy użyciu klienta testowego WCF.  
  
    1. W kliencie testowym WCF kliknij dwukrotnie pozycję **Dodaj ()** w węźle usługi ICalculator.  
  
         Metoda **Add ()** zostanie wyświetlona w okienku po prawej stronie z dwoma parametrami.  
  
    2. Wpisz wartość 2 jako pierwszy parametr i 3 dla drugiego parametru.  
  
    3. Kliknij pozycję **Wywołaj** , aby wywołać metodę.  
  
11. Przejdź do okna **Podgląd zdarzeń** , które zostało już otwarte. Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **serwer aplikacji — aplikacje**.  
  
12. Kliknij prawym przyciskiem myszy węzeł **analityczny** i wybierz polecenie **Odśwież**.  
  
     Zdarzenia są wyświetlane w okienku po prawej stronie.  
  
13. Znajdź zdarzenie o IDENTYFIKATORze 303 i kliknij je dwukrotnie, aby otworzyć i sprawdzić jego zawartość.  
  
     To zdarzenie zostało wyemitowane przez `Add()` metodę usługi ICalculator i ma ładunek równe "2 + 3 = 5".  
  
#### <a name="to-clean-up-optional"></a>Aby oczyścić (opcjonalnie)  
  
1. Otwórz **Podgląd zdarzeń**.  
  
2. Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **aplikacje aplikacji**. Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz polecenie **Wyłącz dziennik**.  
  
3. Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacja-serwer-aplikacje**, a następnie wybierz pozycję **analityczne**. Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz pozycję **Wyczyść dziennik**.  
  
4. Kliknij przycisk **Wyczyść** , aby wyczyścić zdarzenia.  
  
## <a name="known-issue"></a>Znany problem  
 Istnieje znany problem w **Podgląd zdarzeń** , w którym może nie można zdekodować zdarzeń ETW. Może zostać wyświetlony komunikat o błędzie: "Opis identyfikatora zdarzenia \<identyfikator > ze źródła Microsoft-Windows-Application Server — nie można odnaleźć aplikacji. Składnik, który wywołuje to zdarzenie, nie jest zainstalowany na komputerze lokalnym lub instalacja jest uszkodzona. Można zainstalować lub naprawić składnik na komputerze lokalnym ". Jeśli ten błąd wystąpi, wybierz pozycję **Odśwież** z menu **Akcje** . Zdarzenie powinno zostać następnie odpowiednio zdekodowane.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>Zobacz też

- [Przykłady monitorowania oprogramowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
