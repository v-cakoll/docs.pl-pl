---
title: Śledzenie i rejestrowanie komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 9ffb7a99540b953fc93a22d2296caf86f294d25d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143827"
---
# <a name="tracing-and-message-logging"></a>Śledzenie i rejestrowanie komunikatów
W tym przykładzie pokazano, jak włączyć śledzenie i rejestrowanie wiadomości. Wynikowe ślady i dzienniki komunikatów są wyświetlane za pomocą [narzędzia Podgląd śledzenia usług (SvcTraceViewer.exe).](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="tracing"></a>Śledzenie  
 Windows Communication Foundation (WCF) używa mechanizmu <xref:System.Diagnostics> śledzenia zdefiniowanego w obszarze nazw. W tym modelu śledzenia dane śledzenia są tworzone przez źródła śledzenia, które implementują aplikacje. Każde źródło jest identyfikowane przez nazwę. Śledź konsumentów utworzyć detektory śledzenia dla źródeł śledzenia, dla których chcą pobrać informacje. Aby odbierać dane śledzenia, należy utworzyć odbiornik dla źródła śledzenia. W WCF można to zrobić, dodając następujący kod do pliku konfiguracyjnego usługi lub klienta, `switchValue`ustawiając źródło śledzenia modelu usługi:  
  
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
  
 Aby uzyskać więcej informacji na temat źródeł śledzenia, zobacz sekcję Źródło śledzenia w temacie [Konfigurowanie śledzenia.](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
  
## <a name="activity-tracing-and-propagation"></a>Śledzenie i propagacja aktywności  
 Po `ActivityTracing` włączeniu `propagateActivity` i `true` ustawieniu w źródłach `system.ServiceModel` śledzenia dla klienta i usługi zapewniają korelację śladów w ramach jednostek logicznych przetwarzania (działania), między działaniami w punktach końcowych (za pośrednictwem transferów działań) i między działaniami obejmującymi wiele punktów końcowych (za pośrednictwem propagacji identyfikatora działania).  
  
 Te trzy mechanizmy (działania, transfery i propagacji) może pomóc zlokalizować główną przyczynę błędu szybciej za pomocą narzędzia Podgląd śledzenia usługi. Aby uzyskać więcej informacji, zobacz [Używanie przeglądarki śledzenia usług do wyświetlania skorelowanych śladów i rozwiązywania problemów](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Istnieje możliwość rozszerzenia śledzenia, który jest dostarczany przez ServiceModel przez tworzenie śladów aktywności zdefiniowanych przez użytkownika. Śledzenie aktywności zdefiniowane przez użytkownika umożliwia użytkownikowi tworzenie działań śledzenia w celu:  
  
- Grupuj ślady w logiczne jednostki pracy.  
  
- Skorelować działania poprzez transfery i propagacji.  
  
- Zmniejsz koszt wydajności śledzenia WCF (na przykład koszt miejsca na dysku pliku dziennika).  
  
 Aby uzyskać więcej informacji na temat śledzenia aktywności zdefiniowanej przez użytkownika, zobacz [rozszerzenie śledzenia](../../../../docs/framework/wcf/samples/extending-tracing.md) próbki.  
  
## <a name="message-logging"></a>Rejestrowanie komunikatów  
 Rejestrowanie wiadomości można włączyć zarówno na kliencie, jak i w usłudze dowolnej aplikacji WCF. Aby włączyć rejestrowanie wiadomości, należy dodać następujący kod do klienta lub usługi:  
  
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
  
 Po zarejestrowaniu wiadomości typ śledzenia zależy od tego, czy jest śledzony na kliencie, czy na serwerze. Na przykład komunikat "Dodaj", który jest wysyłany do klienta jest śledzony w kategorii "TransportWrite" na kliencie, podczas gdy ten sam komunikat jest śledzony w kategorii "TransportRead" w usłudze.  
  
 Skonfiguruj odbiornik śledzenia, dodając <xref:System.Diagnostics> następujący kod do sekcji pliku App.config klienta lub pliku Web.config usługi:  
  
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
  
 Komunikaty są rejestrowane w formacie XML w katalogu docelowym określonym w pliku konfiguracyjnym.  
  
> [!NOTE]
> Pliki śledzenia nie są tworzone bez początkowego tworzenia katalogu dziennika. Upewnij się, że katalog C:\logs\ istnieje lub określ alternatywny katalog rejestrowania w konfiguracji odbiornika. Aby uzyskać więcej informacji, zobacz instrukcje konfiguracji początkowej na końcu tego dokumentu.  
  
 Aby uzyskać więcej informacji na temat rejestrowania wiadomości, zobacz temat [Rejestrowanie wiadomości konfigurowania.](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Przed uruchomieniem próbki śledzenia i rejestrowania wiadomości utwórz katalog C:\logs\ dla usługi, do którą chcesz zapisać pliki .svclog. Nazwa tego katalogu jest zdefiniowana w pliku konfiguracyjnym jako ścieżka śledzenia i komunikatów, które mają być rejestrowane i mogą być zmieniane. Nadaj użytkownikowi usługę sieciową dostęp do zapisu do katalogu dzienników.  
  
3. Aby utworzyć wersję C#, C++ lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
