---
title: Rozszerzanie śledzenia
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: a7231d340d2528a42c8cbb5294d812d52db92d54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183687"
---
# <a name="extending-tracing"></a>Rozszerzanie śledzenia
W tym przykładzie pokazano, jak rozszerzyć funkcję śledzenia programu Windows Communication Foundation (WCF), zapisując ślady aktywności zdefiniowane przez użytkownika w kodzie klienta i usługi. Dzięki temu użytkownik może tworzyć działania śledzenia i grupować ślady w logiczne jednostki pracy. Możliwe jest również skorelowanie działań za pośrednictwem transferów (w ramach tego samego punktu końcowego) i propagacji (między punktami końcowymi). W tym przykładzie śledzenie jest włączone dla klienta i usługi. Aby uzyskać więcej informacji na temat włączania śledzenia w plikach konfiguracyjnych klienta i usługi, zobacz [Śledzenie i rejestrowanie wiadomości](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>Śledzenie i propagacja aktywności  
 Śledzenie aktywności zdefiniowane przez użytkownika umożliwia użytkownikowi tworzenie własnych działań śledzenia w celu grupowania śladów w logiczne jednostki pracy, skorelowanie działań poprzez transfery i propagację oraz zmniejszenie kosztów wydajności śledzenia WCF (na przykład koszt miejsca na dysku pliku dziennika).  
  
### <a name="adding-custom-sources"></a>Dodawanie źródeł niestandardowych  
 Ślady zdefiniowane przez użytkownika można dodać do kodu klienta i usługi. Dodawanie źródeł śledzenia do plików konfiguracyjnych klienta lub usługi umożliwia rejestrowanie i wyświetlanie tych niestandardowych śladów w [narzędziu Service Trace Viewer Tool (SvcTraceViewer.exe).](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) Poniższy kod pokazuje, jak dodać źródło `ServerCalculatorTraceSource` śledzenia zdefiniowane przez użytkownika o nazwie do pliku konfiguracji.  
  
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
  
### <a name="correlating-activities"></a>Działania korelujące  
 Aby skorelować działania bezpośrednio między punktami końcowymi, `propagateActivity` `true` atrybut `System.ServiceModel` musi być ustawiony w źródle śledzenia. Ponadto do propagowania śladów bez przechodzenia przez WCF działań, ServiceModel śledzenia aktywności musi być wyłączony. Można to zobaczyć w poniższym przykładzie kodu.  
  
> [!NOTE]
> Wyłączenie śledzenia aktywności Usługi ServiceModel nie jest tym samym, co `switchValue` poziom śledzenia, oznaczony przez właściwość, ustawiony na wyłączony.  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a>Zmniejszenie kosztów wydajności  
 Ustawienie `ActivityTracing` wyłączone w `System.ServiceModel` źródle śledzenia generuje plik śledzenia, który zawiera tylko ślady aktywności zdefiniowane przez użytkownika, bez żadnych servicemodel śledzenia aktywności zawarte. Powoduje to plik dziennika o znacznie mniejszym rozmiarze. Jednak możliwość skorelowania śladów przetwarzania WCF zostanie utracona.  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też

- [Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
