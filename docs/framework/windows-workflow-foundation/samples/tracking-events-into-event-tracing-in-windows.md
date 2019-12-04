---
title: Zdarzenia śledzenia do śledzenia zdarzeń w systemie Windows
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: fe50476eedef505258c2e6818e75a32c06ed6fa6
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715930"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a>Zdarzenia śledzenia do śledzenia zdarzeń w systemie Windows

W tym przykładzie pokazano, jak włączyć śledzenie Windows Workflow Foundation (WF) w usłudze przepływu pracy i emitować zdarzenia śledzenia w usłudze śledzenie zdarzeń systemu Windows (ETW). Aby emitować rekordy śledzenia przepływu pracy do funkcji ETW, przykład używa uczestnika śledzenia ETW (<xref:System.Activities.Tracking.EtwTrackingParticipant>).

Przepływ pracy w przykładzie odbiera żądanie, przypisuje odwrotność danych wejściowych do zmiennej wejściowej i Zwraca odwrotność z powrotem do klienta. Gdy dane wejściowe mają wartość 0, wystąpi wyjątek dzielenia przez zero, który jest nieobsługiwany, który powoduje przerwanie przepływu pracy. Po włączeniu śledzenia rekord śledzenia błędów jest emitowany do funkcji ETW, co może pomóc w późniejszym rozwiązaniu błędu. Uczestnik śledzenia ETW jest skonfigurowany przy użyciu profilu śledzenia w celu subskrybowania śledzenia rekordów. Profil śledzenia jest zdefiniowany w pliku Web. config i podany jako parametr konfiguracji uczestnika śledzenia ETW. Uczestnik śledzenia funkcji ETW jest skonfigurowany w pliku Web. config usługi przepływu pracy i jest stosowany do usługi jako zachowanie usługi. W tym przykładzie przeglądasz zdarzenia śledzenia w dzienniku zdarzeń przy użyciu Podgląd zdarzeń.

## <a name="workflow-tracking-details"></a>Szczegóły śledzenia przepływu pracy

Windows Workflow Foundation udostępnia infrastrukturę śledzenia do śledzenia wykonywania wystąpienia przepływu pracy. Środowisko uruchomieniowe śledzenia tworzy wystąpienie przepływu pracy do emisji zdarzeń związanych z cyklem życia przepływu pracy, zdarzeniami z działań przepływu pracy i zdarzeniami niestandardowymi. W poniższej tabeli przedstawiono podstawowe składniki infrastruktury śledzenia.

|Składnik|Opis|
|---------------|-----------------|
|Śledzenie środowiska uruchomieniowego|Udostępnia infrastrukturę do emisji rekordów śledzenia.|
|Śledzenie uczestników|Uzyskuje dostęp do rekordów śledzenia. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] dostarcza uczestnika śledzenia, który zapisuje rekordy śledzenia jako zdarzenia śledzenia zdarzeń systemu Windows (ETW).|
|Profil śledzenia|Mechanizm filtrowania umożliwiający uczestnikom śledzenia subskrybowanie podzbioru rekordów śledzenia emitowanych z wystąpienia przepływu pracy.|

W poniższej tabeli przedstawiono szczegółowe informacje o rekordach śledzenia, które są emitowane przez środowisko uruchomieniowe przepływu pracy.

|Rekord śledzenia|Opis|
|---------------------|-----------------|
|Rekordy śledzenia wystąpienia przepływu pracy.|Opisuje cykl życia wystąpienia przepływu pracy. Na przykład rekord wystąpienia jest emitowany, gdy przepływ pracy zostanie uruchomiony lub zakończony.|
|Rekordy śledzenia stanu działania.|Szczegóły wykonywania działania. Te rekordy wskazują stan działania przepływu pracy, np. Kiedy działanie zostało zaplanowane lub gdy działanie zostało zakończone lub gdy zostanie zgłoszony błąd.|
|Rekord wznowienia zakładki.|Emitowane za każdym razem, gdy zostanie wznowiona Zakładka w wystąpieniu przepływu pracy.|
|Niestandardowe rekordy śledzenia.|Autor przepływu pracy może tworzyć niestandardowe rekordy śledzenia i emitować je w ramach działania niestandardowego.|
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|Ten rekord jest emitowany, gdy działanie zaplanuje inne działanie.|
|<xref:System.Activities.Tracking.FaultPropagationRecord>|Ten rekord jest emitowany, gdy błąd jest propagowany z działania.|
|<xref:System.Activities.Tracking.CancelRequestedRecord>|Ten rekord jest emitowany, gdy działanie zostało anulowane przez inne działanie.|

Uczestnik śledzenia subskrybuje podzestaw wyemitowanych rekordów śledzenia przy użyciu profilów śledzenia. Profil śledzenia zawiera kwerendy śledzenia, które umożliwiają subskrybowanie określonego typu rekordu śledzenia. Profile śledzenia można określić w kodzie lub w konfiguracji.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania EtwTrackingParticipantSample. sln.

2. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

