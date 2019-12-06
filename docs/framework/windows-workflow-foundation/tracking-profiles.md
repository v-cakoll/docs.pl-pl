---
title: Profile śledzenia
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 9217f25ba4499e7ff75020642be387aa79ba27bf
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837626"
---
# <a name="tracking-profiles"></a>Profile śledzenia

Profile śledzenia zawierają zapytania śledzenia umożliwiające uczestnikom śledzenia subskrybowanie zdarzeń przepływu pracy, które są emitowane w przypadku zmiany stanu wystąpienia przepływu pracy w czasie wykonywania.

## <a name="tracking-profiles"></a>Profile śledzenia

Profile śledzenia służą do określania, które informacje o śledzeniu są emitowane dla wystąpienia przepływu pracy. Jeśli profil nie zostanie określony, zostaną wyemitowane wszystkie zdarzenia śledzenia. Jeśli określono profil, zdarzenia śledzenia określone w profilu będą emitowane. W zależności od wymagań dotyczących monitorowania można napisać profil, który jest bardzo ogólny, który subskrybuje niewielki zestaw zmian stanu wysokiego poziomu w przepływie pracy. Z drugiej strony można utworzyć bardzo szczegółowy profil, którego zdarzenia są wystarczająco rozbudowane w celu późniejszego odtworzenia szczegółowego przepływu wykonania.

Śledzenie profilów jako elementów XML w standardowym pliku konfiguracji .NET Framework lub określonych w kodzie. Poniższy przykład dotyczy profilu śledzenia [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] w pliku konfiguracji, który umożliwia uczestnikom śledzenia subskrybowanie `Started` i `Completed` zdarzeń przepływu pracy.

```xml
<system.serviceModel>
    ...
    <tracking>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started"/>
                <state name="Completed"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
    ...
</system.serviceModel>
```

Poniższy przykład przedstawia odpowiedni profil śledzenia utworzony przy użyciu kodu.

```csharp
TrackingProfile profile = new TrackingProfile()
{
    Name = "CustomTrackingProfile",
    Queries =
    {
        new WorkflowInstanceQuery()
        {
            // Limit workflow instance tracking records for started and
            // completed workflow states.
            States = { WorkflowInstanceStates.Started, WorkflowInstanceStates.Completed },
        }
    }
};
```

Rekordy śledzenia są filtrowane przez tryb widoczności w profilu śledzenia przy użyciu atrybutu <xref:System.Activities.Tracking.ImplementationVisibility>. Działanie złożone to działanie najwyższego poziomu, które zawiera inne działania, które tworzą jego implementację. Tryb widoczności określa rekordy śledzenia emitowane z działań złożonych w ramach działania przepływu pracy, aby określić, czy działania tworzące implementację są śledzone. Tryb widoczności dotyczy poziomu profilu śledzenia. Filtrowanie rekordów śledzenia dla poszczególnych działań w ramach przepływu pracy jest kontrolowane przez zapytania w ramach profilu śledzenia. Aby uzyskać więcej informacji, zobacz sekcję **śledzenie typów zapytań profilu** w tym dokumencie.

Dwa tryby widoczności określone przez atrybut `implementationVisibility` w profilu śledzenia są `RootScope` i `All`. Użycie trybu `RootScope` powoduje pominięcie rekordów śledzenia dla działań, które tworzą implementację działania w przypadku, gdy działanie złożone nie jest elementem głównym przepływu pracy. Oznacza to, że gdy działanie zaimplementowane przy użyciu innych działań jest dodawane do przepływu pracy, a `implementationVisibility` ustawiona na RootScope, śledzone jest tylko działanie najwyższego poziomu w ramach tego działania złożonego. Jeśli działanie jest elementem głównym przepływu pracy, implementacja działania jest przepływem pracy, a śledzone rekordy są emitowane dla działań, które tworzą implementację. Użycie trybu All zezwala na emisję wszystkich rekordów śledzenia dla działania głównego i wszystkich jego działań złożonych.

