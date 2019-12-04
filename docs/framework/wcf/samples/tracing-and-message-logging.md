---
title: Śledzenie i rejestrowanie komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: f6f2fd0bbbc191d466ac600bd9639c8955d5b7fe
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715676"
---
# <a name="tracing-and-message-logging"></a>Śledzenie i rejestrowanie komunikatów
Ten przykład pokazuje, jak włączyć śledzenie i rejestrowanie komunikatów. Wynikowe ślady i dzienniki komunikatów są wyświetlane za pomocą [narzędzia Podgląd śledzenia usług (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="tracing"></a>Śledzenie  
 Windows Communication Foundation (WCF) używa mechanizmu śledzenia zdefiniowanego w przestrzeni nazw <xref:System.Diagnostics>. W tym modelu śledzenia dane śledzenia są tworzone przez źródła śledzenia wdrażane przez aplikacje. Każde źródło jest identyfikowane przez nazwę. Użytkownicy śledzenia tworzą detektory śledzenia dla źródeł śledzenia, dla których chcą pobrać informacje. Aby odbierać dane śledzenia, należy utworzyć odbiornik dla źródła śledzenia. W programie WCF można to zrobić, dodając następujący kod do pliku konfiguracji usługi lub klienta, ustawiając Źródło śledzenia modelu usług `switchValue`:  
  
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
  
 Więcej informacji o źródłach śledzenia znajduje się w sekcji Źródło śledzenia w temacie [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) .  
  
## <a name="activity-tracing-and-propagation"></a>Śledzenie działań i Propagacja  
 `ActivityTracing` włączone i `propagateActivity` ustawione na `true` w `system.ServiceModel` źródła śledzenia zarówno dla klienta, jak i usługi zapewniają korelację śladów w jednostkach logicznych przetwarzania (działania), między działaniami w punktach końcowych (za pośrednictwem transferów aktywności) i między działaniami obejmującymi wiele punktów końcowych (za pośrednictwem propagacji identyfikatora działania).  
  
 Te trzy mechanizmy (działania, transfery i propagacje) mogą pomóc w szybkim wyszukiwaniu głównej przyczyny błędu za pomocą narzędzia Podgląd śledzenia usługi. Aby uzyskać więcej informacji, zobacz [Korzystanie z przeglądarki śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Można zwiększyć śledzenie dostarczone przez element ServiceModel, tworząc zdefiniowane przez użytkownika ślady aktywności. Śledzenie działań zdefiniowane przez użytkownika umożliwia użytkownikowi tworzenie działań śledzenia:  
  
- Grupuj ślady na jednostki logiczne pracy.  
  
- Skorelowanie działań przy użyciu transferów i propagacji.  
  
- Obniżenie kosztu wydajności śledzenia WCF (na przykład koszt miejsca na dysku w pliku dziennika).  
  
 Aby uzyskać więcej informacji na temat śledzenia aktywności zdefiniowanej przez użytkownika, zobacz [rozszerzanie](../../../../docs/framework/wcf/samples/extending-tracing.md) przykładu śledzenia.  
  
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
  
 Skonfiguruj odbiornik śledzenia, dodając następujący kod do sekcji <xref:System.Diagnostics> pliku App. config klienta lub pliku Web. config usługi:  
  
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
  
 Więcej informacji o rejestrowaniu komunikatów znajduje się w temacie [Konfigurowanie rejestrowania komunikatów](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) .  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Przed uruchomieniem przykładu śledzenia i rejestrowania komunikatów Utwórz katalog C:\logs\ dla usługi, aby napisać pliki. svclog do programu. Nazwa tego katalogu jest zdefiniowana w pliku konfiguracji jako ścieżka śledzenia i komunikatów, które mają być rejestrowane i można je zmienić. Przyznaj usłudze sieciowej dostępu zapis do katalogu dzienników.  
  
3. Aby skompilować C# C++lub Visual Basic wersję .NET rozwiązania, należy postępować zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>Zobacz także

- [Śledzenie](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Przykłady monitorowania oprogramowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
