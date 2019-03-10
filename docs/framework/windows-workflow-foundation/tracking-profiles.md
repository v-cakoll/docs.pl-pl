---
title: Profile śledzenia
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 2fa4d65a6f0056824b2fc9dd67b93608777fc75d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721375"
---
# <a name="tracking-profiles"></a>Profile śledzenia

Śledzenie profile zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.

## <a name="tracking-profiles"></a>Profile śledzenia

Profile śledzenia są używane do określania, jakie informacje śledzenia jest emitowane dla wystąpienia przepływu pracy. Jeśli profil nie jest określony, wszystkie zdarzenia śledzenia są emitowane. Jeśli profil jest określony, zdarzenia śledzenia określone w profilu będzie emitowane. W zależności od wymagań dotyczących monitorowania może zapisu profil, który jest bardzo ogólny, które subskrybuje niewielkiego zestawu zmian stanu wysokiego poziomu w przepływie pracy. Z drugiej strony można utworzyć bardzo szczegółowe profil którego wynikowego zdarzenia są rozbudowanych, odtworzenie przepływ wykonania szczegółowe później.

Profile śledzenia objawy elementy XML w ramach standardowej [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] pliku konfiguracji lub określone w kodzie. Poniższy przykład jest [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] profil w pliku konfiguracji, który umożliwia śledzenia uczestnika do subskrybowania śledzenia `Started` i `Completed` zdarzenia przepływu pracy.

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

Poniższy przykład pokazuje odpowiednik śledzenia profil został utworzony przy użyciu kodu.

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

Rekordy śledzenia są filtrowane w trybie widoczność w profilu śledzenia przy użyciu <xref:System.Activities.Tracking.ImplementationVisibility> atrybutu. Działanie złożone jest czynnością najwyższego poziomu, zawierający innych działań, które tworzą jego wykonania. Określa tryb widoczności, rekordów śledzenia emitowane z złożonych działań wewnątrz działania elementu przepływu pracy, aby określić, jeśli działania, które tworzą implementację są śledzone. Tryb widoczności odnosi się na śledzenie poziomu profilu. Filtrowanie rekordów dla poszczególnych działań w przepływie pracy śledzenia jest kontrolowane przez zapytania w profilu śledzenia. Aby uzyskać więcej informacji, zobacz **śledzenie typów zapytań profilu** sekcji tego dokumentu.

Tryby widoczność dwie określone przez `implementationVisibility` atrybutu w profilu śledzenia `RootScope` i `All`. Za pomocą `RootScope` tryb Pomija rekordy śledzenia działań, które tworzą implementację działanie w przypadku, gdy działanie złożone nie jest głównym przepływu pracy. Oznacza to, że po dodaniu działania, który jest implementowany przy użyciu innych działań w przepływie pracy i `implementationVisibility` wartość RootScope, działanie najwyższego poziomu w ramach tego działania złożonego jest śledzone. Jeśli działanie jest głównym przepływu pracy, a następnie wykonanie działania jest przepływ pracy wraz z śledzenia rekordów, które są emitowane dla działań, które tworzą implementację. Przy użyciu trybu wszystkich zezwala na wszystkich rekordów śledzenia emitowane dla działania głównego i wszystkich jego działań złożonych.

Na przykład, załóżmy, że *MyActivity* jest czynnością złożonego, którego implementacja zawiera dwa działania *działania Activity1* i *Activity2*. Gdy to działanie jest dodawany do przepływu pracy i śledzenia włączono profil śledzenia z `implementationVisibility` równa `RootScope`, tylko w przypadku są emitowane rekordów śledzenia *MyActivity*. Jednak żadne rekordy nie są emitowane działań *działania Activity1* i *Activity2*.

Jednak jeśli `implementationVisibility` atrybutu dla profilu śledzenia jest ustawiony na `All`, a następnie są emitowane rekordów śledzenia nie tylko *MyActivity*, ale również dla działań *działania Activity1* i  *Activity2*.

