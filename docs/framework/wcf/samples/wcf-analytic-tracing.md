---
title: Śledzenie danych analitycznych programu WCF
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: ef636a672d9384e8e3d658f0488cfaadb8d293e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183215"
---
# <a name="wcf-analytic-tracing"></a>Śledzenie danych analitycznych programu WCF
W tym przykładzie pokazano, jak dodać własne zdarzenia śledzenia do strumienia śladów analitycznych, które Program Windows [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]Communication Foundation (WCF) zapisuje do ETW w programie . Ślady analityczne mają na celu ułatwienie wglądu w usługi bez płacenia kary za wysoką wydajność. W tym przykładzie <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> pokazano, jak używać interfejsów API do zapisywania zdarzeń, które integrują się z usługami WCF.  
  
 Aby uzyskać więcej <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> informacji na <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>temat interfejsów API, zobacz .  
  
 Aby dowiedzieć się więcej o śledzeniu zdarzeń w systemie Windows, zobacz [Poprawianie debugowania i dostrajania wydajności za pomocą etw](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw).  
  
## <a name="disposing-eventprovider"></a>Usuwanie EventProvider  
 W tym przykładzie <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> użyto <xref:System.IDisposable?displayProperty=nameWithType>klasy, która implementuje . Podczas implementowania śledzenia dla usługi WCF, jest prawdopodobne, <xref:System.Diagnostics.Eventing.EventProvider>że można użyć zasobów 's przez cały okres istnienia usługi. Z tego powodu i dla czytelności, ta próbka nigdy nie usuwa zawinięte <xref:System.Diagnostics.Eventing.EventProvider>. Jeśli z jakiegoś powodu usługa ma różne wymagania dotyczące śledzenia i należy usunąć ten zasób, należy zmodyfikować ten przykład zgodnie z najlepszymi rozwiązaniami dotyczącymi usuwania zasobów niezarządzanych. Aby uzyskać więcej informacji na temat usuwania zasobów niezarządzanych, zobacz [Implementowanie metody dispose](https://docs.microsoft.com/dotnet/standard/garbage-collection/implementing-dispose).  
  
## <a name="self-hosting-vs-web-hosting"></a>Hosting własny a hosting  
 W przypadku usług hostowanych w sieci Web śledzenia analityczne WCF zapewniają pole o nazwie "HostReference", które jest używane do identyfikowania usługi emitującej ślady. Rozszerzalne ślady użytkownika mogą uczestniczyć w tym modelu i w tym przykładzie przedstawiono najlepsze rozwiązania w tym zakresie. Format odwołania do hosta sieci Web, gdy znak "&#124;" potoku faktycznie pojawia się w wynikowym ciągu może być jedną z następujących czynności:  
  
- Jeśli aplikacja nie znajduje się w katalogu głównym.  
  
     \<Nazwa>\<aplikacji>>&#124;\<ServiceVirtualPath>&#124;\<ServiceName>  
  
- Jeśli aplikacja znajduje się w katalogu głównym.  
  
     \<>&#124;\<ServiceVirtualPath>&#124;\<ServiceName>  
  
 W przypadku usług hostowanych samodzielnie ślady analityczne WCF nie wypełniają pola "HostReference". Klasa `WCFUserEventProvider` w tym przykładzie zachowuje się konsekwentnie, gdy jest używana przez usługę hostowane samodzielnie.  
  
## <a name="custom-event-details"></a>Niestandardowe szczegóły zdarzenia  
 Manifest dostawcy zdarzeń ETW WCF definiuje trzy zdarzenia, które są przeznaczone do emisji przez autorów usług WCF z poziomu kodu usługi. W poniższej tabeli przedstawiono podział trzech zdarzeń.  
  
|Wydarzenie|Opis|Identyfikator zdarzenia|  
|-----------|-----------------|--------------|  
|UżytkownikDefiniowanyInformationEventOccurred|Emituj to zdarzenie, gdy coś uwagi dzieje się w usłudze, która nie jest problemem. Na przykład może emitować zdarzenie po pomyślnym wywołaniu bazy danych.|301|  
|UżytkownikDefiniowanyWarningZanienie|Emituj to zdarzenie, gdy wystąpi problem, który może spowodować błąd w przyszłości. Na przykład może emitować zdarzenie ostrzegawcze, gdy wywołanie bazy danych kończy się niepowodzeniem, ale udało się odzyskać przez powrót do magazynu danych nadmiarowych.|302|  
|UżytkownikDefdefedErrorOccurred|Emituj to zdarzenie, gdy usługa nie działa zgodnie z oczekiwaniami. Na przykład może emitować zdarzenie, jeśli wywołanie bazy danych nie powiedzie się i nie można pobrać danych z innego miejsca.|303|  
  
#### <a name="to-use-this-sample"></a>Aby użyć tej próbki  
  
1. Za pomocą programu Visual Studio 2012, otwórz plik rozwiązania WCFAnalyticTracingExtensibility.sln.  
  
2. Aby utworzyć rozwiązanie, naciśnij klawisze CTRL+SHIFT+B.  
  
