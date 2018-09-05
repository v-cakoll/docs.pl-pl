---
title: Rozszerzanie śledzenia
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: 02dfcc099883ed1d5e97b4f7b1a1f76d49b27a20
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565148"
---
# <a name="extending-tracing"></a>Rozszerzanie śledzenia
Niniejszy przykład pokazuje, jak rozszerzyć funkcję śledzenia usług Windows Communication Foundation (WCF), pisząc dane śledzenia działań użytkownika w kodzie klienta i usługi. Dzięki temu użytkownikowi na tworzenie śledzenia działań i grupować dane śledzenia w logiczne jednostki pracy. Istnieje również możliwość skorelowania działania za pośrednictwem transfery (w obrębie tego samego punktu końcowego) i propagację (za pośrednictwem punktów końcowych). W tym przykładzie jest włączone śledzenie zarówno klient, jak i usługi. Aby uzyskać więcej informacji o tym, jak włączyć śledzenie w plikach konfiguracji klienta i usługi, zobacz [śledzenia i rejestrowania komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>Śledzenie i propagowania działań.  
 Śledzenie aktywności użytkownika zezwala użytkownikowi na tworzenie własnych śledzenia działań w ramach grupy danych śledzenia w logiczne jednostki pracy, korelować działania za pośrednictwem transferu i propagację i zmniejszyć koszty wydajności śledzenia WCF (na przykład miejsca na dysku, koszt pliku dziennika).  
  
### <a name="adding-custom-sources"></a>Dodawanie źródła niestandardowego  
 Ślady zdefiniowanych przez użytkownika można dodać do kodu zarówno klient, jak i usługi. Dodawanie źródła śledzenia do plików konfiguracji klienta lub usługę umożliwiają ślady te niestandardowe rejestrowane i wyświetlane w [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Poniższy kod przedstawia sposób dodawania źródła śledzenia zdefiniowanych przez użytkownika o nazwie `ServerCalculatorTraceSource` do pliku konfiguracji.  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>....  
....  
```  
  
### <a name="correlating-activities"></a>Korelowanie działań  
 Aby skorelować działania bezpośrednio w obrębie punktów końcowych, `propagateActivity` atrybutu musi być równa `true` w `System.ServiceModel` źródła śledzenia. Ponadto do propagowania ślady bez pośrednictwa usługi WCF działań, śledzenie aktywności ServiceModel musi być wyłączony. Można to zaobserwować w poniższym przykładzie kodu.  
  
> [!NOTE]
>  Wyłączenie śledzenia działań ServiceModel nie jest taka sama jak o poziomie śledzenia, wskazywane przez `switchValue` właściwość ustawiona na wartość off.  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a>Zmniejszenie spadek wydajności  
 Ustawienie `ActivityTracing` na wyłączone w `System.ServiceModel` źródła śledzenia generuje plik śledzenia, który zawiera tylko działania użytkownika ślady, bez jakichkolwiek ślady działania elementu ServiceModel uwzględnione. Skutkuje to znacznie mniejszy rozmiar pliku dziennika. Jednak możliwość korelacji WCF przetwarzania śladów zostaną utracone.  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
