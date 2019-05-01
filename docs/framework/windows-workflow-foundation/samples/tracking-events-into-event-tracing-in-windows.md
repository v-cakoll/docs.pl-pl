---
title: Zdarzenia śledzenia do śledzenia zdarzeń w systemie Windows
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: 129b82da068251d87bd9b0ca029b7e5a1c274936
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004812"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a>Zdarzenia śledzenia do śledzenia zdarzeń w systemie Windows
W tym przykładzie pokazano, jak włączyć śledzenie usługi przepływu pracy Windows Workflow Foundation (WF) i emitować zdarzenia śledzenia w śledzenie zdarzeń dla Windows (ETW). Aby emitować śledzenia rekordów do ETW przepływu pracy, w przykładzie użyto uczestnika śledzenia zdarzeń systemu Windows (<xref:System.Activities.Tracking.EtwTrackingParticipant>).

 Przepływ pracy w próbce odbiera żądanie, przypisuje zmienna wejściowa odwrotność dane wejściowe i zwraca wzajemnego wstecz do klienta. W przypadku danych wejściowych wynosi 0, dzielenie przez zero wyjątek wystąpi jest nieobsługiwany, powoduje, że przepływ pracy, aby przerwać. Z włączoną funkcją śledzenia, błąd rekord śledzenia jest emitowane zdarzeń systemu Windows, które mogą pomóc rozwiązać błąd później. Uczestnika śledzenia zdarzeń systemu Windows jest skonfigurowany z profil śledzenia do subskrybowania śledzenie rekordów. Profil śledzenia jest zdefiniowane w pliku Web.config i przekazana jako parametr konfiguracji do uczestnika śledzenia zdarzeń systemu Windows. Uczestnika śledzenia zdarzeń systemu Windows jest skonfigurowany w pliku Web.config usługi przepływu pracy i jest stosowana do usługi jako zachowanie usługi. W tym przykładzie możesz wyświetlić zdarzenia śledzenia w dzienniku zdarzeń za pomocą Podglądu zdarzeń.

## <a name="workflow-tracking-details"></a>Szczegóły śledzenia przepływu pracy
 Windows Workflow Foundation udostępnia infrastrukturę śledzenia do śledzenia wykonywania wystąpienia przepływu pracy. Środowisko uruchomieniowe śledzenia tworzy wystąpienie przepływu pracy, aby emitować zdarzenia związane z cyklem życia przepływu pracy, zdarzenia z działań przepływu pracy i zdarzeń niestandardowych. W poniższej tabeli przedstawiono podstawowe składniki infrastruktury śledzenia.

|Składnik|Opis|
|---------------|-----------------|
|Śledzenie czasu wykonywania|Zapewnia infrastrukturę, aby emitować rekordów śledzenia.|
|Uczestnicy śledzenia|Uzyskuje dostęp do rekordów śledzenia. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] dostarczany z śledzenia uczestnika, który zapisuje rekordy śledzenia jako zdarzenia śledzenie zdarzeń dla Windows (ETW).|
|Profil śledzenia|Mechanizm filtrowania, który umożliwia śledzenia uczestnika do subskrybowania dla podzbioru rekordów śledzenia emitowane z wystąpienia przepływu pracy.|

 W poniższej tabeli przedstawiono rekordów śledzenia emitowane przez środowisko wykonawcze przepływów pracy.

|Rekord śledzenia|Opis|
|---------------------|-----------------|
|Rekordy śledzenia wystąpienia przepływu pracy.|W tym artykule opisano cyklu życia wystąpienia przepływu pracy. Na przykład rekord wystąpienia jest emitowane, gdy przepływ pracy rozpoczyna się lub kończy.|
|Rekordy śledzenia stanu działania.|Szczegóły wykonania działania. Te informacje wskazują stan działania przepływu pracy, takie jak kiedy zaplanowano działania lub po zakończeniu działania lub kiedy zostanie wygenerowany błąd.|
|Zakładki wznowienie rekordów.|Emitowane przy każdym zakładki w ramach wystąpienie przepływu pracy zostanie wznowione.|
|Niestandardowe rekordy śledzenia.|Tworzenie przepływu pracy można utworzyć niestandardowe rekordy śledzenia i emitować je w ramach działania niestandardowego.|
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|Ten rekord jest emitowane, gdy działanie planuje innego działania.|
|<xref:System.Activities.Tracking.FaultPropagationRecord>|Ten rekord jest emitowane po awarii jest propagowana na podstawie działania.|
|<xref:System.Activities.Tracking.CancelRequestedRecord>|Ten rekord jest emitowane, gdy działanie zostało anulowane przez innego działania.|

 Subskrybuje uczestnika śledzenia dla podzbioru rekordów śledzenia emitowany przy użyciu profilów śledzenia. Profil śledzenia zawiera śledzenia zapytań, zezwalających na subskrypcji dla śledzenia określonego typu rekordu. Śledzenie profile można określić w kodzie lub w konfiguracji.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2010, otwórz plik rozwiązania EtwTrackingParticipantSample.sln.

2. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

