---
title: Śledzenie zdarzeń do zdarzenia śledzenia w systemie Windows
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: 82de8ee74c12019f815adc63f2ca4441ad95d325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519509"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a>Śledzenie zdarzeń do zdarzenia śledzenia w systemie Windows
W tym przykładzie pokazano, jak włączyć śledzenie usługi przepływu pracy Windows Workflow Foundation (WF), a emisją zdarzeń śledzenia w funkcji Śledzenie zdarzeń systemu Windows (). Aby emitować śledzenia rekordów do ETW przepływu pracy, próbki używa uczestnika śledzenia zdarzeń systemu Windows (<xref:System.Activities.Tracking.EtwTrackingParticipant>).  
  
 Przepływ pracy w próbce odbiera żądanie, przypisuje odwrotność danych wejściowych do wprowadzania zmiennej i zwraca wzajemnego wstecz do klienta. Gdy dane wejściowe to 0, dzielenie przez zero wyjątek występuje nieobsługiwany który powoduje, że przepływ pracy do przerwania. Z włączonym śledzeniem, błąd Śledź rekord jest emitowany do funkcji ETW, co może pomóc rozwiązać problem później. Uczestnik śledzenia zdarzeń systemu Windows jest skonfigurowany przy użyciu profilu śledzenia, aby subskrybować śledzenie rekordów. Profil śledzenia jest zdefiniowana w pliku Web.config i podać jako parametr konfiguracji do uczestnika śledzenia zdarzeń systemu Windows. Uczestnik śledzenia zdarzeń systemu Windows jest skonfigurowany w pliku Web.config usługi przepływu pracy i zastosowano je do usługi jako zachowanie usługi. W tym przykładzie można wyświetlać zdarzenia śledzenia w dzienniku zdarzeń za pomocą Podglądu zdarzeń.  
  
## <a name="workflow-tracking-details"></a>Szczegóły śledzenia przepływu pracy  
 Windows Workflow Foundation udostępnia infrastrukturę śledzenia śledzić wystąpienia przepływu pracy. Środowisko uruchomieniowe śledzenia tworzy wystąpienie przepływu pracy do wysyłania zdarzeń związanych z cyklem życia przepływu pracy, zdarzenia z działań przepływu pracy i zdarzeń niestandardowych. W poniższej tabeli przedstawiono podstawowe składniki infrastruktury śledzenia.  
  
|Składnik|Opis|  
|---------------|-----------------|  
|Śledzenie czasu wykonywania|Zapewnia infrastrukturę do emisji rekordów śledzenia.|  
|Uczestników śledzenia|Uzyskuje dostęp do rekordów śledzenia. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] jest dostarczany z uczestnika śledzenia, który zapisuje rekordy śledzenia jako zdarzenia funkcji Śledzenie zdarzeń systemu Windows ().|  
|Profil śledzenia|Mechanizm filtrowania, który umożliwia śledzenie uczestnika do subskrybowania dla podzestawu rekordów śledzenia wyemitowanego z wystąpieniem przepływu pracy.|  
  
 W poniższej tabeli przedstawiono rekordy śledzenia emitowane środowiska uruchomieniowego przepływu pracy.  
  