Na przykład załóżmy, że *działanie to złożone działanie,* którego implementacja zawiera dwa działania, *zakończeniu* i *Activity2*. Gdy to działanie jest dodawane do przepływu pracy, a funkcja śledzenia jest włączona z profilem śledzenia o `implementationVisibility` ustawionym na `RootScope`, śledzenie rekordów jest emitowane tylko dla *działania*. Jednak żadne rekordy nie są emitowane dla działań *zakończeniu* i *Activity2*.

Jeśli jednak atrybut `implementationVisibility` dla profilu śledzenia jest ustawiony na `All`, to śledzenie rekordów jest emitowane nie tylko dla *akcji moje działanie*, ale również dla działań *zakończeniu* i *Activity2*.

Flaga `implementationVisibility` ma zastosowanie do następujących typów rekordów śledzenia:

- ActivityStateRecord

- FaultPropagationRecord

- CancelRequestedRecord

- ActivityScheduledRecord

> [!NOTE]
> CustomTrackingRecords emitowane z implementacji działania nie są filtrowane przez ustawienie implementationVisibility.

Funkcja `implementationVisibility` jest określana jako <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> w profilu śledzenia w kodzie w następujący sposób:

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

Funkcja `implementationVisibility` jest określona jako <xref:System.Activities.Tracking.ImplementationVisibility.All> w profilu śledzenia w pliku konfiguracji w następujący sposób:

```xml
<tracking>
      <profiles>
        <trackingProfile name="Shipping Monitoring" implementationVisibility="All">
          <workflow activityDefinitionId="*">
...
         </workflow>
        </trackingProfile>
      </profiles>
</tracking>
```

Ustawienie `ImplementationVisibility` profilu śledzenia jest opcjonalne. Domyślnie wartość jest ustawiona na `RootScope`. W wartościach tego atrybutu rozróżniana jest wielkość liter.

### <a name="tracking-profile-query-types"></a>Typy zapytań profilu śledzenia

Profile śledzenia mają strukturę jako deklaratywne subskrypcji dla śledzenia rekordy, które umożliwiają zapytania dla rekordów śledzenie wersję wykonawczą przepływu pracy. Istnieje kilka typów zapytań, które umożliwiają subskrybowanie różnych klas obiektów <xref:System.Activities.Tracking.TrackingRecord>. Profile śledzenia można określić w obszarze Konfiguracja lub za poorednictwem kodu. Oto najpopularniejsze typy zapytań:

