---
title: Profile śledzenia
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 4f70964ea7e2456f82aeac4bfb9aedfdb239d58a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519987"
---
# <a name="tracking-profiles"></a>Profile śledzenia
Śledzenie profile zawierają zapytania dotyczące śledzenia, które umożliwiają śledzenie uczestnika do subskrybowanie zdarzeń przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.  
  
## <a name="tracking-profiles"></a>Profile śledzenia  
 Profile śledzenia służą do określania, jakie informacje śledzenia jest emitowany dla wystąpienia przepływu pracy. Jeśli profil nie jest określona, wszystkie zdarzenia śledzenia są emitowane. Jeśli profil jest określony, zdarzenia śledzenia określone w profilu zostanie wyemitowany. W zależności od wymagań monitorowania może zapisać profil, który jest bardzo ogólnych, które subskrybuje niewielki zestaw zmian stanu ogólny przepływ pracy. Z drugiej strony może utworzyć profil bardzo szczegółowe którego wynikowy zdarzenia są sformatowanego odtworzenie przepływu szczegółowe wykonywania później.  
  
 Profile śledzenia pojawiają się jako elementów XML w ramach standardowego [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] pliku konfiguracji lub określona w kodzie. Poniższy przykład jest [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] profil w pliku konfiguracji, który umożliwia śledzenie uczestnika do subskrybowania śledzenia `Started` i `Completed` zdarzeń przepływu pracy.  
  
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
  
 W poniższym przykładzie przedstawiono odpowiednikiem śledzenia profil utworzony przy użyciu kodu.  
  
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
  
 Śledzenie rekordów są filtrowane w trybie widoczność w profilu śledzenia przy użyciu <xref:System.Activities.Tracking.ImplementationVisibility> atrybutu. Działanie złożone jest najwyższego poziomu działanie, które zawiera inne działania, które tworzą jego wykonania. Tryb widoczności określa rekordy śledzenia wyemitowanego z złożonego działań w ramach działania przepływu pracy, aby określić, czy działania, które tworzą wdrożenia są śledzone.  Tryb widoczności zastosuje w śledzenia profilu poziom. Filtrowanie rekordów dla poszczególnych działań w przepływie pracy śledzenia jest kontrolowana przez kwerend w profilu śledzenia. Aby uzyskać więcej informacji, zobacz **śledzenia typy zapytań profilu** części tego dokumentu.  
  
 Widoczność dwóch trybów określony przez `implementationVisibility` w profilu śledzenia są `RootScope` i `All`. Przy użyciu `RootScope` tryb Pomija rekordy śledzenia działań, które tworzą implementacja działania, w przypadku, gdy działanie złożone nie jest elementem głównym przepływu pracy.  Oznacza to, że po dodaniu działania, która jest zaimplementowana przy użyciu innych działań w przepływie pracy i `implementationVisibility` wartość RootScope, śledzić działania najwyższego poziomu w obrębie tego działania złożonego. Jeśli działanie jest głównego przepływu pracy, a następnie wykonanie działania jest przepływ pracy się i śledzenie rekordów są emitowane działań, które tworzą implementacji. Przy użyciu trybu wszystkich zezwala na wszystkie rekordy śledzenia, aby emitować dla działania głównego i jego działań złożonych.  
  
 Załóżmy na przykład, *MyActivity* jest działania złożonego, którego implementację zawiera dwa działania *działania Activity1* i *Activity2*.  Gdy to działanie jest dodawany do przepływu pracy i śledzenie jest włączone w profilu śledzenia z `implementationVisibility` ustawioną `RootScope`, śledzenie rekordów są emitowane tylko w przypadku *MyActivity*.  Jednak żadne rekordy są emitowane działań *działania Activity1* i *Activity2*.  
  
 Jednak jeśli `implementationVisisbility` atrybutu dla profilu śledzenia jest ustawiony na `All`, a następnie rejestruje śledzenia są emitowane nie tylko w przypadku *MyActivity*, ale także dla działań *działania Activity1* i  *Activity2*.  
  
 `implementationVisibility` Flaga jest stosowana do następujących typów rekordów śledzenia:  
  
-   ActivityStateRecord  
  
-   FaultPropagationRecord  
  
-   CancelRequestedRecord  
  
-   ActivityScheduledRecord  
  
