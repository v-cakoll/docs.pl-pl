---
title: Śledzenie za pomocą pliku tekstowego
ms.date: 03/30/2017
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
ms.openlocfilehash: 19b4d544bc1d1c5bc9ebfa51b4ba28eb82c525d0
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45674601"
---
# <a name="tracking-using-a-text-file"></a>Śledzenie za pomocą pliku tekstowego
Niniejszy przykład pokazuje, jak rozszerzyć śledzenia w Windows Workflow Foundation (WF) przez tworzenie niestandardowego uczestnika śledzenia. Śledzenie uczestników są odbierać rekordów śledzenia ze środowiska wykonawczego, ponieważ są one emitowane klas .NET Framework. Można utworzyć uczestnikiem śledzenia do transportu zdarzenia śledzenia, niezależnie od docelowego jest wymagane dla danego scenariusza. Na przykład uczestnika śledzenia zdarzeń systemu Windows (Event Tracing for Windows) jest dostarczana jako część [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Uczestnik śledzenia w tym przykładzie zapisuje rekordy w formacie XML do pliku tekstowego.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 W celu zoptymalizowania użyteczność i niezawodność usługi śledzenia uczestnika, celu prawidłowo podłączenia uczestnikiem śledzenia do środowiska uruchomieniowego, należy wykonać kilka dodatkowych kroków. W poniższej tabeli opisano klasy używane w tym przykładzie do tworzenia śledzenia uczestnika, który jest zgodny z najlepszymi rozwiązaniami.  
  
|Class|Opis|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> służy do definiowania sekcja konfiguracji umożliwia skonfigurowanie uczestnika śledzenia pliku tekstowego. Dzięki temu użytkownicy mogą określić miejsce docelowe pliku dziennika przy użyciu standardowe pliki konfiguracji .NET Framework.|  
|`TextFileTrackingBehavior`|Zachowania w programie WCF umożliwiają użytkownikom wstrzyknąć rozszerzenia w czasie wykonywania. To zachowanie dodaje uczestnikiem śledzenia do usługi, po uruchomieniu usługi.|  
|`TextFileTrackingParticipant`|Śledzenia uczestnika, który odbiera uczestników śledzenia w czasie wykonywania i zapisuje je w pliku dziennika w formacie XML.|  
  
## <a name="behavior-extension-elements-configuration"></a>Zachowanie rozszerzenia elementów konfiguracji  
 Jeszcze jeden krok jest wymagany, aby użyć elementu rozszerzenia zachowanie opisany wcześniej za pomocą plików konfiguracji .NET Framework. Następująca konfiguracja muszą być umieszczone w plikach konfiguracji, których rozszerzenie ma być używany.  
  
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
>  Można znaleźć w pliku Web.config w przykładzie użycie kompletny przykład, zachowanie rozszerzeń elementów konfiguracji.  
  
## <a name="custom-tracking-records"></a>Niestandardowe rekordy śledzenia  
 Plik GetStockPrices.cs pokazuje, jak utworzyć niestandardowe rekordy śledzenia z poziomu <xref:System.Activities.CodeActivity>. Poszukaj tego rekordu, gdy działa aplikacja przykładowa.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania WFStockPriceApplication.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
     Okno przeglądarki otwiera i pokazuje katalog zawierający informacje o aplikacji.  
  
4.  W przeglądarce kliknij przycisk StockPriceService.xamlx.  
  
5.  Wyświetla przeglądarki **StockPriceService** strony, która zawiera adres wsdl Usługa lokalna. Skopiuj ten adres.  
  
     Na przykład adres wsdl Usługa lokalna http://localhost:53797/StockPriceService.xamlx?wsdl.  
  
6.  Za pomocą [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], przejdź do swojej [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder (domyślny folder instalacji to %SystemDrive%\Program Files\Microsoft Visual Studio 10.0). Następnie znajdź podfolder Common7\IDE\.  
  
7.  Kliknij dwukrotnie plik WcfTestClient.exe, aby uruchomić klienta testowego WCF.  
  
8.  W kliencie testowym WCF wybierz **Dodaj usługę...** z **pliku** menu.  
  
9. Wklej adres URL został skopiowany do pola tekstowego.  
  
10. Kliknij przycisk **OK** aby zamknąć okno dialogowe.  
  
11. Przetestuj usługę za pomocą klienta testowego WCF.  
  
    1.  W kliencie testowym WCF, kliknij dwukrotnie **GetStockPrice()** w obszarze **IStockPriceService** węzła.  
  
         **GetStockPrice()** metoda pojawia się w okienku po prawej stronie, z jednym parametrem.  
  
    2.  Wpisz w firmie Contoso jako wartość parametru.  
  
    3.  Kliknij przycisk **wywołania**.  
  
12. Zobacz rejestrowanych zdarzeń w pliku dziennika, znajduje się w katalogu % APPDATA%\trackingRecords.log danych aplikacji.  
  
    > [!NOTE]
    >  % APPDATA % jest zmienną środowiskową, który jest rozpoznawany jako %SystemDrive%\Users\\< nazwa_użytkownika\>\AppData\Roaming w [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], lub Windows Server 2008.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
