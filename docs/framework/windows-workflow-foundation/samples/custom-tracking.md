---
title: Niestandardowe śledzenie
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: c986d9845bb76219ad8b0657a3a7252aaaf4c6cd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392546"
---
# <a name="custom-tracking"></a>Niestandardowe śledzenie
W tym przykładzie pokazano, jak tworzenie niestandardowego uczestnika śledzenia i zapisać zawartość danych śledzenia do konsoli. Ponadto w przykładzie pokazano jak emitowanie <xref:System.Activities.Tracking.CustomTrackingRecord> danych zdefiniowane przez obiekty użytkownika jest wypełniony. Filtry uczestnika śledzenia opartych na konsoli <xref:System.Activities.Tracking.TrackingRecord> obiektów emitowanych przez przepływ pracy korzystający z profilu śledzenia obiekt utworzony w kodzie.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Windows Workflow Foundation (WF) zapewnia infrastrukturę śledzenia do śledzenia wykonywania wystąpienia przepływu pracy. Środowisko uruchomieniowe śledzenia implementuje wystąpienia przepływu pracy, aby emitować zdarzenia związane z cyklem życia przepływu pracy, zdarzenia z działań przepływu pracy i zdarzenia niestandardowe śledzenia. W poniższej tabeli przedstawiono podstawowe składniki infrastruktury śledzenia.  
  
|Składnik|Opis|  
|---------------|-----------------|  
|Śledzenie czasu wykonywania|Zapewnia infrastrukturę, aby emitować rekordów śledzenia.|  
|Uczestnicy śledzenia|Używa rekordów śledzenia. [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] dostarczany z śledzenia uczestnika, który zapisuje rekordy śledzenia jako zdarzenia śledzenie zdarzeń dla Windows (ETW).|  
|Profil śledzenia|Mechanizm filtrowania, który umożliwia śledzenia uczestnika do subskrybowania dla podzbioru rekordów śledzenia emitowane z wystąpienia przepływu pracy.|  
  
 W poniższej tabeli przedstawiono rekordów śledzenia emitowane przez środowisko wykonawcze przepływów pracy.  
  
|Rekord śledzenia|Opis|  
|---------------------|-----------------|  
|Rekordy śledzenia wystąpienia przepływu pracy.|W tym artykule opisano cyklu życia wystąpienia przepływu pracy. Na przykład rekord wystąpienia jest emitowane, gdy przepływ pracy rozpoczyna się lub kończy.|  
|Stan śledzenia rekordów działań.|Szczegóły wykonania działania. Te informacje wskazują stan działania przepływu pracy, takie jak kiedy zaplanowano działania lub po zakończeniu działania lub kiedy zostanie wygenerowany błąd.|  
|Zakładki wznowienie rekordów.|Emitowane przy każdym zakładki w ramach wystąpienie przepływu pracy zostanie wznowione.|  
|Niestandardowe rekordy śledzenia.|Tworzenie przepływu pracy można utworzyć niestandardowe rekordy śledzenia i emitować je w ramach działania niestandardowego.|  
  
 Uczestnik śledzenia subskrybuje dla podzbioru emitowany <xref:System.Activities.Tracking.TrackingRecord> obiektów przy użyciu profilów śledzenia. Profil śledzenia zawiera śledzenia zapytań, zezwalających na subskrypcji dla śledzenia określonego typu rekordu. Śledzenie profile można określić w kodzie lub w konfiguracji.  
  
### <a name="custom-tracking-participant"></a>Niestandardowego uczestnika śledzenia  
 Uczestnik śledzenia interfejsu API umożliwia rozszerzenie środowiska uruchomieniowego śledzenia z uczestnika śledzenia dostarczone przez użytkownika, który może zawierać niestandardowej logiki do obsługi <xref:System.Activities.Tracking.TrackingRecord> obiektów emitowanych przez środowisko wykonawcze przepływów pracy.  
  
 Można zapisać do śledzenia uczestnika użytkownik musi implementować <xref:System.Activities.Tracking.TrackingParticipant>. W szczególności <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> metoda musi być implementowana przez uczestnikiem niestandardowe. Ta metoda jest wywoływana, gdy <xref:System.Activities.Tracking.TrackingRecord> są emitowane przez środowisko wykonawcze przepływów pracy.  
  
