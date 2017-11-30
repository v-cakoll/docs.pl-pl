---
title: "Niestandardowe śledzenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3a32e76bdee87d6f00a5f01893e76ccb3de9ef51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="custom-tracking"></a>Niestandardowe śledzenia
W tym przykładzie pokazano, jak utworzyć uczestnika niestandardowych śledzenia i zapisanie zawartości dane śledzenia do konsoli. Ponadto przykładzie pokazano, jak Emituj <xref:System.Activities.Tracking.CustomTrackingRecord> dane zdefiniowanego przez obiekty wypełnione z użytkownikiem. Filtry uczestnika opartych na konsoli śledzenia <xref:System.Activities.Tracking.TrackingRecord> obiektów emitowanych przez przepływ pracy korzystający z profilu śledzenia obiektu utworzonego w kodzie.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 [!INCLUDE[wf](../../../../includes/wf-md.md)]zapewnia infrastrukturę śledzenia, aby śledzić wykonywania wystąpienia przepływu pracy. Środowisko uruchomieniowe śledzenia implementuje wystąpienia przepływu pracy do wysyłania zdarzeń związanych z cyklem życia przepływu pracy, zdarzenia z działań przepływu pracy i niestandardowych śledzenia zdarzeń. W poniższej tabeli przedstawiono podstawowe składniki infrastruktury śledzenia.  
  
|Składnik|Opis|  
|---------------|-----------------|  
|Śledzenie czasu wykonywania|Zapewnia infrastrukturę do emisji rekordów śledzenia.|  
|Uczestników śledzenia|Wykorzystuje rekordy śledzenia. [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]jest dostarczany z uczestnika śledzenia, który zapisuje rekordy śledzenia jako zdarzenia funkcji Śledzenie zdarzeń systemu Windows ().|  
|Profil śledzenia|Mechanizm filtrowania, który umożliwia śledzenie uczestnika do subskrybowania dla podzestawu rekordów śledzenia wyemitowanego z wystąpieniem przepływu pracy.|  
  
 W poniższej tabeli przedstawiono rekordy śledzenia emitowane środowiska uruchomieniowego przepływu pracy.  
  
|Rekord śledzenia|Opis|  
|---------------------|-----------------|  
|Rejestruje śledzenia wystąpienia przepływu pracy.|W tym artykule opisano cyklu życia wystąpienia przepływu pracy. Na przykład wystąpienia rekord jest emitowany podczas uruchamiania przepływu pracy, lub zakończy.|  
|Stan śledzenia zapisów czynności.|Szczegóły wykonywania działania. Te rekordy wskazują stan działania przepływu pracy, takie jak kiedy zaplanowano działania lub po ukończeniu działania lub gdy zostanie zgłoszony błąd.|  
|Zakładki wznowienie rekordu.|Emitowane zawsze, gdy zostanie wznowione zakładki w ramach wystąpienia przepływu pracy.|  
|Śledzenie niestandardowych rekordów.|Autor przepływu pracy można tworzyć niestandardowych rekordów śledzenia i wysyłać je w ramach działania niestandardowego.|  
  
 Subskrybuje uczestnika śledzenia dla podzbioru emitowany <xref:System.Activities.Tracking.TrackingRecord> obiektów przy użyciu profilów śledzenia. Profil śledzenia zawiera śledzenia zapytań, które umożliwia subskrybowania śledzenia określonego typu rekordu. Śledzenie profile można określić w kodzie, lub w konfiguracji.  
  
### <a name="custom-tracking-participant"></a>Niestandardowe śledzenia uczestnika  
 Uczestnik śledzenia interfejsu API umożliwia rozszerzenie środowiska uruchomieniowego śledzenia z uczestnika śledzenia podane przez użytkownika, które mogą uwzględniać niestandardowej logiki do obsługi <xref:System.Activities.Tracking.TrackingRecord> obiektów emitowanych przez środowisko wykonawcze przepływu pracy.  
  
 Można zapisać do śledzenia uczestnika użytkownik musi implementować <xref:System.Activities.Tracking.TrackingParticipant>. W szczególności <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> — metoda musi być implementowana przez uczestnika niestandardowych. Ta metoda jest wywoływana, gdy <xref:System.Activities.Tracking.TrackingRecord> są emitowane przez środowisko uruchomieniowe przepływu pracy.  
  
```csharp  
public abstract class TrackingParticipant  
{  
    protected TrackingParticipant();  
  
    public virtual TrackingProfile TrackingProfile { get; set; }  
    public abstract void Track(TrackingRecord record, TimeSpan timeout);  
}  
```  
  
 Uczestnik pełną śledzenia jest zaimplementowana w pliku ConsoleTrackingParticipant.cs. Następujący przykładowy kod to <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> metoda uczestnika śledzenia niestandardowych.  
  
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
  
 Poniższy przykładowy kod dodaje uczestnika konsoli do wywołującego przepływu pracy.  
  
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
  
### <a name="emitting-custom-tracking-records"></a>Emitowanie śledzenia niestandardowych rekordów  
 W tym przykładzie przedstawiono również możliwość Emituj <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów z działania niestandardowego przepływu pracy:  
  
-   <xref:System.Activities.Tracking.CustomTrackingRecord> Obiekty są tworzone i wypełniane przy użyciu danych zdefiniowane przez użytkownika wymagane jest, aby emitować z rekordem.  
  
-   <xref:System.Activities.Tracking.CustomTrackingRecord> Są emitowane przez wywołanie metody Śledź <xref:System.Activities.ActivityContext>.  
  
 W poniższym przykładzie pokazano sposób Emituj <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów w ramach działania niestandardowego.  
  
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
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania CustomTrackingSample.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
