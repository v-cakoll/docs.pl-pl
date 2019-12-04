---
title: Śledzenie cykliczne
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: b0778a25c75ae48c2215625f40b08a1e3815ba81
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716006"
---
# <a name="circular-tracing"></a>Śledzenie cykliczne

Ten przykład pokazuje implementację odbiornika cyklicznego śledzenia buforów. Typowym scenariuszem dla usług produkcyjnych jest posiadanie usług dostępnych przez długi czas i włączenie rejestrowania śledzenia na niskim poziomie. Te usługi zużywają dużo miejsca na dysku. W przypadku rozwiązywania problemów z usługą najnowsze dane w dzienniku śledzenia są istotne do rozwiązywania problemu. Ten przykład pokazuje implementację detektora cyklicznego śledzenia bufora, w którym tylko najnowsze ślady są przechowywane na dysku do konfigurowalnej ilości danych. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i zawiera odbiornik niestandardowego śledzenia.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

W tym przykładzie założono, że znasz przykład [śledzenia i rejestrowania komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) oraz Przeczytaj dokumentację dotyczącą śledzenia i przykładowego [rejestrowania komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) .

## <a name="circular-buffer-trace-listener"></a>Odbiornik cyklicznego śledzenia buforu

Koncepcja w odróżnieniu od implementacji detektora śledzenia cyklicznego buforu ma dwa pliki, które mogą przechowywać do połowy łącznej liczby żądanych danych dziennika śledzenia. Odbiornik tworzy jeden plik i zapisuje je do tego pliku do momentu, aż osiągnie limit o połowie rozmiaru danych, w którym wskazuje na drugi plik. Gdy odbiornik osiągnie limit dla drugiego pliku — zastępuje pierwszy plik nowym śladem.

Ten odbiornik pochodzi z `XmlWriteTraceListener` i umożliwia wyświetlanie dzienników za pomocą [narzędzia Podgląd śledzenia usług (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Podczas próby wyświetlenia dzienników te dwa pliki dziennika można łatwo połączyć przez otwarcie obu plików dziennika w tym samym czasie w narzędziu Podgląd śledzenia usługi. Narzędzie Podgląd śledzenia usług automatycznie zajmuje się sortowaniem śladów, tak aby były wyświetlane w odpowiedniej kolejności.

## <a name="configuration"></a>Konfiguracja

Usługę można skonfigurować tak, aby korzystała z detektora śledzenia cyklicznego buforu przez dodanie następującego kodu dla odbiornika i elementów źródłowych. Maksymalny rozmiar pliku jest określony przez ustawienie atrybutu `maxFileSizeKB` w konfiguracji detektora cyklicznego śledzenia. Przedstawiono to w poniższym kodzie.

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

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`

## <a name="see-also"></a>Zobacz także

- [Przykłady monitorowania oprogramowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
