---
title: Śledzenie cykliczne
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: 2339cb780cd09a98dd0cb77eefd66b2473597860
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152376"
---
# <a name="circular-tracing"></a>Śledzenie cykliczne
Niniejszy przykład pokazuje implementację odbiornik śledzenia cyklicznego buforu. Typowy scenariusz dla usług produkcyjnych jest usług, które są dostępne przez długi czas i mieć włączone na niskim poziomie rejestrowanie śledzenia. Te usługi to zajmować dużo miejsca na dysku. Podczas rozwiązywania problemów z usługą, najnowsze dane w dzienniku śledzenia dotyczy rozwiązywanie problemów. Niniejszy przykład pokazuje implementację odbiornik śledzenia cyklicznego buforu, w którym tylko najbardziej aktualne dane śledzenia są przechowywane na dysku do skonfigurowanej ilości danych. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i zawiera odbiornik śledzenia niestandardowych.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 W tym przykładzie przyjęto założenie, że czytelnik zna [śledzenia i rejestrowania komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) przykładowe i po ich przeczytaniu w dokumentacji dostarczonej [śledzenia i rejestrowania komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) próbki.  
  
## <a name="circular-buffer-trace-listener"></a>Odbiornik śledzenia cyklicznego buforu  
 Koncepcja za wdrożenia okrągły odbiornik śledzenia bufora ma dwa pliki, które każdy przechowywać do połowy dane dziennika całkowita żądanego śledzenia. Odbiornik tworzy jeden plik i zapisuje do tego pliku, dopóki nie zostanie osiągnięty limit połowę rozmiaru danych, w tym momencie przełączenie do drugiego pliku. Gdy odbiornik osiągnie limit dla drugiego pliku — zastępuje pierwszego pliku przy użyciu nowych danych śledzenia.  
  
 Tego odbiornika jest pochodną `XmlWriteTraceListener` i umożliwia dzienniki aby je przeglądać za pomocą [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Podczas próby wyświetlić dzienniki, dwa pliki dziennika można łatwo odtwarzane, otwierając oba pliki dziennika w tym samym czasie w narzędziu przeglądarki danych śledzenia usługi. Narzędzie przeglądarki danych śledzenia usługi automatycznie zajmie się sortowanie śladów, aby były wyświetlane w odpowiedniej kolejności.  
  
## <a name="configuration"></a>Konfiguracja  
 Usługę można skonfigurować do użycia odbiornik śledzenia cyklicznego buforu, dodając następujący kod dla elementów źródła i odbiornika. Maksymalny rozmiar pliku jest określany przez ustawienie `maxFileSizeKB` atrybut w konfiguracji odbiornika śledzenia cykliczne. Jest to zaprezentowane w poniższym kodzie.  
  
```xml  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">  
      <listeners>  
        <add name="CircularTraceListener" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"   
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Pamiętaj, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady monitorowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
