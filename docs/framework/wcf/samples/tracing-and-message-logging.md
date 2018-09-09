---
title: Śledzenie i rejestrowanie komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 7f729e845fe552d523a46a1783404baf4e0bbfca
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227444"
---
# <a name="tracing-and-message-logging"></a>Śledzenie i rejestrowanie komunikatów
Niniejszy przykład pokazuje, jak włączyć śledzenie i rejestrowanie komunikatów. Wynikowy ślady i dzienniki komunikatów są wyświetlane przy użyciu [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
## <a name="tracing"></a>Śledzenie  
 Windows Communication Foundation (WCF) używa mechanizmu śledzenia, zdefiniowane w <xref:System.Diagnostics> przestrzeni nazw. W tym modelu śledzenia danych śledzenia jest produkowanych przez źródła śledzenia, które implementują aplikacji. Każde źródło jest identyfikowane przez nazwę. Śledzenie konsumenci tworzą obiekty nasłuchujące śledzenia dla źródła śledzenia, dla których chcesz pobrać informacji. Aby odbierać dane śledzenia, należy utworzyć odbiornik dla źródła śledzenia. W programie WCF, można to zrobić, dodając następujący kod do pliku konfiguracji usługi lub klienta przez ustawienie źródło śladu modelu usługi `switchValue`:  
  
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
  
 Aby uzyskać więcej informacji na temat źródła śledzenia, zobacz sekcję źródła śledzenia w [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) tematu.  
  
## <a name="activity-tracing-and-propagation"></a>Śledzenie działania i propagację  
 Posiadanie `ActivityTracing` włączone i `propagateActivity` równa `true` w `system.ServiceModel` źródła śledzenia dla klienta i usługi zapewnienia działania w ramach punktów końcowych (korelacja ślady w ramach przetwarzania (działalności), jednostki logiczne za pośrednictwem przesyłania działania) i na różnych działań, obejmujące wiele punktów końcowych (za pośrednictwem Propagacja Identyfikatora działania).  
  
 Te trzy mechanizmy (działań transferu i propagację) pomóc Ci znaleźć przyczynę błędu, więcej szybko przy użyciu narzędzia przeglądarki danych śledzenia usługi. Aby uzyskać więcej informacji, zobacz [za pomocą przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów z](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Istnieje możliwość rozszerzyć śledzenia, dostarczone przez ServiceModel, tworząc śledzenia działań użytkownika. Śledzenie aktywności użytkownika umożliwia użytkownikowi utworzenie śledzenia działań:  
  
-   Grupa śledzenia w logiczne jednostki pracy.  
  
-   Korelowanie działań przy użyciu transferu i propagacji.  
  
-   Ogranicza koszty wydajności śledzenia WCF (na przykład koszt miejsca na dysku w pliku dziennika).  
  
 Aby uzyskać więcej informacji na temat śledzenia działań użytkownika, zobacz [rozszerzanie śledzenia](../../../../docs/framework/wcf/samples/extending-tracing.md) próbki.  
  
## <a name="message-logging"></a>Rejestrowanie komunikatów  
 Można ją włączyć rejestrowanie komunikatów, zarówno na kliencie i usługi aplikacji WCF. Aby włączyć rejestrowanie komunikatów, należy dodać następujący kod do klienta lub usługi:  
  
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
  
 Gdy komunikat jest rejestrowany, typ śledzenia jest zależna od tego, czy jest on śledzone na klienta lub serwera. Na przykład "Dodaj". komunikat o błędzie jest wysyłany do klienta śledzonego w kategorii "TransportWrite" po stronie klienta, natomiast śledzona jest ten sam komunikat w kategorii "TransportRead" na usługę.  
  
 Konfigurowanie odbiornika śledzenia, dodając następujący kod do <xref:System.Diagnostics> sekcji w pliku App.config klienta lub plik Web.config usługi:  
  
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
  
 Komunikaty są rejestrowane w formacie XML w katalogu docelowym, określone w pliku konfiguracji.  
  
> [!NOTE]
>  Pliki śledzenia nie są tworzone bez początkowo tworzenia katalogu dziennika. Upewnij się, że katalog C:\logs\ istnieje, lub określ katalog rejestrowania alternatywne w konfiguracji odbiornika. Zapoznaj się z instrukcjami instalacji początkowej na końcu tego dokumentu, aby uzyskać więcej informacji.  
  
 Aby uzyskać więcej informacji na temat rejestrowania komunikatów, zobacz [Konfigurowanie rejestrowania komunikatów](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) tematu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Przed uruchomieniem przykładu śledzenia i rejestrowania komunikatów, należy utworzyć katalog C:\logs\ usługi do zapisania plików .svclog do. Nazwa tego katalogu jest zdefiniowana w pliku konfiguracyjnym jako ścieżki dla danych śledzenia i komunikaty, które mają być rejestrowane i można je zmienić. Przyznaj użytkownikowi dostęp do zapisu usługi sieciowej do katalogu logs.  
  
3.  Aby kompilować rozwiązania w wersji języka C#, C++ lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Przykłady monitorowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
