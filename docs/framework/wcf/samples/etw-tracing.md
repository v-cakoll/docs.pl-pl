---
title: Śledzenie za pomocą funkcji ETW
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 07379a464e6635a3de10c08647dbc769a5885e4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183704"
---
# <a name="etw-tracing"></a>Śledzenie za pomocą funkcji ETW
W tym przykładzie pokazano, jak zaimplementować end-to-end (E2E) śledzenia `ETWTraceListener` przy użyciu śledzenia zdarzeń dla systemu Windows (ETW) i który jest dostarczany z tego przykładu. Próbka jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i zawiera śledzenie ETW.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie przyjęto założenie, że użytkownik jest zaznajomiony z [śledzeniem i rejestrowaniem wiadomości.](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)  
  
 Każde źródło śledzenia <xref:System.Diagnostics> w modelu śledzenia może mieć wiele odbiorników śledzenia, które określają, gdzie i jak dane są śledzone. Typ odbiornika definiuje format, w którym rejestrowane są dane śledzenia. Poniższy przykład kodu pokazuje, jak dodać odbiornika do konfiguracji.  
  
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
  
 Przed użyciem tego odbiornika należy uruchomić sesję śledzenia ETW. Tę sesję można uruchomić przy użyciu pliku Logman.exe lub Tracelog.exe. Plik SetupETW.bat jest dołączony do tego przykładu, dzięki czemu można skonfigurować etw śledzenia sesji wraz z plikiem CleanupETW.bat do zamknięcia sesji i ukończenia pliku dziennika.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu. Aby uzyskać więcej informacji na temat tych narzędzi, zobacz<https://go.microsoft.com/fwlink/?LinkId=56580>  
  
 Podczas korzystania z ETWTraceListener, ślady są rejestrowane w binarnych plikach .etl. Po włączeniu śledzenia ServiceModel wszystkie wygenerowane ślady są wyświetlane w tym samym pliku. Narzędzie [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) umożliwia przeglądanie plików dziennika .etl i .svclog. Przeglądarka tworzy widok end-to-end systemu, który umożliwia śledzenie wiadomości ze źródła do miejsca docelowego i punktu zużycia.  
  
 Odbiornik śledzenia ETW obsługuje rejestrowanie cykliczne. Aby włączyć tę funkcję, przejdź do `cmd` ekranu **Start**, **Uruchom** i wpisz, aby uruchomić konsolę poleceń. W poniższym poleceniu zastąp `<logfilename>` parametr nazwą pliku dziennika.  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 `-f` Przełączniki `-max` i są opcjonalne. Określają one binarny format kołowy i maksymalny rozmiar dziennika odpowiednio 1000MB. Przełącznik `-p` jest używany do określenia dostawcy śledzenia. W naszym `"{411a0819-c24b-428c-83e2-26b41091702e}"` przykładzie jest identyfikator GUID dla "XML ETW sample provider".  
  
 Aby rozpocząć sesję, wpisz następujące polecenie.  
  
```console  
logman start Wcf  
```  
  
 Po zakończeniu rejestrowania można zatrzymać sesję za pomocą następującego polecenia.  
  
```console  
logman stop Wcf  
```  
  
 Ten proces generuje binarne dzienniki cykliczne, które można przetwarzać za pomocą wybranego narzędzia, w tym [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) lub Tracerpt.  
  
 Można również przejrzeć próbkę [śledzenia kołowego, aby](../../../../docs/framework/wcf/samples/circular-tracing.md) uzyskać więcej informacji na temat alternatywnego odbiornika do wykonywania rejestrowania cyklicznego.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
    > [!NOTE]
    > Aby użyć poleceń RegisterProvider.bat, SetupETW.bat i CleanupETW.bat, należy uruchomić je pod lokalnym kontem administratora. Jeśli używasz systemu Windows Vista lub nowszego, należy również uruchomić wiersz polecenia z podwyższonymi uprawnieniami. W tym celu kliknij prawym przyciskiem myszy ikonę wiersza polecenia, a następnie kliknij polecenie **Uruchom jako administrator**.  
  
3. Przed uruchomieniem próbki uruchom registerprovider.bat na kliencie i serwerze. Spowoduje to skonfigurowanie wynikowego pliku ETWTracingSampleLog.etl w celu wygenerowania śladów, które mogą być odczytywane przez przeglądarkę śledzenia usług. Ten plik można znaleźć w folderze C:\logs. Jeśli ten folder nie istnieje, musi zostać utworzony lub nie są generowane żadne ślady. Następnie uruchom plik SetupETW.bat na komputerach klienckich i serwerowych, aby rozpocząć sesję śledzenia ETW. Plik SetupETW.bat można znaleźć w folderze CS\Client.  
  
4. Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Po zakończeniu próbkowania uruchom cleanupetw.bat, aby zakończyć tworzenie pliku ETWTracingSampleLog.etl.  
  
6. Otwórz plik ETWTracingSampleLog.etl z poziomu przeglądarki śledzenia usług. Zostanie wyświetlony monit o zapisanie pliku w formacie binarnym jako pliku .svclog.  
  
7. Otwórz nowo utworzony plik .svclog z poziomu przeglądarki śledzenia usług, aby wyświetlić ślady ETW i ServiceModel.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>Zobacz też

- [Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