> [!NOTE]
>  CustomTrackingRecords wyemitowanego z implementacji działania nie są odfiltrowywane przez ustawienie implementationVisibility.  
  
 `implementationVisibility` Funkcji jest określony jako <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> na śledzenie profilu w kodzie w następujący sposób:  
  
```  
TrackingProfile sampleTrackingProfile = new TrackingProfile()  
{  
    Name = "Sample Tracking Profile",  
    ImplementationVisibility = ImplementationVisibility.RootScope  
};  
```  
  
 `implementationVisibility` Funkcji jest określony jako <xref:System.Activities.Tracking.ImplementationVisibility.All> w konfiguracji profilu śledzenia plików w następujący sposób:  
  
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
  
 `ImplementationVisibility` Ustawienie w profilu śledzenia jest opcjonalne. Domyślnie, jego wartość jest równa `RootScope`. Wartości dla tego atrybutu jest uwzględniana wielkość liter.  
  
### <a name="tracking-profile-query-types"></a>Typy zapytań profilu śledzenia  
 Profile śledzenia mają strukturę jako deklaratywne subskrypcji dla śledzenia rekordy, które umożliwiają zapytania dla rekordów śledzenie wersję wykonawczą przepływu pracy. Istnieje kilka typów zapytania umożliwiające subskrybować różnych klas <xref:System.Activities.Tracking.TrackingRecord> obiektów. Śledzenie profile można określić w konfiguracji lub za pomocą kodu. W tym miejscu są najczęściej używane typy zapytań:  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceQuery> -Służy do śledzenia zmiany cyklu życia wystąpienia przepływu pracy, takich jak wcześniej — zostało to pokazane `Started` i `Completed`. <xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
     Stany, które może być subskrybowana są określone w <xref:System.Activities.Tracking.WorkflowInstanceStates> klasy.  
  
     Konfiguracja lub kod używany do subskrybowania śledzenia rekordy na poziomie wystąpienia przepływu pracy `Started` wystąpienie stanu przy użyciu <xref:System.Activities.Tracking.WorkflowInstanceQuery> przedstawiono w poniższym przykładzie.  
  
    ```xml  
    <workflowInstanceQueries>  
        <workflowInstanceQuery>  
          <states>  
            <state name="Started"/>  
          </states>  
        </workflowInstanceQuery>  
    </workflowInstanceQueries>  
    ```  
  
    ```  
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
  
-   <xref:System.Activities.Tracking.ActivityStateQuery> -Służy do śledzenia zmian cyklu życia działań, które tworzą wystąpienia przepływu pracy. Na przykład może być do śledzenia każdorazowo po ukończeniu działania "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy. To zapytanie jest niezbędne do <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.ActivityStateRecord> obiektów. Dostępne stany do subskrybowania są określone w <xref:System.Activities.Tracking.ActivityStates>.  
  
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
  
    ```  
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
    >  Jeśli wiele elementów activityStateQuery mają taką samą nazwę, tylko Stany w ostatnim elemencie są używane w profilu śledzenia.  
  
-   <xref:System.Activities.Tracking.ActivityScheduledQuery> — To zapytanie umożliwia śledzenie działania zaplanowane do uruchomienia przez działania nadrzędnego. Zapytanie jest niezbędne do <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.ActivityScheduledRecord> obiektów.  
  
     Konfiguracja i kod używany do subskrybowania rekordy związane z `SendEmailActivity` działanie podrzędne planowany przy użyciu <xref:System.Activities.Tracking.ActivityScheduledQuery> przedstawiono w poniższym przykładzie.  
  
    ```xml  
    <activityScheduledQueries>  
      <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />  
     </activityScheduledQueries>  
    ```  
  
    ```  
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
  
-   <xref:System.Activities.Tracking.FaultPropagationQuery> -Służy do śledzenia Obsługa błędów występujących w ramach działania. Zapytanie jest niezbędne do <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.FaultPropagationRecord> obiektów.  
  
     Konfiguracja i kod używany do subskrybowania rekordy powiązane z użyciem propagacji błędów <xref:System.Activities.Tracking.FaultPropagationQuery> przedstawiono w poniższym przykładzie.  
  
    ```xml  
    <faultPropagationQueries>  
      <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />  
    </faultPropagationQueries>  
    ```  
  
    ```  
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
  
