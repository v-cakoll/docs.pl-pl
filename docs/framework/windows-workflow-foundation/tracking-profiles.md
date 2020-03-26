---
title: Profile śledzenia
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 609c3f0c728e71d1bbf5335aae0b18d6f99a7181
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249041"
---
# <a name="tracking-profiles"></a>Profile śledzenia

Profile śledzenia zawierają zapytania śledzenia, które umożliwiają uczestnikowi śledzenia subskrybowanie zdarzeń przepływu pracy, które są emitowane, gdy stan wystąpienia przepływu pracy zmienia się w czasie wykonywania.

## <a name="tracking-profiles"></a>Profile śledzenia

Profile śledzenia służą do określania, które informacje o śledzeniu są emitowane dla wystąpienia przepływu pracy. Jeśli nie określono profilu, wszystkie zdarzenia śledzenia są emitowane. Jeśli profil zostanie określony, zostaną wyemitowane zdarzenia śledzenia określone w profilu. W zależności od wymagań monitorowania można napisać profil, który jest bardzo ogólny, który subskrybuje mały zestaw zmian stanu wysokiego poziomu w przepływie pracy. Z drugiej strony można utworzyć bardzo szczegółowy profil, którego wynikowe zdarzenia są wystarczająco bogate, aby później odtworzyć szczegółowy przepływ wykonania.

Profile śledzenia manifestują się jako elementy XML w standardowym pliku konfiguracyjnym programu .NET Framework lub są określone w kodzie. Poniższy przykład jest [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] profilu śledzenia w pliku konfiguracji, który umożliwia uczestnikowi śledzenia subskrybować zdarzenia `Started` i `Completed` przepływu pracy.

