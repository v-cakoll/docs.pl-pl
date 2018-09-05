---
title: Śledzenie za pomocą funkcji ETW
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 3e4dd141bd5f6a9d137b2fe981b3b412ec0c81e2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558374"
---
# <a name="etw-tracing"></a>Śledzenie za pomocą funkcji ETW
Ten przykład demonstruje sposób implementacji śledzenia End-to-End (E2E) przy użyciu śledzenie zdarzeń dla Windows (ETW) i `ETWTraceListener` która jest dostarczana z tego przykładu. Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) oraz śledzenie.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie przyjęto założenie, że czytelnik zna [śledzenia i rejestrowania komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Każde źródło śledzenia w <xref:System.Diagnostics> śledzenia model może mieć wiele obiektów nasłuchujących śledzenia, które określają, gdzie i w jaki sposób dane są śledzone. Typ odbiornika definiuje format, w którym dane śledzenia są rejestrowane. Poniższy przykład kodu pokazuje, jak dodać odbiornika do konfiguracji.  
  
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
  
 Przed rozpoczęciem korzystania z tego odbiornika można uruchomić sesji śledzenia zdarzeń systemu Windows. Za pomocą Logman.exe lub Tracelog.exe można uruchomić tej sesji. Plik SetupETW.bat jest dołączone do tego przykładu tak, aby skonfigurować sesję śledzenia funkcji ETW, wraz z plikiem CleanupETW.bat zamykania sesji i uzupełniania pliku dziennika.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu. Aby uzyskać więcej informacji o tych narzędziach zobacz [https://go.microsoft.com/fwlink/?LinkId=56580](https://go.microsoft.com/fwlink/?LinkId=56580)  
  
 Korzystając z ETWTraceListener, ślady są rejestrowane w plikach binarnych ETL. Z włączonym śledzeniem elementu ServiceModel jest włączone, wszystkie ślady wygenerowanego pojawiają się w tym samym pliku. Użyj [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) dotyczące wyświetlania plików dziennika ETL i .svclog. Podgląd tworzy widok end-to-end, co system, który pozwala na śledzenie komunikatów ze źródła do miejsca docelowego i punktem zużycia.  
  
 Odbiornik śledzenia zdarzeń systemu Windows obsługuje logowanie cykliczne. Aby włączyć tę funkcję, przejdź do **Start**, **Uruchom** i typ `cmd` można uruchomić konsoli poleceń. W poniższym poleceniu zastąp `<logfilename>` parametr o nazwie pliku dziennika.  
  
```  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 `-f` i `-max` przełączniki są opcjonalne. Odpowiednio określają format binarny cykliczne i maksymalny rozmiar dziennika z 1000MB. `-p` Przełącznik jest używany do określenia dostawcy śledzenia. W naszym przykładzie `"{411a0819-c24b-428c-83e2-26b41091702e}"` oznacza identyfikator GUID "Dostawcy próbki ETW XML".  
  
 Aby rozpocząć sesję, wpisz następujące polecenie.  
  
```  
Logman start Wcf  
```  
  
 Po zakończeniu rejestrowania można zatrzymać sesji za pomocą następującego polecenia.  
  
```  
Logman stop Wcf  
```  
  
 Ten proces generuje dzienniki cykliczne binarne, przetwarzających z narzędziem wyboru, w tym [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) lub Tracerpt.  
  
 Możesz również przejrzeć [śledzenie cykliczne](../../../../docs/framework/wcf/samples/circular-tracing.md) przykładowe więcej informacji na temat odbiornik alternatywne do wykonywania logowanie cykliczne.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Pamiętaj, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
    > [!NOTE]
    >  Aby użyć polecenia RegisterProvider.bat, SetupETW.bat i CleanupETW.bat, należy uruchomić przy użyciu konta administratora lokalnego. Jeśli używasz [!INCLUDE[wv](../../../../includes/wv-md.md)] lub nowszej, należy także uruchomić wiersz polecenia z podwyższonym poziomem uprawnień. Aby to zrobić, kliknij prawym przyciskiem myszy ikonę wiersza polecenia, a następnie kliknij przycisk **Uruchom jako administrator**.  
  
3.  Przed uruchomieniem przykładu, należy uruchomić RegisterProvider.bat na kliencie i serwerze. Spowoduje to utworzenie wynikowy plik ETWTracingSampleLog.etl do generowania danych śledzenia, które mogą być odczytywane przez przeglądarki danych śledzenia usługi. Ten plik można znaleźć w folderze C:\logs. Jeśli ten folder nie istnieje, musi ona zostać utworzona, lub są generowane nie dane śledzenia. Następnie uruchom SetupETW.bat na komputerach klienta i serwera, aby rozpocząć sesję śledzenia funkcji ETW. Plik SetupETW.bat znajdują się w folderze CS\Client.  
  
4.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Po ukończeniu próbki, należy uruchomić CleanupETW.bat, aby zakończyć tworzenie pliku ETWTracingSampleLog.etl.  
  
6.  Otwórz plik ETWTracingSampleLog.etl z w ramach przeglądarki danych śledzenia usługi. Zostanie wyświetlony monit Zapisz plik binarny sformatowane jako plik .svclog.  
  
7.  Otwórz plik .svclog nowo utworzony z w ramach przeglądarki danych śledzenia usługi do wyświetlania śladów funkcji ETW i ServiceModel.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