```csharp  
public abstract class TrackingParticipant  
{  
    protected TrackingParticipant();  
  
    public virtual TrackingProfile TrackingProfile { get; set; }  
    public abstract void Track(TrackingRecord record, TimeSpan timeout);  
}  
```  
  
 Pełną śledzenia uczestnika, który jest wdrażany w pliku ConsoleTrackingParticipant.cs. Poniższy przykład kodu jest <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> metodę dla niestandardowego uczestnika śledzenia.  
  
```csharp  
protected override void Track(TrackingRecord record, TimeSpan timeout)  
{  
    ...             
    WorkflowInstanceRecord workflowInstanceRecord = record as WorkflowInstanceRecord;  
    if (workflowInstanceRecord != null)  
    {  
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,  
            " Workflow InstanceID: {0} Workflow instance state: {1}",  
            record.InstanceId, workflowInstanceRecord.State));  
    }  
  
    ActivityStateRecord activityStateRecord = record as ActivityStateRecord;  
    if (activityStateRecord != null)  
    {  
        IDictionary<String, object> variables = activityStateRecord.Variables;  
        StringBuilder vars = new StringBuilder();  
  
        if (variables.Count > 0)  
        {  
            vars.AppendLine("\n\tVariables:");  
            foreach (KeyValuePair<string, object> variable in variables)  
            {     
                vars.AppendLine(String.Format(  
                    "\t\tName: {0} Value: {1}", variable.Key, variable.Value));  
            }  
        }  
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,  
            " :Activity DisplayName: {0} :ActivityInstanceState: {1} {2}",  
                activityStateRecord.Activity.Name, activityStateRecord.State,  
            ((variables.Count > 0) ? vars.ToString() : String.Empty)));  
    }  
  
    CustomTrackingRecord customTrackingRecord = record as CustomTrackingRecord;  
  
    if ((customTrackingRecord != null) && (customTrackingRecord.Data.Count > 0))  
    {  
        ...  
    }  
    Console.WriteLine();  
  
}  
```  
  
 Poniższy przykład kodu dodaje uczestnika konsoli do wywoływania przepływu pracy.  
  
```csharp  
ConsoleTrackingParticipant customTrackingParticipant = new ConsoleTrackingParticipant()  
{  
    ...  
    // The tracking profile is set here, refer to Program.CS  
...  
}  
  
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());  
invoker.Extensions.Add(customTrackingParticipant);  
```  
  
### <a name="emitting-custom-tracking-records"></a>Emitowanie niestandardowe rekordy śledzenia  
 Niniejszy przykład pokazuje także możliwość emisji <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów z działanie niestandardowego przepływu pracy:  
  
-   <xref:System.Activities.Tracking.CustomTrackingRecord> Obiekty są tworzone i wypełniane przy użyciu danych zdefiniowane przez użytkownika, którego pożądany jest emitowane z rekordem.  
  
-   <xref:System.Activities.Tracking.CustomTrackingRecord> Są emitowane przez wywołanie metody śledzenia <xref:System.Activities.ActivityContext>.  
  
 W poniższym przykładzie pokazano sposób emitować <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów w ramach działań niestandardowych.  
  
```csharp  
// Create the Custom Tracking Record  
CustomTrackingRecord customRecord = new CustomTrackingRecord("OrderIn")  
{  
    Data =   
    {  
        {"OrderId", 200},  
        {"OrderDate", "20 Aug 2001"}  
    }  
};  
  
// Emit custom tracking record  
context.Track(customRecord);  
```  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania CustomTrackingSample.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