|Rekord śledzenia|Opis|  
|---------------------|-----------------|  
|Rejestruje śledzenia wystąpienia przepływu pracy.|Informacje o cyklu życia wystąpienia przepływu pracy. Na przykład wystąpienia rekord jest emitowany podczas uruchamiania przepływu pracy, lub zakończy.|  
|Rejestruje śledzenia stanu działania.|Szczegóły wykonywania działania. Te rekordy wskazują stan działania przepływu pracy, takie jak kiedy zaplanowano działania lub po ukończeniu działania lub gdy zostanie zgłoszony błąd.|  
|Zakładki wznowienie rekordu.|Emitowane zawsze, gdy zostanie wznowione zakładki w ramach wystąpienia przepływu pracy.|  
|Śledzenie niestandardowych rekordów.|Autor przepływu pracy można utworzyć rekordy śledzenia niestandardowych i wysyłać je w ramach działania niestandardowego.|  
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|Ten rekord jest emitowany, gdy działanie planuje innego działania.|  
|<xref:System.Activities.Tracking.FaultPropagationRecord>|Ten rekord jest emitowany przy propagacji błąd z działania.|  
|<xref:System.Activities.Tracking.CancelRequestedRecord>|Ten rekord jest emitowany, gdy działanie zostało anulowane przez innego działania.|  
  
 Subskrybuje uczestnika śledzenia dla podzestawu rekordów emitowany śledzenia przy użyciu profilów śledzenia. Profil śledzenia zawiera śledzenia zapytań, które umożliwia subskrybowania śledzenia określonego typu rekordu. Śledzenie profile można określić w kodzie, lub w konfiguracji.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania EtwTrackingParticipantSample.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
     Domyślnie usługa nasłuchuje na porcie 53797 (http://localhost:53797/SampleWorkflowService.xamlx).  
  
4.  Przy użyciu [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], otwórz klienta testowego WCF.  
  
     Klienta testowego WCF (WcfTestClient.exe) znajduje się w \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder instalacji > \Common7\IDE\ folderu.  
  
     Wartość domyślna [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder instalacji to C:\Program Files\Microsoft Visual Studio 10.0.  
  
5.  W kliencie testowym WCF, wybierz **Dodaj usługę** z **pliku** menu.  
  
     Dodaj adres punktu końcowego w odpowiednim polu. Wartość domyślna to http://localhost:53797/SampleWorkflowService.xamlx.  
  
6.  Otwórz aplikację Podgląd zdarzeń.  
  
     Przed wywołaniem usługi, uruchomienie podglądu zdarzeń z **Start** menu, wybierz opcję **Uruchom** i wpisz `eventvwr.exe`. Upewnij się, że dziennik zdarzeń nasłuchuje śledzenia zdarzeń wyemitowanego z usługi przepływu pracy.  
  
7.  W widoku drzewa Podgląd zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, i **Microsoft**. Kliknij prawym przyciskiem myszy **Microsoft** i wybierz **widoku** , a następnie **dzienniki Pokaż analityczne i debugowania** włączyć analityczne i debugowania dzienników  
  
     Upewnij się, że **dzienniki Pokaż analityczne i debugowania** zaznaczenia pola wyboru.  
  
8.  W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik** umożliwiające **analityczne** dziennika.  
  
9. Testowanie usługi przy użyciu klienta testowego WCF, klikając dwukrotnie `GetData`.  
  
     Spowoduje to otwarcie `GetData` metody. Żądanie przyjmuje jeden parametr i zapewnia, że wartość wynosi 0, co jest ustawieniem domyślnym.  
  
     Kliknij przycisk **wywołania**.  
  
10. Sprawdź zdarzenia wysyłanego z przepływu pracy.  
  
     Wrócić do podglądu zdarzeń, a następnie przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Odśwież**.  
  
     Przepływ pracy zdarzenia są wyświetlane w Podglądzie zdarzeń. Zwróć uwagę, że są wyświetlane zdarzenia wykonywania przepływu pracy i że jeden z nich jest nieobsługiwany wyjątek odpowiadający błąd w przepływie pracy. Ponadto zdarzenie ostrzeżenia jest emitowany z działania przepływu pracy, co oznacza, że działanie jest zgłaszanie błędów.  
  
11. Powtórz kroki od 9 i Update 10 z wprowadzania danych innych niż 0, dzięki czemu jest zgłaszany błąd nie.  
  
 Profile śledzenia umożliwiają subskrybowanie zdarzeń, które są emitowane przez środowisko uruchomieniowe po zmianie stanu wystąpienia przepływu pracy. W zależności od wymagań monitorowania, można utworzyć profil, który jest przybliżonego, które subskrybuje niewielki zestaw zmian stanu ogólny przepływ pracy. Z drugiej strony można utworzyć profil bardzo dokładne, której wyjście jest zaawansowanych, aby odtworzyć wykonywania później. W przykładzie pokazano zdarzenia wyemitowanego z środowiska uruchomieniowego przepływu pracy przy użyciu funkcji ETW `HealthMonitoring Tracking Profile`, który emituje niewielki zestaw zdarzeń. Dostępne są również innego profilu, który emituje jeden przepływ pracy zdarzenia śledzenia w pliku Web.config, o nazwie `Troubleshooting Tracking Profile`. Gdy [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] jest zainstalowany, domyślny profil o pustej nazwie jest skonfigurowany w pliku Machine.config. Ten profil jest używany przez ETW śledzenia konfigurację zachowania, gdy brak nazwy profilu lub profilu pusta nazwa jest określona.  
  
 Monitorowania profilu śledzenia kondycji emituje rekordów wystąpienia przepływu pracy i działania błędów Propagacja rekordów. Ten profil jest tworzony przez dodanie następującego profilu śledzenia w pliku konfiguracji Web.config.  
  
```xml  
<<tracking>  
      <profiles>  
        <trackingProfile name="HealthMonitoring Tracking Profile">  
          <workflow activityDefinitionId="*">  
            <workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="Started"/>  
                  <state name="Completed"/>  
                  <state name="Aborted"/>  
                  <state name="UnhandledException"/>  
                </states>  
            </workflowInstanceQuery>  
           </workflowInstanceQueries>  
            <faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
            </faultPropagationQueries>  
          </workflow>  
        </trackingProfile>  
       </profiles>  
</tracking>  
```  
  
 Profil można zmienić, zmieniając `EtwTrackingParticipant` konfiguracji do następującego.  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="HealthMonitoring Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
#### <a name="to-clean-up-optional"></a>Aby wyczyścić (opcjonalnie)  
  
1.  Otwórz Podgląd zdarzeń.  
  
2.  Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji Aplikacje serwera**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **wyłączyć dziennika**.  
  
3.  Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji Aplikacje serwera**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Wyczyść dziennik**.  
  
4.  Wybierz **wyczyść** opcję, aby wyczyścić zdarzenia.  
  
## <a name="known-issue"></a>Znany problem  
  
> [!NOTE]
>  Istnieje znany problem w Podglądzie zdarzeń, jeżeli nie może zdekodować zdarzenia ETW. Może zostać wyświetlony komunikat błędu, który wygląda następująco.  
>   
>  Opisu Identyfikatora zdarzenia \<id > ze źródła nie można odnaleźć aplikacji serwera firmy Microsoft-Windows-aplikacji. Składnik, który wywołuje to zdarzenie nie jest zainstalowany na komputerze lokalnym albo instalacja jest uszkodzona. Można zainstalować lub naprawić składnik na komputerze lokalnym.  
>   
>  Jeśli wystąpi ten błąd, kliknij przycisk Odśwież w okienku Akcje. Zdarzenia powinny teraz dekodowania poprawnie.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
