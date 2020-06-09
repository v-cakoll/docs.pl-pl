---
title: Śledzenie i rejestrowanie komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 9af50f138a2788fc7af0ce5d07e95df49d6675cb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602651"
---
# <a name="tracing-and-message-logging"></a>Śledzenie i rejestrowanie komunikatów
Ten przykład pokazuje, jak włączyć śledzenie i rejestrowanie komunikatów. Wynikowe ślady i dzienniki komunikatów są wyświetlane za pomocą [narzędzia Podgląd śledzenia usług (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md). Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="tracing"></a>Śledzenie  
 Windows Communication Foundation (WCF) używa mechanizmu śledzenia zdefiniowanego w <xref:System.Diagnostics> przestrzeni nazw. W tym modelu śledzenia dane śledzenia są tworzone przez źródła śledzenia wdrażane przez aplikacje. Każde źródło jest identyfikowane przez nazwę. Użytkownicy śledzenia tworzą detektory śledzenia dla źródeł śledzenia, dla których chcą pobrać informacje. Aby odbierać dane śledzenia, należy utworzyć odbiornik dla źródła śledzenia. W programie WCF można to zrobić, dodając następujący kod do pliku konfiguracji usługi lub klienta, ustawiając Źródło śledzenia modelu usługi `switchValue` :  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 Więcej informacji o źródłach śledzenia znajduje się w sekcji Źródło śledzenia w temacie [Konfigurowanie śledzenia](../diagnostics/tracing/configuring-tracing.md) .  
  
## <a name="activity-tracing-and-propagation"></a>Śledzenie działań i Propagacja  
 `ActivityTracing`Włączenie i `propagateActivity` ustawienie `true` w `system.ServiceModel` źródła śledzenia zarówno dla klienta, jak i usługi zapewnia korelację śladów w jednostkach logicznych przetwarzania (działania), między działaniami w punktach końcowych (za pośrednictwem transferów aktywności) i między działaniami obejmującymi wiele punktów końcowych (za pośrednictwem propagacji identyfikatora działania).  
  
 Te trzy mechanizmy (działania, transfery i propagacje) mogą pomóc w szybkim wyszukiwaniu głównej przyczyny błędu za pomocą narzędzia Podgląd śledzenia usługi. Aby uzyskać więcej informacji, zobacz [Korzystanie z przeglądarki śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Można zwiększyć śledzenie dostarczone przez element ServiceModel, tworząc zdefiniowane przez użytkownika ślady aktywności. Śledzenie działań zdefiniowane przez użytkownika umożliwia użytkownikowi tworzenie działań śledzenia:  
  
- Grupuj ślady na jednostki logiczne pracy.  
  
- Skorelowanie działań przy użyciu transferów i propagacji.  
  
- Obniżenie kosztu wydajności śledzenia WCF (na przykład koszt miejsca na dysku w pliku dziennika).  
  
 Aby uzyskać więcej informacji na temat śledzenia aktywności zdefiniowanej przez użytkownika, zobacz [rozszerzanie](extending-tracing.md) przykładu śledzenia.  
  
## <a name="message-logging"></a>Rejestrowanie komunikatów  
 Rejestrowanie komunikatów można włączyć zarówno dla klienta, jak i usługi dowolnej aplikacji WCF. Aby włączyć rejestrowanie komunikatów, należy dodać następujący kod do klienta lub usługi:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels -->  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 Po zarejestrowaniu komunikatu typ śledzenia zależy od tego, czy jest on śledzony na kliencie, czy na serwerze. Na przykład komunikat "Add", który jest wysyłany do klienta, jest śledzony w kategorii "TransportWrite" na kliencie, podczas gdy ten sam komunikat jest śledzony w kategorii "TransportRead" w usłudze.  
  
 Skonfiguruj odbiornik śledzenia, dodając następujący kod do <xref:System.Diagnostics> sekcji pliku App. config klienta lub pliku Web. config usługi:  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 Komunikaty są rejestrowane w formacie XML w katalogu docelowym określonym w pliku konfiguracji.  
  
> [!NOTE]
> Pliki śledzenia nie są tworzone bez wstępnego utworzenia katalogu dziennika. Upewnij się, że katalog C:\logs\ istnieje lub określ alternatywny katalog rejestrowania w konfiguracji odbiornika. Aby uzyskać więcej informacji, zobacz instrukcje wstępne Instalatora na końcu tego dokumentu.  
  
 Więcej informacji o rejestrowaniu komunikatów znajduje się w temacie [Konfigurowanie rejestrowania komunikatów](../diagnostics/configuring-message-logging.md) .  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Przed uruchomieniem przykładu śledzenia i rejestrowania komunikatów Utwórz katalog C:\logs\ dla usługi, aby napisać pliki. svclog do programu. Nazwa tego katalogu jest zdefiniowana w pliku konfiguracji jako ścieżka śledzenia i komunikatów, które mają być rejestrowane i można je zmienić. Przyznaj usłudze sieciowej dostępu zapis do katalogu dzienników.  
  
3. Aby skompilować wersję rozwiązania dla języka C#, C++ lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](../diagnostics/tracing/index.md)
- [Przykłady monitorowania oprogramowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
