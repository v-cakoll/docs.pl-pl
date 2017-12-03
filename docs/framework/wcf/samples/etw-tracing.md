---
title: "Śledzenie za pomocą funkcji ETW"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ebffd082f5d1b07ab016c0e5e72d6ad23542147
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="etw-tracing"></a>Śledzenie za pomocą funkcji ETW
W tym przykładzie pokazano, jak wdrożyć śledzenia End-to-End (E2E) przy użyciu zdarzenia śledzenia dla systemu Windows (ETW) i `ETWTraceListener` dostarczanym z tego przykładu. Próbki jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i obejmuje śledzenia zdarzeń systemu Windows.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie przyjęto założenie, że czytelnik zna [śledzenie i rejestrowanie komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Każde źródło śledzenia w <xref:System.Diagnostics> śledzenie model może mieć wiele obiektów nasłuchujących śledzenia, które określają, jak i gdzie dane są śledzone. Typ odbiornika definiuje format, w którym rejestrowane są dane śledzenia. Poniższy przykładowy kod przedstawia sposób Dodaj do konfiguracji odbiornika.  
  
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
  
 Przed użyciem tego odbiornika, można uruchomić sesję śledzenia funkcji ETW. Za pomocą Logman.exe lub Tracelog.exe można uruchomić tej sesji. Plik SetupETW.bat jest uwzględniona w tym przykładzie, dzięki czemu możesz skonfigurować sesję śledzenia funkcji ETW wraz z plikiem CleanupETW.bat zamykania sesji i uzupełniania w pliku dziennika.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu. Aby uzyskać więcej informacji na temat tych narzędzi, zobacz [http://go.microsoft.com/fwlink/?LinkId=56580](http://go.microsoft.com/fwlink/?LinkId=56580)  
  
 Używając ETWTraceListener, dane śledzenia są rejestrowane w plikach binarnych ETL. Z włączonym śledzeniem ServiceModel jest włączona, wszystkie ślady generowane są wyświetlane w tym samym pliku. Użyj [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) dotyczące wyświetlania plików dziennika ETL i .svclog. Podgląd komunikatów o tworzy widok end-to-end systemu, dzięki któremu można wyśledzić komunikatu od źródła do miejsca docelowego i punktem zużycia.  
  
 Odbiornik śledzenia zdarzeń systemu Windows obsługuje logowanie cykliczne. Aby włączyć tę funkcję, przejdź do **Start**, **Uruchom** i typ `cmd` można uruchomić konsoli poleceń. W poniższym poleceniu zastąp `<logfilename>` parametr o nazwie pliku dziennika.  
  
```  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 `-f` i `-max` przełączniki są opcjonalne. Określa format binarny cykliczne i dziennika maksymalny rozmiar 1000MB odpowiednio. `-p` Przełącznik jest używany do określenia dostawcy śledzenia. W naszym przykładzie `"{411a0819-c24b-428c-83e2-26b41091702e}"` oznacza identyfikator GUID "Dostawcy próbki ETW XML".  
  
 Aby rozpocząć sesję, wpisz następujące polecenie.  
  
```  
Logman start Wcf  
```  
  
 Po zakończeniu rejestrowania, można zatrzymać sesji przy użyciu następującego polecenia.  
  
```  
Logman stop Wcf  
```  
  
 Ten proces generuje dzienniki cyklicznych binarne, przetwarzające z narzędziem wyboru, w tym [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) lub Tracerpt.  
  
 Można również przejrzeć [śledzenie cykliczne](../../../../docs/framework/wcf/samples/circular-tracing.md) przykładowa uzyskać więcej informacji o alternatywnych odbiornika przeprowadzić logowanie cykliczne.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Pamiętaj, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
    > [!NOTE]
    >  Aby używać poleceń RegisterProvider.bat, SetupETW.bat i CleanupETW.bat, należy uruchomić przy użyciu konta administratora lokalnego. Jeśli używasz [!INCLUDE[wv](../../../../includes/wv-md.md)] lub później, należy także uruchomić wiersz polecenia z podwyższonym poziomem uprawnień. Aby to zrobić, kliknij prawym przyciskiem myszy ikonę wiersz polecenia, a następnie kliknij przycisk **Uruchom jako administrator**.  
  
3.  Przed uruchomieniem próbki, należy uruchomić RegisterProvider.bat na kliencie i serwerze. Wynikowy plik ETWTracingSampleLog.etl to konfiguruje do generowania danych śledzenia, które mogą być odczytywane przez Podgląd śledzenia usługi. Ten plik znajduje się w folderze C:\logs. Jeśli ten folder nie istnieje, należy utworzyć lub są generowane nie dane śledzenia. Następnie uruchom SetupETW.bat na komputery klienckie i serwery, aby rozpocząć sesję śledzenia funkcji ETW. Plik SetupETW.bat znajduje się w folderze CS\Client.  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Po zakończeniu próbki, należy uruchomić CleanupETW.bat, aby zakończyć tworzenie pliku ETWTracingSampleLog.etl.  
  
6.  Otwórz plik ETWTracingSampleLog.etl od w podglądzie śledzenia usługi. Pojawi się monit można zapisać pliku binarnego sformatowane jako plik .svclog.  
  
7.  Otworzyć plik .svclog nowo utworzonego w ramach podglądu śledzenia usługi, aby wyświetlić dane śledzenia zdarzeń systemu Windows i ServiceModel.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
