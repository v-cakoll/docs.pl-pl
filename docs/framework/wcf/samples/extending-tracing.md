---
title: Rozszerzanie śledzenia
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: 59bdfeea41bac812840ffe166895050a6cd1ad2d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600519"
---
# <a name="extend-tracing"></a>Rozwiń śledzenie

Ten przykład pokazuje, jak zwiększyć funkcję śledzenia Windows Communication Foundation (WCF), pisząc ślady aktywności zdefiniowane przez użytkownika w kodzie klienta i usługi. Pisanie śladów aktywności zdefiniowanej przez użytkownika umożliwia użytkownikowi tworzenie działań śledzenia i grupowanie śladów w logiczne jednostki pracy. Istnieje również możliwość skorelowania działań przez transfery (w tym samym punkcie końcowym) i propagacji (między punktami końcowymi). W tym przykładzie śledzenie jest włączone zarówno dla klienta, jak i dla usługi. Aby uzyskać więcej informacji na temat włączania śledzenia w plikach konfiguracji klienta i usługi, zobacz [śledzenie i rejestrowanie komunikatów](tracing-and-message-logging.md).  
  
 Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>Śledzenie i Propagacja działań  
 Śledzenie aktywności zdefiniowane przez użytkownika umożliwia użytkownikowi tworzenie własnych działań śledzenia w celu grupowania śladów w logiczne jednostki pracy, skorelowanie działań przez transfery i propagację oraz zmniejszanie kosztów wydajności śledzenia WCF (na przykład koszt miejsca na dysku w pliku dziennika).  
  
### <a name="add-custom-sources"></a>Dodawanie niestandardowych źródeł  
 Ślady zdefiniowane przez użytkownika mogą być dodawane do kodu klienta i usługi. Dodawanie źródeł śledzenia do plików konfiguracji klienta lub usługi pozwala na rejestrowanie tych niestandardowych śladów i wyświetlanie ich w [narzędziu Podgląd śledzenia usługi (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md). Poniższy kod przedstawia sposób dodawania zdefiniowanego przez użytkownika źródła śledzenia o nazwie `ServerCalculatorTraceSource` do pliku konfiguracji.  
  
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
</system.diagnostics>
....
```  
  
### <a name="correlate-activities"></a>Skorelowanie działań  
 Aby skorelować działania bezpośrednio między punktami końcowymi, `propagateActivity` atrybut musi być ustawiony na `true` w `System.ServiceModel` źródle śledzenia. Ponadto w celu propagowania śladów bez przechodzenia przez działania programu WCF należy wyłączyć śledzenie działań elementu ServiceModel. Może to być widoczne w poniższym przykładzie kodu.  
  
> [!NOTE]
> Wyłączenie śledzenia aktywności zestawu elementów nie jest takie samo jak w przypadku poziomu śledzenia, oznaczonego przez właściwość jako `switchValue` off.  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessen-performance-cost"></a>Zmniejszanie kosztów wydajności  
 Ustawienie `ActivityTracing` wyłączone w `System.ServiceModel` źródle śledzenia generuje plik śledzenia, który zawiera tylko ślady aktywności zdefiniowane przez użytkownika, bez dołączania żadnych śladów działania programu ServiceModel. Wykluczenie wyników śledzenia działania programu ServiceModel skutkuje znacznie mniejszym plikiem dziennika. Jednak możliwość skorelowania śladów przetwarzania danych WCF zostanie utracona.  
  
## <a name="set-up-build-and-run-the-sample"></a>Konfigurowanie, kompilowanie i uruchamianie przykładu  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przykłady monitorowania oprogramowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