`implementationVisibility` Flaga ma zastosowanie do następujące typy rekordów śledzenia:

- ActivityStateRecord

- FaultPropagationRecord

- CancelRequestedRecord

- ActivityScheduledRecord

> [!NOTE]
> CustomTrackingRecords emitowane przez implementację działania nie są odfiltrowywane przez ustawienie implementationVisibility.

`implementationVisibility` Funkcji jest określony jako <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> śledzenia profilu w kodzie w następujący sposób:

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

`implementationVisibility` Funkcji jest określony jako <xref:System.Activities.Tracking.ImplementationVisibility.All> w profilu śledzenia w konfiguracji pliku w następujący sposób:

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

`ImplementationVisibility` Ustawienie w profilu śledzenia jest opcjonalne. Domyślnie, jej wartość jest równa `RootScope`. Wartości dla tego atrybutu jest uwzględniana wielkość liter.

### <a name="tracking-profile-query-types"></a>Typy zapytań profilu śledzenia

Profile śledzenia mają strukturę jako deklaratywne subskrypcji dla śledzenia rekordy, które umożliwiają zapytania dla rekordów śledzenie wersję wykonawczą przepływu pracy. Istnieje kilka typów zapytania, które umożliwiają subskrybować różnymi klasami <xref:System.Activities.Tracking.TrackingRecord> obiektów. Śledzenie profile można określić w konfiguracji lub za pomocą kodu. Poniżej przedstawiono najbardziej typowych zapytań:

- <xref:System.Activities.Tracking.WorkflowInstanceQuery> — Umożliwia śledzenie zmian cyklu życia wystąpienia przepływu pracy, takich jak wcześniej — pokazano `Started` i `Completed`. 
  <xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:

    - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

    - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

    - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

    - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

    - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

    Stany, które mogą być subskrybowane są określone w <xref:System.Activities.Tracking.WorkflowInstanceStates> klasy.

    Konfiguracja lub kod używany do subskrybowania rekordów dla śledzenia na poziomie wystąpienia przepływu pracy `Started` wystąpienie stanu za pomocą <xref:System.Activities.Tracking.WorkflowInstanceQuery> przedstawiono w poniższym przykładzie.

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

- <xref:System.Activities.Tracking.ActivityStateQuery> — Ten służy do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy. Na przykład chcesz do śledzenia za każdym razem, gdy kończy działanie "Wyślij wiadomość E-Mail", w ramach wystąpienie przepływu pracy. To zapytanie jest niezbędne do <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.ActivityStateRecord> obiektów. Stany do subskrybowania są wyszczególnione w <xref:System.Activities.Tracking.ActivityStates>.

    Konfiguracja i kod używany do subskrybowania rekordów śledzenia stanu działania, korzystających z <xref:System.Activities.Tracking.ActivityStateQuery> dla `SendEmailActivity` działania przedstawiono w poniższym przykładzie.

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
    > Jeśli wiele elementów activityStateQuery mają taką samą nazwę, tylko Stany w ostatnim elemencie są używane w profilu śledzenia.

- <xref:System.Activities.Tracking.ActivityScheduledQuery> — To zapytanie pozwala do śledzenia działania zaplanowane do wykonania przez działanie nadrzędne. Zapytanie jest niezbędne dla <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.ActivityScheduledRecord> obiektów.

    Konfiguracja i kod używany do subskrybowania rekordów związanych z `SendEmailActivity` działania podrzędnego zaplanowanej przy użyciu <xref:System.Activities.Tracking.ActivityScheduledQuery> przedstawiono w poniższym przykładzie.

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

- <xref:System.Activities.Tracking.FaultPropagationQuery> — Ten służy do śledzenia obsługi błędów występujących w ramach działania. Zapytanie jest niezbędne dla <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.FaultPropagationRecord> obiektów.

    Konfiguracja i kod używany do subskrybowania rekordów związanych z propagacji błędów <xref:System.Activities.Tracking.FaultPropagationQuery> przedstawiono w poniższym przykładzie.

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

