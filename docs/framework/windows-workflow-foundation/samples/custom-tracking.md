---
title: Niestandardowe śledzenie
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: 2b100b877bbc8c6d830f09a4a59decffde511511
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182838"
---
# <a name="custom-tracking"></a>Niestandardowe śledzenie
W tym przykładzie pokazano, jak utworzyć niestandardowego uczestnika śledzenia i zapisać zawartość danych śledzenia do konsoli. Ponadto w przykładzie pokazano, <xref:System.Activities.Tracking.CustomTrackingRecord> jak emitować obiekty wypełnione danymi zdefiniowanymi przez użytkownika. Uczestnik śledzenia oparty na konsoli <xref:System.Activities.Tracking.TrackingRecord> filtruje obiekty emitowane przez przepływ pracy przy użyciu obiektu profilu śledzenia utworzonego w kodzie.

## <a name="sample-details"></a>Przykładowe szczegóły
 Windows Workflow Foundation (WF) zapewnia infrastrukturę śledzenia do śledzenia wykonywania wystąpienia przepływu pracy. Środowisko uruchomieniowe śledzenia implementuje wystąpienie przepływu pracy do emitowania zdarzeń związanych z cyklem życia przepływu pracy, zdarzeniami z działań przepływu pracy i niestandardowymi zdarzeniami śledzenia. W poniższej tabeli przedstawiono podstawowe składniki infrastruktury śledzenia.

|Składnik|Opis|
|---------------|-----------------|
|Śledzenie środowiska wykonawczego|Zapewnia infrastrukturę do emitowania rekordów śledzenia.|
|Śledzenie uczestników|Zużywa rekordy śledzenia. Program .NET Framework 4 jest dostarczany z uczestnikiem śledzenia, który zapisuje rekordy śledzenia jako zdarzenia śledzenia zdarzeń dla systemu Windows (ETW).|
|Profil śledzenia|Mechanizm filtrowania, który umożliwia uczestnikowi śledzenia subskrybowanie podzbioru rekordów śledzenia emitowanych z wystąpienia przepływu pracy.|

 W poniższej tabeli opisano rekordy śledzenia emitujące środowisko wykonawcze przepływu pracy.

|Rekord śledzenia|Opis|
|---------------------|-----------------|
|Rekordy śledzenia wystąpienia przepływu pracy.|Opisuje cykl życia wystąpienia przepływu pracy. Na przykład rekord wystąpienia jest emitowany po uruchomieniu lub zakończeniu przepływu pracy.|
|Rekordy śledzenia stanu działania.|Szczegóły wykonania działania. Te rekordy wskazują stan działania przepływu pracy, na przykład kiedy działanie jest zaplanowane lub po zakończeniu działania lub gdy zostanie zgłoszony błąd.|
|Rekord wznowienia zakładki.|Emitowana za każdym razem, gdy zakładka w wystąpieniu przepływu pracy zostanie wznowiona.|
|Niestandardowe rekordy śledzenia.|Autor przepływu pracy może tworzyć niestandardowe rekordy śledzenia i emitować je w ramach działania niestandardowego.|

 Uczestnik śledzenia subskrybuje podzbiór <xref:System.Activities.Tracking.TrackingRecord> emitowanych obiektów przy użyciu profilów śledzenia. Profil śledzenia zawiera zapytania śledzenia, które umożliwiają subskrybowanie określonego typu rekordu śledzenia. Profile śledzenia można określić w kodzie lub w konfiguracji.

### <a name="custom-tracking-participant"></a>Uczestnik śledzenia niestandardowego
 Interfejs API uczestnika śledzenia umożliwia rozszerzenie środowiska wykonawczego śledzenia z użytkownikiem <xref:System.Activities.Tracking.TrackingRecord> pod warunkiem uczestnika śledzenia, który może zawierać niestandardową logikę do obsługi obiektów emitowanych przez środowisko wykonawcze przepływu pracy.

 Aby napisać uczestnika śledzenia, <xref:System.Activities.Tracking.TrackingParticipant>użytkownik musi zaimplementować . W szczególności <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> metoda musi być zaimplementowana przez uczestnika niestandardowego. Ta metoda jest <xref:System.Activities.Tracking.TrackingRecord> wywoływana, gdy jest emitowany przez środowisko wykonawcze przepływu pracy.

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 Uczestnik śledzenia całego jest implementowany w pliku ConsoleTrackingParticipant.cs. Poniższy przykład kodu <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> jest metodą dla niestandardowego uczestnika śledzenia.

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

 Poniższy przykład kodu dodaje uczestnika konsoli do invoker przepływu pracy.

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
 W tym przykładzie pokazano <xref:System.Activities.Tracking.CustomTrackingRecord> również możliwość emitowania obiektów z niestandardowego działania przepływu pracy:

- Obiekty <xref:System.Activities.Tracking.CustomTrackingRecord> są tworzone i wypełniane danymi zdefiniowanymi przez użytkownika, które mają być emitowane wraz z rekordem.

- Jest <xref:System.Activities.Tracking.CustomTrackingRecord> emitowany przez wywołanie metody <xref:System.Activities.ActivityContext>ścieżki .

 W poniższym przykładzie <xref:System.Activities.Tracking.CustomTrackingRecord> pokazano, jak emitować obiekty w ramach działania niestandardowego.

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

#### <a name="to-use-this-sample"></a>Aby użyć tej próbki

1. Za pomocą programu Visual Studio 2010 otwórz plik rozwiązania CustomTrackingSample.sln.

2. Aby utworzyć rozwiązanie, naciśnij klawisze CTRL+SHIFT+B.

3. Aby uruchomić rozwiązanie, naciśnij klawisze CTRL+F5.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a>Zobacz też

- [Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