- <xref:System.Activities.Tracking.WorkflowInstanceQuery> — Użyj tego do śledzenia zmian cyklu życia wystąpienia przepływu pracy, takich jak wcześniej zademonstrowane `Started` i `Completed`. <xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  Stany, do których można subskrybować, są określone w klasie <xref:System.Activities.Tracking.WorkflowInstanceStates>.

  W poniższym przykładzie przedstawiono konfigurację lub kod służący do subskrybowania rekordów śledzenia na poziomie wystąpienia przepływu pracy dla `Started` stanu wystąpienia, przy użyciu <xref:System.Activities.Tracking.WorkflowInstanceQuery>.

  ```xml
  <workflowInstanceQueries>
      <workflowInstanceQuery>
        <states>
          <state name="Started"/>
        </states>
      </workflowInstanceQuery>
  </workflowInstanceQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new WorkflowInstanceQuery()
          {
              States = { WorkflowInstanceStates.Started}
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.ActivityStateQuery> — Użyj tego do śledzenia zmian cyklu życia działań, które tworzą wystąpienie przepływu pracy. Na przykład możesz chcieć śledzić każde działanie "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy. To zapytanie jest niezbędne do subskrybowania <xref:System.Activities.Tracking.ActivityStateRecord> obiektów <xref:System.Activities.Tracking.TrackingParticipant>. Dostępne Stany subskrybowania są określone w <xref:System.Activities.Tracking.ActivityStates>.

  W poniższym przykładzie przedstawiono konfigurację i kod służący do subskrybowania rekordów śledzenia stanu działań, które używają <xref:System.Activities.Tracking.ActivityStateQuery> dla działania `SendEmailActivity`.

  ```xml
  <activityStateQueries>
    <activityStateQuery activityName="SendEmailActivity">
      <states>
        <state name="Closed"/>
      </states>
    </activityStateQuery>
  </activityStateQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityStateQuery()
          {
              ActivityName = "SendEmailActivity",
              States = { ActivityStates.Closed }
          }
      }
  };
  ```

  > [!NOTE]
  > Jeśli wiele elementów activityStateQuery ma taką samą nazwę, tylko Stany w ostatnim elemencie są używane w profilu śledzenia.

- <xref:System.Activities.Tracking.ActivityScheduledQuery> — to zapytanie umożliwia śledzenie działania zaplanowanych do wykonania przez działanie nadrzędne. Zapytanie jest niezbędne do subskrybowania <xref:System.Activities.Tracking.ActivityScheduledRecord> obiektów <xref:System.Activities.Tracking.TrackingParticipant>.

  W poniższym przykładzie przedstawiono konfigurację i kod służący do subskrybowania rekordów związanych z `SendEmailActivity`m działaniem podrzędnym, które jest planowane przy użyciu <xref:System.Activities.Tracking.ActivityScheduledQuery>.

  ```xml
  <activityScheduledQueries>
    <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </activityScheduledQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityScheduledQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.FaultPropagationQuery> — Użyj tego do śledzenia obsługi błędów występujących w ramach działania. Zapytanie jest niezbędne do subskrybowania <xref:System.Activities.Tracking.FaultPropagationRecord> obiektów <xref:System.Activities.Tracking.TrackingParticipant>.

  W poniższym przykładzie przedstawiono konfigurację i kod służący do subskrybowania rekordów związanych z propagacją błędów przy użyciu <xref:System.Activities.Tracking.FaultPropagationQuery>.

  ```xml
  <faultPropagationQueries>
    <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />
  </faultPropagationQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new FaultPropagationQuery()
          {
              FaultSourceActivityName = "SendEmailActivity",
              FaultHandlerActivityName = "NotificationsFaultHandler"
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.CancelRequestedQuery> — Użyj tego do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne. Zapytanie jest niezbędne do subskrybowania <xref:System.Activities.Tracking.CancelRequestedRecord> obiektów <xref:System.Activities.Tracking.TrackingParticipant>.

  W poniższym przykładzie przedstawiono konfigurację i kod służący do subskrybowania rekordów związanych z anulowaniem działania przy użyciu <xref:System.Activities.Tracking.CancelRequestedQuery>.

  ```xml
  <cancelRequestedQueries>
    <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </cancelRequestedQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CancelRequestedQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.CustomTrackingQuery> — Użyj tego do śledzenia zdarzeń zdefiniowanych w działaniach kodu. Zapytanie jest niezbędne do subskrybowania <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów <xref:System.Activities.Tracking.TrackingParticipant>.

  W poniższym przykładzie przedstawiono konfigurację i kod służący do subskrybowania rekordów związanych z niestandardowymi rekordami śledzenia przy użyciu <xref:System.Activities.Tracking.CustomTrackingQuery>.

  ```xml
  <customTrackingQueries>
    <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />
  </customTrackingQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CustomTrackingQuery()
          {
              Name = "EmailAddress",
              ActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.BookmarkResumptionQuery> — Użyj tej metody, aby śledzić wznowienie zakładki w ramach wystąpienia przepływu pracy. To zapytanie jest niezbędne do subskrybowania <xref:System.Activities.Tracking.BookmarkResumptionRecord> obiektów <xref:System.Activities.Tracking.TrackingParticipant>.

  W poniższym przykładzie przedstawiono konfigurację i kod służący do subskrybowania rekordów związanych z wznowieniem zakładek przy użyciu <xref:System.Activities.Tracking.BookmarkResumptionQuery>.

  ```xml
  <bookmarkResumptionQueries>
    <bookmarkResumptionQuery name="SentEmailBookmark" />
  </bookmarkResumptionQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new BookmarkResumptionQuery()
          {
              Name = "sentEmailBookmark"
          }
      }
  };
  ```

### <a name="annotations"></a>Adnotacje

Adnotacje umożliwiają arbitralnie tag śledzenia rekordów o wartości, które mogą być skonfigurowane po czas kompilacji. Na przykład może być konieczne kilka rekordów śledzenia w kilku przepływach pracy, które mają być otagowane przy użyciu "serwer poczty" = = "wiadomość serwer1". To ułatwia znalezienie wszystkich rekordów z tym znacznikiem podczas wykonywania zapytania rekordów śledzenia później.

Aby to osiągnąć, adnotacja jest dodawana do zapytania śledzenia, jak pokazano w poniższym przykładzie.

```xml
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed"/>
  </states>
  <annotations>
    <annotation name="MailServer" value="Mail Server1"/>
  </annotations>