- <xref:System.Activities.Tracking.CancelRequestedQuery> — Ten służy do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne. Zapytanie jest niezbędne dla <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.CancelRequestedRecord> obiektów.

    Konfiguracja i kod używany do subskrybowania rekordów związanych z anulowania działania <xref:System.Activities.Tracking.CancelRequestedQuery> przedstawiono w poniższym przykładzie.

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

- <xref:System.Activities.Tracking.CustomTrackingQuery> — Ten służy do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu. Zapytanie jest niezbędne dla <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów.

    Konfiguracja i kod używany do subskrybowania rekordów powiązanych śledzenia niestandardowe rekordów przy użyciu <xref:System.Activities.Tracking.CustomTrackingQuery> przedstawiono w poniższym przykładzie.

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

- <xref:System.Activities.Tracking.BookmarkResumptionQuery> — Ten służy do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy. To zapytanie jest niezbędne do <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.BookmarkResumptionRecord> obiektów.

    Konfiguracja i kod używany do subskrybowania rekordów związanych z wznowienie zakładki <xref:System.Activities.Tracking.BookmarkResumptionQuery> przedstawiono w poniższym przykładzie.

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

Adnotacje umożliwiają arbitralnie tag śledzenia rekordów o wartości, które mogą być skonfigurowane po czas kompilacji. Na przykład może być kilka rekordów śledzenia na kilka przepływy pracy służące do być oznakowane za pomocą "Serwer poczty" == "Serwer1 poczty". To ułatwia znalezienie wszystkich rekordów z tym znacznikiem podczas wykonywania zapytania rekordów śledzenia później.

Aby to osiągnąć, adnotacja jest dodawany do zapytania śledzenia, jak pokazano w poniższym przykładzie.

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

Elementy zapytania śledzenia są używane do tworzenia profilu śledzenia przy użyciu pliku konfiguracji XML lub [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]kodu. Poniżej przedstawiono przykład profilu śledzenia, który został utworzony przy użyciu pliku konfiguracji.

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
> Dla programu WF przy użyciu hosta usługi przepływu pracy profilu śledzenia jest zwykle tworzony, przy użyciu pliku konfiguracji. Istnieje również możliwość tworzenia profilu śledzenia przy użyciu kodu przy użyciu profilu śledzenia i śledzenia interfejsu API zapytań.

Profil, który został skonfigurowany jako plik konfiguracyjny XML jest stosowany do śledzenia uczestnika, za pomocą rozszerzenia zachowania. To jest dodawany do klasy WorkflowServiceHost zgodnie z opisem w dalszej części [Konfigurowanie śledzenia przepływu pracy](configuring-tracking-for-a-workflow.md).

Poziom szczegółowości rekordów śledzenia emitowane przez hosta jest określana przez ustawienia konfiguracji w profilu śledzenia. Subskrybuje uczestnikiem śledzenia do śledzenia rekordów przez dodanie zapytania do profilu śledzenia. Aby subskrybować wszystkie rekordy śledzenia, należy określić wszystkie zapytania śledzenia przy użyciu profilu śledzenia "\*" w polach Nazwa we wszystkich zapytań.

Poniżej przedstawiono niektóre typowe przykłady śledzenie profile.

- Profil śledzenia do uzyskania rekordów wystąpienia przepływu pracy i usterek.

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

1. Profil śledzenia można uzyskać wszystkie niestandardowe rekordy śledzenia.

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
- [Windows Server AppFabric monitorowania](https://go.microsoft.com/fwlink/?LinkId=201273)
- [Monitorowanie aplikacji przy użyciu rozwiązania AppFabric](https://go.microsoft.com/fwlink/?LinkId=201275)
