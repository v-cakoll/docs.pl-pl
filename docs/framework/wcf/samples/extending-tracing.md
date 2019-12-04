---
title: Rozszerzanie śledzenia
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: 64f9d18b68e5f2604631a72579eb45bf7f7b8372
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716401"
---
# <a name="extending-tracing"></a>Rozszerzanie śledzenia
Ten przykład pokazuje, jak zwiększyć funkcję śledzenia Windows Communication Foundation (WCF), pisząc ślady aktywności zdefiniowane przez użytkownika w kodzie klienta i usługi. Dzięki temu użytkownik może tworzyć działania śledzenia i grupować ślady w logiczne jednostki pracy. Istnieje również możliwość skorelowania działań przez transfery (w tym samym punkcie końcowym) i propagacji (między punktami końcowymi). W tym przykładzie śledzenie jest włączone zarówno dla klienta, jak i dla usługi. Aby uzyskać więcej informacji na temat włączania śledzenia w plikach konfiguracji klienta i usługi, zobacz [śledzenie i rejestrowanie komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>Śledzenie i Propagacja działań  
 Śledzenie aktywności zdefiniowane przez użytkownika umożliwia użytkownikowi tworzenie własnych działań śledzenia w celu grupowania śladów w logiczne jednostki pracy, skorelowanie działań za pomocą transferów i propagacji oraz zmniejszanie kosztów wydajności śledzenia WCF (na przykład koszt miejsca na dysku pliku dziennika).  
  
### <a name="adding-custom-sources"></a>Dodawanie źródeł niestandardowych  
 Ślady zdefiniowane przez użytkownika mogą być dodawane do kodu klienta i usługi. Dodawanie źródeł śledzenia do plików konfiguracji klienta lub usługi pozwala na rejestrowanie tych niestandardowych śladów i wyświetlanie ich w [narzędziu Podgląd śledzenia usług (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Poniższy kod przedstawia sposób dodawania zdefiniowanego przez użytkownika źródła śledzenia o nazwie `ServerCalculatorTraceSource` do pliku konfiguracji.  
  
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
  
### <a name="correlating-activities"></a>Korelacja działań  
 Aby skorelować działania bezpośrednio między punktami końcowymi, atrybut `propagateActivity` musi być ustawiony na `true` w źródle śledzenia `System.ServiceModel`. Ponadto w celu propagowania śladów bez przechodzenia przez działania programu WCF należy wyłączyć śledzenie działań elementu ServiceModel. Może to być widoczne w poniższym przykładzie kodu.  
  
> [!NOTE]
> Wyłączenie śledzenia działań ServiceModel nie jest takie samo jak w przypadku poziomu śledzenia, oznaczonego przez właściwość `switchValue`, ustawione na off.  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a>Zmniejszanie kosztów wydajności  
 Ustawienie `ActivityTracing` wyłączone w źródle śledzenia `System.ServiceModel` generuje plik śledzenia, który zawiera tylko ślady aktywności zdefiniowane przez użytkownika, bez dołączania żadnych śladów działania ServiceModel. Powoduje to zmniejszenie rozmiaru pliku dziennika. Jednak możliwość skorelowania śladów przetwarzania danych WCF zostanie utracona.  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady monitorowania oprogramowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