</activityStateQuery>
```

### <a name="how-to-create-a-tracking-profile"></a>Jak utworzyć profil śledzenia

Elementy zapytania śledzenia są używane do tworzenia profilu śledzenia przy użyciu pliku konfiguracyjnego XML lub kodu [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]. Oto przykład profilu śledzenia utworzonego przy użyciu pliku konfiguracji.

```xml
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile ">
        <workflow activityDefinitionId="*">
          <!--Specify the tracking profile query elements to subscribe for tracking records-->
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```

> [!WARNING]
> W przypadku WF przy użyciu hosta usługi przepływu pracy profil śledzenia jest zwykle tworzony przy użyciu pliku konfiguracji. Istnieje również możliwość utworzenia profilu śledzenia z kodem przy użyciu profilu śledzenia i interfejsu API zapytań śledzenia.

Profil skonfigurowany jako plik konfiguracji XML jest stosowany do śledzenia uczestnika przy użyciu rozszerzenia zachowania. Ten element jest dodawany do obiektu WorkflowServiceHost zgodnie z opisem w dalszej części [Konfigurowanie śledzenia dla przepływu pracy](configuring-tracking-for-a-workflow.md).

Poziom szczegółowości rekordów śledzenia emitowanych przez hosta jest określany przez ustawienia konfiguracji w ramach profilu śledzenia. Uczestnik śledzenia subskrybuje śledzenie rekordów przez dodawanie zapytań do profilu śledzenia. Aby subskrybować wszystkie rekordy śledzenia, profil śledzenia musi określać wszystkie zapytania śledzenia przy użyciu "\*" w polach nazw w poszczególnych zapytaniach.

Poniżej przedstawiono niektóre typowe przykłady profilów śledzenia.

- Profil śledzenia umożliwiający uzyskanie rekordów wystąpień przepływu pracy i błędów.

  ```xml
  <trackingProfile name="Instance and Fault Records">
    <workflow activityDefinitionId="*">
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="*" />
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
      <activityStateQueries>
        <activityStateQuery activityName="*">
          <states>
            <state name="Faulted"/>
          </states>
        </activityStateQuery>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
  ```

- Profil śledzenia umożliwiający uzyskanie wszystkich niestandardowych rekordów śledzenia.

  ```xml
  <trackingProfile name="Instance_And_Custom_Records">
    <workflow activityDefinitionId="*">
      <customTrackingQueries>
        <customTrackingQuery name="*" activityName="*" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
  ```

## <a name="see-also"></a>Zobacz także

- [Śledzenie SQL](./samples/sql-tracking.md)
- [Monitorowanie aplikacji sieci szkieletowej systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Monitorowanie aplikacji przy użyciu sieci szkieletowej aplikacji](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
