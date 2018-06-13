---
title: Śledzenie za pomocą pliku tekstowego
ms.date: 03/30/2017
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
ms.openlocfilehash: aa59ab8304c68873c938f42fc585be883b234ecc
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805801"
---
# <a name="tracking-using-a-text-file"></a>Śledzenie za pomocą pliku tekstowego
W tym przykładzie pokazano, jak rozszerzyć śledzenia w systemie Windows Workflow Foundation (WF) przez utworzenie uczestnika śledzenia niestandardowych. Klasy .NET Framework, które odbierają rekordy śledzenia z środowiska uruchomieniowego, ponieważ są one emitowane się uczestników śledzenia. Można utworzyć uczestnika śledzenia do transportu zdarzenia śledzenia do niezależnie od docelowego jest wymagane dla danego scenariusza. Na przykład uczestnika śledzenia funkcji ETW (zdarzenia śledzenia dla systemu Windows) jest dostarczana jako część [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Uczestnik śledzenia w tym przykładzie zapisuje rekordy w formacie XML w pliku tekstowym.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Aby zoptymalizować użyteczność i niezawodność sieci uczestnika śledzenia, dodatkowe kroki musi zostać wypełniony prawidłowo okablować uczestnika śledzenia do środowiska wykonawczego. W poniższej tabeli opisano klasy używane w tym przykładzie do tworzenia uczestnika śledzenia, który jest zgodny z najlepszymi rozwiązaniami.  
  
|Class|Opis|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> służy do definiowania sekcji konfiguracji używane do konfigurowania tego uczestnika tekstu pliku śledzenia. Dzięki temu użytkownicy mogą określić miejsce docelowe pliku dziennika przy użyciu standardowe pliki konfiguracji .NET Framework.|  
|`TextFileTrackingBehavior`|Zachowania w programie WCF Zezwalaj użytkownikom na iniekcję rozszerzenia w czasie wykonywania. To zachowanie dodaje uczestnika śledzenia do usługi, po uruchomieniu usługi.|  
|`TextFileTrackingParticipant`|Uczestnik śledzenia, który odbiera uczestników śledzenia w czasie wykonywania i zapisuje je w pliku dziennika w formacie XML.|  
  
## <a name="behavior-extension-elements-configuration"></a>Zachowanie rozszerzenia elementów konfiguracji  
 Jeden krok jest wymagany, aby użyć elementu rozszerzenia zachowanie opisany wcześniej za pomocą plików konfiguracji platformy .NET Framework. Następująca konfiguracja muszą znajdować się w plikach konfiguracji, w którym ma być używany rozszerzenia.  
  
```xml  
<system.serviceModel>  
    <extensions>  
      <behaviorExtensions>  
        <add name="textFileTracking" type="Microsoft.Samples.TextFileTracking.TextFileTrackingExtensionElement, WFStockPriceApplication, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
…  
  </system.serviceModel>  
```  
  
> [!NOTE]
>  Znajduje się w pliku Web.config w próbce użytkowania pełny przykład zachowanie rozszerzenia elementów konfiguracji.  
  
## <a name="custom-tracking-records"></a>Śledzenie niestandardowych rekordów  
 Plik GetStockPrices.cs demonstruje sposób tworzenia niestandardowych śledzenie rekordów z poziomu <xref:System.Activities.CodeActivity>. Wyszukaj ten rekord podczas uruchamiania próbki.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania WFStockPriceApplication.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
     Oknie przeglądarki zostanie otwarty i zawiera katalog zawierający informacje o aplikacji.  
  
4.  W przeglądarce kliknij przycisk StockPriceService.xamlx.  
  
5.  Wyświetla przeglądarki **StockPriceService** strony, która zawiera adres wsdl Usługa lokalna. Skopiuj ten adres.  
  
     Na przykład adres wsdl Usługa lokalna http://localhost:53797/StockPriceService.xamlx?wsdl.  
  
6.  Przy użyciu [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], przejdź do Twojej [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder (%SystemDrive%\Program Files\Microsoft Visual Studio 10.0 domyślny folder instalacji to). Następnie odszukaj podfolder Common7\IDE\.  
  
7.  Kliknij dwukrotnie plik WcfTestClient.exe, aby uruchomić klienta testowego WCF.  
  
8.  W kliencie testowym WCF, wybierz **Dodawanie usługi...** z **pliku** menu.  
  
9. Wklej skopiowany w polu tekstowym adres URL.  
  
10. Kliknij przycisk **OK** aby zamknąć okno dialogowe.  
  
11. Przetestuj usługę za pomocą klienta testowego WCF.  
  
    1.  W kliencie testowym WCF, kliknij dwukrotnie **GetStockPrice()** w obszarze **IStockPriceService** węzła.  
  
         **GetStockPrice()** metoda pojawia się w okienku po prawej stronie, z jednym parametrem.  
  
    2.  Jako wartość parametru, wpisz w firmie Contoso.  
  
    3.  Kliknij przycisk **wywołania**.  
  
12. Zobacz śledzonych zdarzeń w pliku dziennika znajduje się w katalogu % APPDATA%\trackingRecords.log danych aplikacji.  
  
    > [!NOTE]
    >  % APPDATA % jest zmienną środowiskową, który jest rozpoznawany jako %SystemDrive%\Users\\< nazwa_użytkownika\>\AppData\Roaming w [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], lub Windows Server 2008.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