```xml
<system.serviceModel>
    ...
    <tracking>
     <profiles>
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

W poniższym przykładzie przedstawiono równoważny profil śledzenia utworzony przy użyciu kodu.

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

Rekordy śledzenia są filtrowane w trybie widoczności <xref:System.Activities.Tracking.ImplementationVisibility> w profilu śledzenia przy użyciu atrybutu. Działanie złożone jest działaniem najwyższego poziomu, które zawiera inne działania, które tworzą jego implementację. Tryb widoczności określa rekordy śledzenia emitowane z działań złożonych w ramach działania przepływu pracy, aby określić, czy działania, które tworzą implementację są śledzone. Tryb widoczności ma zastosowanie na poziomie profilu śledzenia. Filtrowanie rekordów śledzenia dla poszczególnych działań w ramach przepływu pracy jest kontrolowane przez zapytania w profilu śledzenia. Aby uzyskać więcej informacji, zobacz sekcję **Typy zapytań profilu śledzenia** w tym dokumencie.

Dwa tryby widoczności `implementationVisibility` określone przez atrybut w `RootScope` `All`profilu śledzenia są i . Za `RootScope` pomocą trybu pomija rekordy śledzenia dla działań, które tworzą implementację działania w przypadku, gdy działanie złożone nie jest głównym przepływu pracy. Oznacza to, że gdy działanie, które jest implementowane przy użyciu innych `implementationVisibility` działań jest dodawany do przepływu pracy i zestaw rootscope, tylko działania najwyższego poziomu w ramach tego działania złożonego jest śledzony. Jeśli działanie jest głównym przepływem pracy, implementacja działania jest samym przepływem pracy i rekordami śledzenia są emitowane dla działań, które tworzą implementację. Tryb Wszystkie umożliwia emitowanie wszystkich rekordów śledzenia dla działania głównego i wszystkich jego działań złożonych.

Załóżmy na przykład, że *MyActivity* jest działaniem złożonym, którego implementacja zawiera dwa działania: *Activity1* i *Activity2*. Gdy to działanie zostanie dodane do przepływu pracy, a `implementationVisibility` śledzenie `RootScope`jest włączone z profilem śledzenia z ustawionym na , rekordy śledzenia są emitowane tylko dla *MyActivity*. Jednak dla działań *Activity1* i *Activity2*nie są emitowane żadne rekordy.

Jeśli jednak `implementationVisibility` atrybut profilu śledzenia jest ustawiony `All`na , a następnie rekordy śledzenia są emitowane nie tylko dla *MyActivity,* ale także dla działań *Activity1* i *Activity2*.

Flaga `implementationVisibility` dotyczy następujących typów rekordów śledzenia:

- Activitystaterecord

- Faultpropagationrecord

- Cancelrequestedrecord

- Activityscheduledrecord

> [!NOTE]
> CustomTrackingRecords emitowane z implementacji działania nie są odfiltrowywały przez implementacjęStawianie.

Funkcja `implementationVisibility` jest określona <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> jako profil śledzenia w kodzie w następujący sposób:

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

Funkcja `implementationVisibility` jest określona <xref:System.Activities.Tracking.ImplementationVisibility.All> jako profil śledzenia w pliku konfiguracyjnym w następujący sposób:

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

Ustawienie `ImplementationVisibility` w profilu śledzenia jest opcjonalne. Domyślnie jego wartość jest `RootScope`ustawiona na . W wartościach dla tego atrybutu jest również rozróżniana wielkość liter.

### <a name="tracking-profile-query-types"></a>Typy zapytań profilu śledzenia

Profile śledzenia mają strukturę jako deklaratywne subskrypcji dla śledzenia rekordy, które umożliwiają zapytania dla rekordów śledzenie wersję wykonawczą przepływu pracy. Istnieje kilka typów zapytań, które umożliwiają subskrybowanie różnych klas <xref:System.Activities.Tracking.TrackingRecord> obiektów. Profile śledzenia można określić w konfiguracji lub za pomocą kodu. Oto najczęściej spotykane typy zapytań:

- <xref:System.Activities.Tracking.WorkflowInstanceQuery>- Użyj tego do śledzenia zmian cyklu życia wystąpienia `Started` `Completed`przepływu pracy, takich jak wcześniej zademonstrowane i . <xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  Stany, które można subskrybować są <xref:System.Activities.Tracking.WorkflowInstanceStates> określone w klasie.

  Konfiguracja lub kod używany do subskrybowania rekordów `Started` śledzenia na <xref:System.Activities.Tracking.WorkflowInstanceQuery> poziomie wystąpienia przepływu pracy dla stanu wystąpienia przy użyciu stanu jest wyświetlany w poniższym przykładzie.

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

- <xref:System.Activities.Tracking.ActivityStateQuery>- Użyj tego do śledzenia zmian cyklu życia działań, które tworzą wystąpienie przepływu pracy. Na przykład można śledzić za każdym razem, gdy działanie "Wyślij e-mail" zostanie ukończone w wystąpieniu przepływu pracy. Ta kwerenda jest <xref:System.Activities.Tracking.TrackingParticipant> niezbędna do <xref:System.Activities.Tracking.ActivityStateRecord> subskrybowania obiektów. Dostępne stany do subskrybowania <xref:System.Activities.Tracking.ActivityStates>są określone w .

  Konfiguracja i kod używany do subskrybowania <xref:System.Activities.Tracking.ActivityStateQuery> rekordów `SendEmailActivity` śledzenia stanu działania, które używają dla działania jest pokazany w poniższym przykładzie.

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
  > Jeśli wiele activityStateQuery elementy mają taką samą nazwę, tylko stany w ostatnim elemencie są używane w profilu śledzenia.

- <xref:System.Activities.Tracking.ActivityScheduledQuery>- Ta kwerenda umożliwia śledzenie działania zaplanowanego do wykonania przez działanie nadrzędne. Kwerenda jest niezbędna <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.ActivityScheduledRecord> obiektów.

  Konfiguracja i kod używany do subskrybowania rekordów związanych z aktywnością podrzędną `SendEmailActivity` zaplanowaną <xref:System.Activities.Tracking.ActivityScheduledQuery> przy użyciu jest pokazany w poniższym przykładzie.

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

- <xref:System.Activities.Tracking.FaultPropagationQuery>- Użyj tego do śledzenia obsługi usterek występujących w ramach działania. Kwerenda jest niezbędna <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.FaultPropagationRecord> obiektów.

  Konfiguracja i kod używany do subskrybowania rekordów <xref:System.Activities.Tracking.FaultPropagationQuery> związanych z propagacją błędów za pomocą jest pokazany w poniższym przykładzie.

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

- <xref:System.Activities.Tracking.CancelRequestedQuery>- Użyj tego do śledzenia żądań anulowania działania podrzędnego przez działanie nadrzędne. Kwerenda jest niezbędna <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.CancelRequestedRecord> obiektów.

  Konfiguracja i kod używany do subskrybowania <xref:System.Activities.Tracking.CancelRequestedQuery> rekordów związanych z anulowaniem działania przy użyciu jest pokazany w poniższym przykładzie.

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

- <xref:System.Activities.Tracking.CustomTrackingQuery>- Użyj tego do śledzenia zdarzeń, które można zdefiniować w działaniach kodu. Kwerenda jest niezbędna <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów.

  Konfiguracja i kod używany do subskrybowania rekordów związanych z niestandardowymi rekordami śledzenia za pomocą <xref:System.Activities.Tracking.CustomTrackingQuery> jest pokazany w poniższym przykładzie.

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

- <xref:System.Activities.Tracking.BookmarkResumptionQuery>- Użyj tego, aby śledzić wznowienie zakładki w wystąpieniu przepływu pracy. Ta kwerenda jest <xref:System.Activities.Tracking.TrackingParticipant> niezbędna do <xref:System.Activities.Tracking.BookmarkResumptionRecord> subskrybowania obiektów.

  Konfiguracja i kod używany do subskrybowania rekordów <xref:System.Activities.Tracking.BookmarkResumptionQuery> związanych z wznowieni zakładówek owanie przy użyciu jest pokazany w poniższym przykładzie.

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

Adnotacje umożliwiają arbitralnie tag śledzenia rekordów o wartości, które mogą być skonfigurowane po czas kompilacji. Na przykład można dodać kilka rekordów śledzenia w kilku przepływach pracy tagiem "Serwer poczty" == "Serwer poczty1". To ułatwia znalezienie wszystkich rekordów z tym znacznikiem podczas wykonywania zapytania rekordów śledzenia później.

Aby to osiągnąć, adnotacja jest dodawana do kwerendy śledzącej, jak pokazano w poniższym przykładzie.

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

Elementy zapytania śledzenia są używane do tworzenia profilu śledzenia przy [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] użyciu pliku konfiguracyjnego XML lub kodu. Oto przykład profilu śledzenia utworzonego przy użyciu pliku konfiguracyjnego.

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
> W przypadku WF przy użyciu hosta usługi przepływ pracy profil śledzenia jest zazwyczaj tworzony przy użyciu pliku konfiguracyjnego. Istnieje również możliwość utworzenia profilu śledzenia z kodem przy użyciu profilu śledzenia i śledzenia interfejsu API kwerendy.

Profil skonfigurowany jako plik konfiguracyjny XML jest stosowany do uczestnika śledzenia przy użyciu rozszerzenia zachowania. Zostanie on dodany do workflowServiceHost zgodnie z opisem w dalszej sekcji [Konfigurowanie śledzenia dla przepływu pracy](configuring-tracking-for-a-workflow.md).

Szczegółowość rekordów śledzenia emitowanych przez hosta zależy od ustawień konfiguracji w profilu śledzenia. Uczestnik śledzenia subskrybuje rekordy śledzenia, dodając zapytania do profilu śledzenia. Aby zasubskrybować wszystkie rekordy śledzenia, profil śledzenia musi\*określić wszystkie zapytania śledzenia za pomocą " " w polach nazw w każdym z kwerend.

Oto niektóre z typowych przykładów profili śledzenia.

- Profil śledzenia w celu uzyskania rekordów wystąpienia przepływu pracy i usterek.

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

- Profil śledzenia w celu uzyskania wszystkich niestandardowych rekordów śledzenia.

  ```xml
  <trackingProfile name="Instance_And_Custom_Records">
    <workflow activityDefinitionId="*">
      <customTrackingQueries>
        <customTrackingQuery name="*" activityName="*" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
  ```

## <a name="see-also"></a>Zobacz też

- [Śledzenie SQL](./samples/sql-tracking.md)
- [Monitorowanie sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Monitorowanie aplikacji za pomocą sieci szkieletowej aplikacji](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