3. Aby uruchomić rozwiązanie, naciśnij klawisze CTRL+F5.  
  
     W przeglądarce sieci Web kliknij pozycję **Calculator.svc**. Identyfikator URI dokumentu WSDL dla usługi powinien pojawić się w przeglądarce. Skopiuj ten identyfikator URI.  
  
4. Uruchom klienta testowego WCF (WcfTestClient.exe).  
  
     Klient testowy WCF (WcfTestClient.exe) `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`znajduje się pod adresem . Domyślnym programem dir instalacji programu `C:\Program Files\Microsoft Visual Studio 10.0`Visual Studio 2012 jest .  
  
5. W kliencie testowym WCF dodaj usługę, wybierając **pozycję Plik**, a następnie **Dodaj usługę**.  
  
     Dodaj adres punktu końcowego w polu wprowadzania.  
  
6. Kliknij **przycisk OK,** aby zamknąć okno dialogowe.  
  
     Usługa ICalculator jest dodawana w lewym okienku w obszarze **Moje projekty usługi**.  
  
7. Otwórz aplikację Podgląd zdarzeń.  
  
     Przed wywołaniem usługi uruchom Podgląd zdarzeń i upewnij się, że dziennik zdarzeń nasłuchuje śledzenia zdarzeń emitowanych z usługi WCF.  
  
8. W menu **Start** wybierz polecenie **Narzędzia administracyjne**, a następnie **pozycję Podgląd zdarzeń**. Włącz dzienniki **analityczne** i **debugowania.**  
  
9. W widoku drzewa w Podglądzie zdarzeń przejdź do **pozycji Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Application Server-Applications**. Kliknij prawym przyciskiem myszy **pozycję Serwer aplikacji ,** wybierz polecenie **Widok**, a następnie pozycję **Pokaż dzienniki analityczne i debugowania**.  
  
     Upewnij się, że zaznaczono opcję **Pokaż dzienniki analityczne i debugowania.** Włącz dziennik **analityczny.**  
  
     W widoku drzewa w Podglądzie zdarzeń przejdź do **pozycji Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **Aplikacje serwera aplikacji**, a następnie **analityczny**. Kliknij prawym przyciskiem myszy pozycję **Analityczna** i wybierz polecenie **Włącz dziennik**.  
  
10. Przetestuj usługę przy użyciu klienta testowego WCF.  
  
    1. W kliencie testowym WCF kliknij dwukrotnie przycisk **Add()** w węźle usługi ICalculator.  
  
         Metoda **Add()** pojawia się w prawym okienku z dwoma parametrami.  
  
    2. Wpisz 2 dla pierwszego parametru i 3 dla drugiego parametru.  
  
    3. Kliknij **przycisk Wywołaj,** aby wywołać metodę.  
  
11. Przejdź do okna **Podglądu zdarzeń,** które zostało już otwarte. Przejdź do **przeglądarki zdarzeń,** **dzienników aplikacji i usług,** **firmy Microsoft,** **Systemu Windows,** **aplikacji serwerowych**.  
  
12. Kliknij prawym przyciskiem myszy węzeł **analityczny** i wybierz polecenie **Odśwież**.  
  
     Zdarzenia są wyświetlane w prawym okienku.  
  
13. Znajdź zdarzenie o identyfikatorze 303 i kliknij go dwukrotnie, aby je otworzyć i sprawdzić jego zawartość.  
  
     To zdarzenie zostało wyemitowane przez `Add()` metodę usługi ICalculator i ma ładunek równy "2 +3=5".  
  
#### <a name="to-clean-up-optional"></a>Aby wyczyścić (opcjonalnie)  
  
1. Otwórz **Podgląd zdarzeń**.  
  
2. Przejdź do **przeglądarki zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **application-server-applications**. Kliknij prawym przyciskiem myszy pozycję **Analityczna** i wybierz polecenie **Wyłącz dziennik**.  
  
3. Przejdź do **usługi Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **Aplikacje-Serwer-Aplikacje**, a następnie **analityczne**. Kliknij prawym przyciskiem myszy pozycję **Analityczna** i wybierz polecenie **Wyczyść dziennik**.  
  
4. Kliknij **przycisk Wyczyść,** aby wyczyścić zdarzenia.  
  
## <a name="known-issue"></a>Znany problem  
 W **Podglądzie zdarzeń** występuje znany problem, w którym może nie dokodowywać zdarzeń ETW. Może zostać wyświetlony komunikat o błędzie informujący: \<"Nie można odnaleźć opisu identyfikatora zdarzenia> ze źródła Microsoft-Windows-Application Server-Applications. Składnik, który wywołuje to zdarzenie nie jest zainstalowany na komputerze lokalnym lub instalacja jest uszkodzona. Składnik można zainstalować lub naprawić na komputerze lokalnym." Jeśli wystąpi ten błąd, wybierz **polecenie Odśwież** z menu **Akcje.** Zdarzenie powinno następnie poprawnie zdekodować.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>Zobacz też

- [Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