-   <xref:System.Activities.Tracking.CancelRequestedQuery> — Umożliwia śledzenie żądań, aby anulować działanie podrzędne przez działania nadrzędnego. Zapytanie jest niezbędne do <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.CancelRequestedRecord> obiektów.  
  
     Konfiguracja i kod używany do subskrybowania rekordy powiązane z użyciem anulowania działania <xref:System.Activities.Tracking.CancelRequestedQuery> przedstawiono w poniższym przykładzie.  
  
    ```xml  
    <cancelRequestedQueries>  
      <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />  
    </cancelRequestedQueries>  
    ```  
  
    ```  
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
  
-   <xref:System.Activities.Tracking.CustomTrackingQuery> -Służy do śledzenia zdarzeń zdefiniowanych w działaniach kodu. Zapytanie jest niezbędne do <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów.  
  
     Konfiguracja i kod używany do subskrybowania rekordy związane z śledzenia niestandardowych rekordów przy użyciu <xref:System.Activities.Tracking.CustomTrackingQuery> przedstawiono w poniższym przykładzie.  
  
    ```xml  
    <customTrackingQueries>  
      <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />  
    </customTrackingQueries>  
    ```  
  
    ```  
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
  
-   <xref:System.Activities.Tracking.BookmarkResumptionQuery> -Służy do śledzenia wznowienie zakładki w ramach wystąpienia przepływu pracy. To zapytanie jest niezbędne do <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.BookmarkResumptionRecord> obiektów.  
  
     Konfiguracja i kod używany do subskrybowania rekordy powiązane z użyciem wznowienie zakładki <xref:System.Activities.Tracking.BookmarkResumptionQuery> przedstawiono w poniższym przykładzie.  
  
    ```xml  
    <bookmarkResumptionQueries>  
      <bookmarkResumptionQuery name="SentEmailBookmark" />  
    </bookmarkResumptionQueries>  
    ```  
  
    ```  
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
 Adnotacje umożliwiają arbitralnie tag śledzenia rekordów o wartości, które mogą być skonfigurowane po czas kompilacji. Na przykład może być kilka rekordów śledzenia między kilka przepływy pracy, aby być oznaczane "Serwera poczty" == "Poczty serwer1". To ułatwia znalezienie wszystkich rekordów z tym znacznikiem podczas wykonywania zapytania rekordów śledzenia później.  
  
 Aby to zrobić, adnotacja została dodana do zapytania śledzenia, jak pokazano w poniższym przykładzie.  
  
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
 Elementy zapytania śledzenia są używane do tworzenia profilu śledzenia przy użyciu pliku konfiguracji XML lub [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]kodu.  Oto przykład profilu śledzenia, który został utworzony przy użyciu pliku konfiguracji.  
  
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
>  Przy użyciu hosta usługi przepływu pracy WF profilu śledzenia jest zwykle utworzona przy użyciu pliku konfiguracji. Istnieje również możliwość utworzenia profilu śledzenia z kodu przy użyciu profilu śledzenia i śledzenie zapytania interfejsu API.  
  
 Skonfigurowany jako plik konfiguracyjny XML profilu jest stosowany do uczestnika śledzenia przy użyciu rozszerzenia zachowania. To jest dodawane do obiektu WorkflowServiceHost, zgodnie z opisem w dalszej części artykułu [Konfigurowanie śledzenia przepływu pracy](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
 Poziom szczegółowości śledzenia rekordy emitowane przez hosta jest określana przez ustawienia konfiguracji w profilu śledzenia. Uczestnik śledzenia subskrybuje śledzenie rekordów przez dodanie zapytania do profilu śledzenia. Aby subskrybować wszystkie rekordy śledzenia, należy określić wszystkie zapytania dotyczące śledzenia przy użyciu profilu śledzenia "*" w polach Nazwa każdego zapytania.  
  
 Poniżej przedstawiono niektóre typowe przykłady śledzenia profilów.  
  
-   Profil śledzenia uzyskanie rekordów wystąpienia przepływu pracy i usterek.  
  
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
  
1.  Profil śledzenia można uzyskać wszystkie rekordy śledzenia niestandardowych.  
  
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
 [Śledzenie SQL](../../../docs/framework/windows-workflow-foundation/samples/sql-tracking.md)  
 [Windows Server AppFabric monitorowania](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorowanie aplikacji przy użyciu rozwiązania AppFabric](http://go.microsoft.com/fwlink/?LinkId=201275)