3. Aby uruchomić rozwiązanie, naciśnij klawisz F5.

     Domyślnie usługa nasłuchuje na porcie 53797 (http://localhost:53797/SampleWorkflowService.xamlx).

4. Za pomocą [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], otwórz klienta testowego WCF.

     Testowy klient WCF (WcfTestClient.exe) znajduje się w \<folder instalacji programu Visual Studio 2010 > \Common7\IDE\ folderu.

     Domyślny folder instalacji programu Visual Studio 2010 to C:\Program Files\Microsoft Visual Studio 10.0.

5. W kliencie testowym WCF, wybierz **Dodaj usługę** z **pliku** menu.

     W polu wejściowym, należy dodać adres punktu końcowego. Wartość domyślna to `http://localhost:53797/SampleWorkflowService.xamlx`.

6. Otwórz aplikację Podgląd zdarzeń.

     Przed wywołaniem usługi, Uruchom Podgląd zdarzeń z **Start** menu, wybierz opcję **Uruchom** i wpisz w polu `eventvwr.exe`. Upewnij się, czy w dzienniku zdarzeń nasłuchuje dla śledzenia zdarzeń wysyłanego z usługi przepływu pracy.

7. W widoku drzewa w Podglądzie zdarzeń przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, i **Microsoft**. Kliknij prawym przyciskiem myszy **Microsoft** i wybierz **widoku** i następnie **Pokaż analityczne i debugowania dzienniki** Włącz analityczne i debugowania dzienniki

     Upewnij się, że **Pokaż analityczne i debugowania dzienniki** opcja jest zaznaczona.

8. W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik** umożliwiające **analityczne** dziennika.

9. Testowanie usługę za pomocą klienta testowego WCF, klikając dwukrotnie plik `GetData`.

     Spowoduje to otwarcie `GetData` metody. Żądanie przyjmuje jeden parametr i gwarantuje, że wartość wynosi 0, co jest ustawieniem domyślnym.

     Kliknij przycisk **wywołania**.

10. Sprawdź zdarzenia emitowane z przepływu pracy.

     Przejdź z powrotem do programu Podgląd zdarzeń i przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Odśwież**.

     Zdarzenia przepływu pracy są wyświetlane w Podglądzie zdarzeń. Zwróć uwagę, że są wyświetlane zdarzenia wykonywania przepływu pracy i że jeden z nich jest nieobsługiwany wyjątek, który odpowiada błędowi w przepływie pracy. Ponadto to zdarzenie ostrzegawcze są emitowane z działania przepływu pracy, co oznacza, że działanie zgłasza błąd.

11. Powtórz kroki 9 i 10 przy użyciu danych wejściowych, danych innych niż 0, tak, aby żaden błąd nie jest zgłaszany.

 Profile śledzenia pozwalają do subskrybowania zdarzenia, które są emitowane przez środowisko uruchomieniowe, po zmianie stanu wystąpienia przepływu pracy. W zależności od wymagań dotyczących monitorowania, można utworzyć profil przybliżonego, które subskrybuje niewielkiego zestawu zmian stanu wysokiego poziomu w przepływie pracy. Z drugiej strony można utworzyć bardzo dokładne profilu, którego dane wyjściowe są rozbudowanych, odtworzenie wykonywania później. W przykładzie pokazano zdarzeniach emitowane przez środowisko wykonawcze przepływów pracy za pomocą funkcji ETW `HealthMonitoring Tracking Profile`, który emituje niewielki zestaw zdarzeń. Inny profil, który emituje więcej śledzenia zdarzeń przepływu pracy jest również udostępniany w pliku Web.config, który nosi nazwę `Troubleshooting Tracking Profile`. Gdy [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] jest zainstalowany, domyślny profil z pustą nazwą jest skonfigurowany w pliku Machine.config. Ten profil jest używany przez ETW śledzenia konfiguracji zachowanie, gdy określona jest Brak nazwy profilu lub nazwę pusty profil.

 Monitorowania profilu śledzenia kondycji emituje aktywności błędów propagacji rekordów i rekordów wystąpienia przepływu pracy. Ten profil jest tworzony, dodając poniższy profil śledzenia do pliku konfiguracji Web.config.

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

 Profil, który można zmienić, zmieniając `EtwTrackingParticipant` konfiguracji do następującego.

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

1. Otwórz Podgląd zdarzeń.

2. Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji Aplikacje serwera**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **wyłączanie dziennika**.

3. Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji Aplikacje serwera**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Wyczyść dziennik**.

4. Wybierz **wyczyść** możliwość wyczyszczenia zdarzeń.

## <a name="known-issue"></a>Znany problem

> [!NOTE]
>  Istnieje znany problem w Podglądzie zdarzeń, gdzie może nie zdekodować zdarzenia ETW. Zobaczysz komunikat o błędzie, który wygląda podobnie do poniższego.
>
>  Opis zdarzenia o identyfikatorze \<id > ze źródła, nie można odnaleźć aplikacji serwera firmy Microsoft-Windows-aplikacji. Składnik, który wywołuje to zdarzenie nie jest zainstalowany na komputerze lokalnym albo instalacja jest uszkodzona. Można zainstalować lub naprawić składnik na komputerze lokalnym.
>
>  Jeśli wystąpi ten błąd, kliknij przycisk Odśwież, w okienku Akcje. Zdarzenia powinny teraz poprawnie dekodowane.

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady monitorowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
