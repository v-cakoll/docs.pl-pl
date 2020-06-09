---
title: Śledzenie za pomocą funkcji ETW
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 0bdbf6699a0cfa3dce58abda4c989fb25d764459
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600566"
---
# <a name="etw-tracing"></a>Śledzenie za pomocą funkcji ETW
W tym przykładzie pokazano, jak zaimplementować śledzenie kompleksowego (E2E) przy użyciu funkcji śledzenia zdarzeń systemu Windows (ETW) i `ETWTraceListener` dostarczonej z tym przykładem. Przykład jest oparty na [wprowadzenie](getting-started-sample.md) i zawiera śledzenie ETW.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie założono, że wiesz już, [jak śledzenie i rejestrowanie komunikatów](tracing-and-message-logging.md).  
  
 Każde źródło śledzenia w <xref:System.Diagnostics> modelu śledzenia może mieć wiele detektorów śledzenia, które określają miejsce i sposób, w jaki dane są śledzone. Typ odbiornika definiuje format, w którym rejestrowane są dane śledzenia. Poniższy przykład kodu pokazuje, jak dodać odbiornik do konfiguracji.  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel"
             switchValue="Verbose,ActivityTracing"  
             propagateActivity="true">  
            <listeners>  
                <add type=  
                   "System.Diagnostics.DefaultTraceListener"  
                   name="Default">  
                   <filter type="" />  
                </add>  
                <add name="ETW">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
        <add type=  
            "Microsoft.ServiceModel.Samples.EtwTraceListener, ETWTraceListener"  
            name="ETW" traceOutputOptions="Timestamp">  
            <filter type="" />  
       </add>  
    </sharedListeners>  
</system.diagnostics>  
```  
  
 Przed użyciem tego odbiornika należy uruchomić sesję śledzenia ETW. Tę sesję można uruchomić przy użyciu narzędzia Logman. exe lub tracelog. exe. Plik SetupETW. bat jest dołączony do tego przykładu, aby można było skonfigurować sesję śledzenia ETW wraz z plikiem CleanupETW. bat do zamykania sesji i wypełniania pliku dziennika.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu. Aby uzyskać więcej informacji na temat tych narzędzi, zobacz.<https://go.microsoft.com/fwlink/?LinkId=56580>  
  
 W przypadku korzystania z ETWTraceListener, ślady są rejestrowane w binarnych plikach. etl. Śledzenie ServiceModel jest włączone, wszystkie wygenerowane ślady pojawiają się w tym samym pliku. Użyj [narzędzia Podgląd śledzenia usług (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) do wyświetlania plików dziennika. ETL i. svclog. Przeglądarka tworzy kompleksowy widok systemu, który umożliwia śledzenie komunikatu z jego źródła do jego lokalizacji docelowej i punktu zużycia.  
  
 Odbiornik śledzenia ETW obsługuje rejestrowanie cykliczne. Aby włączyć tę funkcję, przejdź do **menu Start**, **Uruchom** polecenie i wpisz, `cmd` Aby uruchomić konsolę poleceń. W poniższym poleceniu Zastąp `<logfilename>` parametr nazwą pliku dziennika.  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 `-f`Przełączniki i `-max` są opcjonalne. Określają one odpowiednio binarny format cykliczny i maksymalny rozmiar dziennika 1000 MB. `-p`Przełącznik służy do określania dostawcy śledzenia. W naszym przykładzie `"{411a0819-c24b-428c-83e2-26b41091702e}"` jest identyfikator GUID dla "przykładowego dostawcy funkcji ETW języka XML".  
  
 Aby rozpocząć sesję, wpisz następujące polecenie.  
  
```console  
logman start Wcf  
```  
  
 Po zakończeniu rejestrowania możesz zatrzymać sesję przy użyciu poniższego polecenia.  
  
```console  
logman stop Wcf  
```  
  
 Ten proces generuje binarne dzienniki cykliczne, które można przetwarzać za pomocą wybranego narzędzia, w tym [Narzędzia do przeglądania śledzenia usługi (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) lub tracerpt.  
  
 Możesz również przejrzeć przykład [cyklicznego śledzenia](circular-tracing.md) , aby uzyskać więcej informacji na temat alternatywnego odbiornika do wykonywania rejestrowania cyklicznego.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
    > [!NOTE]
    > Aby użyć poleceń RegisterProvider. bat, SetupETW. bat i CleanupETW. bat, należy uruchomić program przy użyciu konta administratora lokalnego. W przypadku korzystania z systemu Windows Vista lub nowszego należy również uruchomić wiersz polecenia z podwyższonym poziomem uprawnień. Aby to zrobić, kliknij prawym przyciskiem myszy ikonę wiersza polecenia, a następnie kliknij polecenie **Uruchom jako administrator**.  
  
3. Przed uruchomieniem przykładu należy uruchomić program RegisterProvider. bat na kliencie i serwerze. Powoduje to skonfigurowanie wynikowego pliku ETWTracingSampleLog. etl w celu wygenerowania śladów, które mogą być odczytywane przez Podgląd śledzenia usługi. Ten plik znajduje się w folderze C:\LOGS. Jeśli ten folder nie istnieje, należy go utworzyć lub nie są generowane żadne dane śledzenia. Następnie uruchom program SetupETW. bat na komputerach klienckich i serwerach, aby rozpocząć sesję śledzenia ETW. Plik SetupETW. bat można znaleźć w folderze CS\Client.  
  
4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
5. Po zakończeniu przykładu należy uruchomić CleanupETW. bat, aby zakończyć tworzenie pliku ETWTracingSampleLog. etl.  
  
6. Otwórz plik ETWTracingSampleLog. etl z poziomu przeglądarki śledzenia usługi. Zostanie wyświetlony monit o zapisanie pliku binarnego w formacie pliku. svclog.  
  
7. Otwórz nowo utworzony plik svclog z poziomu przeglądarki śledzenia usługi, aby wyświetlić dane śledzenia ETW i ServiceModel.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>Zobacz też

- [Przykłady monitorowania oprogramowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
