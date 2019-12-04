---
title: Niestandardowe śledzenie
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: 0d9bd9262c6fc13a36fb7736245fa244ee61d8c3
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710885"
---
# <a name="custom-tracking"></a>Niestandardowe śledzenie
Ten przykład pokazuje, jak utworzyć niestandardowego uczestnika śledzenia i zapisać zawartość śledzenia danych w konsoli programu. Ponadto przykład pokazuje, jak emitować obiekty <xref:System.Activities.Tracking.CustomTrackingRecord> wypełnione danymi zdefiniowanymi przez użytkownika. Uczestnik śledzenia oparty na konsoli filtruje <xref:System.Activities.Tracking.TrackingRecord> obiekty emitowane przez przepływ pracy przy użyciu obiektu profil śledzenia utworzonego w kodzie.

## <a name="sample-details"></a>Przykładowe szczegóły
 Windows Workflow Foundation (WF) oferuje infrastrukturę śledzenia do śledzenia wykonywania wystąpienia przepływu pracy. Środowisko uruchomieniowe śledzenia implementuje wystąpienie przepływu pracy, aby emitować zdarzenia związane z cyklem życia przepływu pracy, zdarzenia z działań przepływu pracy i niestandardowe zdarzenia śledzenia. W poniższej tabeli przedstawiono podstawowe składniki infrastruktury śledzenia.

|Składnik|Opis|
|---------------|-----------------|
|Śledzenie środowiska uruchomieniowego|Udostępnia infrastrukturę do emisji rekordów śledzenia.|
|Śledzenie uczestników|Używa rekordów śledzenia. .NET Framework 4 dostarcza uczestnika śledzenia, który zapisuje rekordy śledzenia jako zdarzenia śledzenia zdarzeń systemu Windows (ETW).|
|Profil śledzenia|Mechanizm filtrowania umożliwiający uczestnikom śledzenia subskrybowanie podzbioru rekordów śledzenia emitowanych z wystąpienia przepływu pracy.|

 W poniższej tabeli przedstawiono szczegółowe informacje o rekordach śledzenia, które są emitowane przez środowisko uruchomieniowe przepływu pracy.

|Rekord śledzenia|Opis|
|---------------------|-----------------|
|Rekordy śledzenia wystąpienia przepływu pracy.|Opisuje cykl życia wystąpienia przepływu pracy. Na przykład rekord wystąpienia jest emitowany, gdy przepływ pracy zostanie uruchomiony lub zakończony.|
|Rekordy śledzenia stanu działania.|Szczegóły wykonywania działania. Te rekordy wskazują stan działania przepływu pracy, np. Kiedy działanie zostało zaplanowane lub gdy działanie zostało zakończone lub gdy zostanie zgłoszony błąd.|
|Rekord wznowienia zakładki.|Emitowane za każdym razem, gdy zostanie wznowiona Zakładka w wystąpieniu przepływu pracy.|
|Niestandardowe rekordy śledzenia.|Autor przepływu pracy może tworzyć niestandardowe rekordy śledzenia i emitować je w ramach działania niestandardowego.|

 Uczestnik śledzenia subskrybuje podzbiór wyemitowanych <xref:System.Activities.Tracking.TrackingRecord> obiektów przy użyciu profilów śledzenia. Profil śledzenia zawiera kwerendy śledzenia, które umożliwiają subskrybowanie określonego typu rekordu śledzenia. Profile śledzenia można określić w kodzie lub w konfiguracji.

### <a name="custom-tracking-participant"></a>Uczestnik śledzenia niestandardowego
 Interfejs API uczestnika śledzenia umożliwia rozszerzenie środowiska uruchomieniowego śledzenia przy użyciu dostarczonego przez użytkownika uczestnika śledzenia, który może uwzględniać logikę niestandardową do obsługi <xref:System.Activities.Tracking.TrackingRecord> obiektów emitowanych przez środowisko uruchomieniowe przepływu pracy.

 Aby napisać uczestnika śledzenia, użytkownik musi zaimplementować <xref:System.Activities.Tracking.TrackingParticipant>. W od<xref:System.Activities.Tracking.TrackingParticipant.Track%2A> Metoda musi być implementowana przez uczestnika niestandardowego. Ta metoda jest wywoływana, gdy <xref:System.Activities.Tracking.TrackingRecord> jest emitowany przez środowisko uruchomieniowe przepływu pracy.

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 Pełny Uczestnik śledzenia jest implementowany w pliku ConsoleTrackingParticipant.cs. Poniższy przykład kodu jest metodą <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> niestandardowego uczestnika śledzenia.

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

 Poniższy przykład kodu dodaje uczestnika konsoli do przepływu pracy źródło.

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

### <a name="emitting-custom-tracking-records"></a>Emitowanie niestandardowych rekordów śledzenia
 Ten przykład ilustruje również możliwość emitowania <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów z niestandardowego działania przepływu pracy:

- Obiekty <xref:System.Activities.Tracking.CustomTrackingRecord> są tworzone i wypełniane danymi zdefiniowanymi przez użytkownika, które są wymagane do emisji z rekordem.

- <xref:System.Activities.Tracking.CustomTrackingRecord> jest emitowany przez wywołanie metody Track <xref:System.Activities.ActivityContext>.

 W poniższym przykładzie pokazano, jak emitować <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów w działaniu niestandardowym.

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

1. Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania CustomTrackingSample. sln.

2. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

3. Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady monitorowania oprogramowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