3. Aby uruchomić rozwiązanie, naciśnij klawisz F5.

    Domyślnie usługa nasłuchuje na porcie 53797 (http://localhost:53797/SampleWorkflowService.xamlx).

4. Korzystając z Eksploratora plików, Otwórz klienta testowego WCF.

    Klient testowy WCF (WcfTestClient. exe) znajduje się w folderze \<instalacyjnym programu Visual Studio 2010 > folderze \Common7\IDE\.

    Domyślny folder instalacji programu Visual Studio 2010 to C:\Program Files\Microsoft Visual Studio 10,0.

5. W kliencie testowym WCF wybierz pozycję **Dodaj usługę** z menu **plik** .

    Dodaj adres punktu końcowego w polu wejściowym. Wartość domyślna to `http://localhost:53797/SampleWorkflowService.xamlx`.

6. Otwórz aplikację Podgląd zdarzeń.

    Przed wywołaniem usługi Uruchom Podgląd zdarzeń z menu **Start** , wybierz polecenie **Uruchom** i wpisz w `eventvwr.exe`. Upewnij się, że dziennik zdarzeń nasłuchuje zdarzeń śledzenia emitowanych z usługi przepływu pracy.

7. W widoku drzewa Podgląd zdarzeń przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**oraz **firmę Microsoft**. Kliknij prawym przyciskiem myszy pozycję **Microsoft** i wybierz pozycję **Widok** , a następnie **Pokaż dzienniki analityczne i debugowania** , aby włączyć dzienniki analityczne i debugowania.

    Upewnij się, że jest zaznaczona opcja **Pokaż dzienniki analityczne i debugowania** .

8. W widoku drzewa w Podgląd zdarzeń przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **serwer aplikacji-aplikacje**. Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz pozycję **Włącz dziennik** , aby włączyć dziennik **analityczny** .

9. Przetestuj usługę przy użyciu klienta testowego WCF przez dwukrotne kliknięcie `GetData`.

    Spowoduje to otwarcie metody `GetData`. Żądanie akceptuje jeden parametr i zapewnia, że wartość jest równa 0, co jest ustawieniem domyślnym.

     Kliknij pozycję **Wywołaj**.

10. Obserwuj zdarzenia emitowane z przepływu pracy.

    Wróć do Podgląd zdarzeń i przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **serwer aplikacji-aplikacje**. Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz polecenie **Odśwież**.

    Zdarzenia przepływu pracy są wyświetlane w Podglądzie zdarzeń. Zwróć uwagę, że są wyświetlane zdarzenia wykonywania przepływu pracy, a jeden z nich jest nieobsługiwanym wyjątek, który odnosi się do błędu w przepływie pracy. Ponadto zdarzenie ostrzegawcze jest emitowane z działania przepływu pracy, co oznacza, że działanie zgłasza błąd.

11. Powtórz kroki 9 i 10 przy użyciu danych wejściowych innych niż 0, aby nie zgłaszać błędów.

Profile śledzenia umożliwiają subskrybowanie zdarzeń, które są emitowane przez środowisko uruchomieniowe po zmianie stanu wystąpienia przepływu pracy. W zależności od wymagań dotyczących monitorowania można utworzyć profil, który jest bardzo duży, który subskrybuje niewielki zestaw zmian stanu wysokiego poziomu w przepływie pracy. Z drugiej strony można utworzyć bardzo precyzyjny profil, którego dane wyjściowe są wystarczająco rozbudowane, aby odtworzyć wykonywanie później. Przykład pokazuje zdarzenia emitowane przez środowisko uruchomieniowe przepływu pracy do funkcji ETW przy użyciu `HealthMonitoring Tracking Profile`, które emitują mały zestaw zdarzeń. Inny profil, który emituje więcej zdarzeń śledzenia przepływu pracy, jest również dostępny w pliku Web. config o nazwie `Troubleshooting Tracking Profile`. Po zainstalowaniu [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] w pliku Machine. config zostanie skonfigurowany profil domyślny o pustej nazwie. Ten profil jest używany przez konfigurację zachowania śledzenia funkcji ETW, gdy nie określono nazwy profilu lub pustej nazwy profilu.

Profil śledzenia monitorowania kondycji emituje rekordy wystąpień przepływu pracy i rekordy propagacji błędów aktywności. Ten profil jest tworzony przez dodanie następującego profilu śledzenia do pliku konfiguracji Web. config.

```xml
<tracking>
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

 Profil można zmienić, zmieniając konfigurację `EtwTrackingParticipant` w następujący sposób.

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <etwTracking profileName="HealthMonitoring Tracking Profile"/>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

#### <a name="to-clean-up-optional"></a>Aby oczyścić (opcjonalnie)

1. Otwórz Podgląd zdarzeń.

2. Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **serwer aplikacji — aplikacje**. Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz polecenie **Wyłącz dziennik**.

3. Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **serwer aplikacji — aplikacje**. Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz pozycję **Wyczyść dziennik**.

4. Wybierz opcję **Wyczyść** , aby wyczyścić zdarzenia.

## <a name="known-issue"></a>Znany problem

> [!NOTE]
> Istnieje znany problem w Podgląd zdarzeń, w którym może nie można zdekodować zdarzeń ETW. Może pojawić się komunikat o błędzie, który wygląda podobnie do poniższego.
>
> Nie można znaleźć opisu identyfikatora zdarzenia \<identyfikator > ze źródła Microsoft-Windows-Application Server-Applications. Składnik, który wywołuje to zdarzenie, nie jest zainstalowany na komputerze lokalnym lub instalacja jest uszkodzona. Można zainstalować lub naprawić składnik na komputerze lokalnym.
>
> Jeśli ten błąd wystąpi, kliknij przycisk Odśwież w okienku Akcje. Zdarzenie powinno teraz zostać zdekodowane poprawnie.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`

## <a name="see-also"></a>Zobacz także

- [Przykłady monitorowania oprogramowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
