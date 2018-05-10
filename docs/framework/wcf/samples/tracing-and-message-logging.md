---
title: Śledzenie i rejestrowanie komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 13d23c0f69c65dd3bd6b2714dd710eb7f97a1c07
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="tracing-and-message-logging"></a>Śledzenie i rejestrowanie komunikatów
W tym przykładzie pokazano, jak włączyć śledzenie i rejestrowanie komunikatów. Wynikowa śladów i dzienników komunikatów wyświetlane przy użyciu [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="tracing"></a>Śledzenie  
 Windows Communication Foundation (WCF) używa mechanizmu śledzenia zdefiniowanych w <xref:System.Diagnostics> przestrzeni nazw. W tym modelu śledzenie danych śledzenia jest generowany przez źródła śledzenia, które implementują aplikacji. Każde źródło jest identyfikowane przez nazwę. Śledzenia konsumenci tworzą obiekty nasłuchujące śledzenia dla źródła śledzenia, dla których chcesz pobrać informacji. Aby odbierać dane śledzenia, należy utworzyć odbiornik źródła śledzenia. W programie WCF, można to zrobić, dodając następujący kod do pliku konfiguracji usługi lub klienta przez ustawienie źródło śladu modelu usługi `switchValue`:  
  
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
  
 Aby uzyskać więcej informacji na temat źródeł śledzenia, zobacz sekcję źródła śledzenia w [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) tematu.  
  
## <a name="activity-tracing-and-propagation"></a>Śledzenie działania i propagacji  
 O `ActivityTracing` włączone i `propagateActivity` ustawioną `true` w `system.ServiceModel` źródła śledzenia dla klienta i usługi dostarczać korelacji śladów w ramach przetwarzania (działania), jednostki logiczne działań wykonywanych w ciągu (punkty końcowe za pomocą działania przesyłania) i działań wykonywanych obejmujących wiele punktów końcowych (za pośrednictwem Propagacja Identyfikatora działania).  
  
 Mechanizmy te trzy (działania, przesyłania i propagacji) może pomóc więcej szybko przy użyciu narzędzia podglądu śledzenia usługi Znajdź przyczynę błędu. Aby uzyskać więcej informacji, zobacz [przy użyciu przeglądarki śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Istnieje możliwość rozszerzenia śledzenie zapewnianej przez ServiceModel przez utworzenie śladów działania zdefiniowane przez użytkownika. Śledzenie działania zdefiniowane przez użytkownika umożliwia użytkownikom tworzenie śledzenia działań do:  
  
-   Grupa śledzenia w logiczne jednostki pracy.  
  
-   Korelowanie działania za pośrednictwem przesyłania i propagacji.  
  
-   Ogranicza koszty wydajności śledzenia WCF (na przykład kosztu miejsca na dysku w pliku dziennika).  
  
 Aby uzyskać więcej informacji dotyczących śledzenia zdefiniowanych przez użytkownika działań, zobacz [rozszerzanie śledzenia](../../../../docs/framework/wcf/samples/extending-tracing.md) próbki.  
  
## <a name="message-logging"></a>Rejestrowanie komunikatów  
 Zarówno na kliencie i usługi WCF dowolnej aplikacji, można włączyć rejestrowanie komunikatów. Aby włączyć rejestrowanie komunikatów, musi Dodaj następujący kod do klienta lub usługi:  
  
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
  
 Gdy komunikat jest rejestrowany, śledzenia zależy od tego, czy jest są śledzone na klienta lub serwera. Na przykład komunikat "Dodaj", który jest wysyłany do klienta jest śledzone w kategorii "TransportWrite" po stronie klienta, podczas gdy ten sam komunikat śledzonego w kategorii "TransportRead" w punkcie usług.  
  
 Skonfiguruj odbiornik śledzenia, dodając następujący kod do <xref:System.Diagnostics> sekcji w pliku App.config klienta lub usługi w pliku Web.config:  
  
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
  
 Komunikaty są rejestrowane w formacie XML w katalog docelowy określony w pliku konfiguracji.  
  
> [!NOTE]
>  Pliki śledzenia nie są tworzone bez początkowo tworzenia katalogu dziennika. Upewnij się, że istnieje katalog C:\logs\, lub określ katalog rejestrowania alternatywny w konfiguracji odbiornika. Zapoznaj się z instrukcjami instalacji początkowej na końcu tego dokumentu, aby uzyskać więcej informacji.  
  
 Aby uzyskać więcej informacji na temat rejestrowania komunikatów, zobacz [Konfigurowanie rejestrowania komunikatów](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) tematu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Przed uruchomieniem przykładowe śledzenie i rejestrowanie komunikatów, należy utworzyć katalog C:\logs\ usługi do zapisania plików .svclog do. Nazwa tego katalogu jest zdefiniowana w pliku konfiguracyjnym jako ścieżkę do śledzenia i komunikaty, które mają być rejestrowane i może być zmieniona. W katalogu dzienników, należy przyznać użytkownikowi dostęp do zapisu usługi sieciowej.  
  
3.  Tworzenie wersji języka C#, C++ lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Przykłady monitorowania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
