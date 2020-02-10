---
title: Działanie zasad zewnętrznych w programie .NET Framework 4.5
ms.date: 03/30/2017
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
ms.openlocfilehash: 8fd08c9c29f7a268170aaa101a9bdb85250157dc
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094634"
---
# <a name="externalized-policy-activity-in-net-framework-45"></a>Działanie zasad zewnętrznych w programie .NET Framework 4.5

Ten przykład pokazuje, jak działanie ExternalizedPolicy4 umożliwia wykonywanie istniejących .NET Framework 3,5 Windows Workflow Foundation (WF 3,5) <xref:System.Workflow.Activities.Rules.RuleSet> obiektów w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Windows Workflow Foundation (WF 4,5) bezpośrednio przy użyciu aparatu reguł, który jest dostarczany w programie WF 3,5. Korzystając z tego działania, można otworzyć i wykonać dowolne istniejące <xref:System.Workflow.Activities.Rules.RuleSet>WF 3,5. Aby uzyskać więcej informacji o aparacie reguł WF 3,5 w ramach Windows Workflow Foundation, Przeczytaj [wprowadzenie do aparatu reguł Windows Workflow Foundation](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480193(v=msdn.10)). Aby uzyskać więcej informacji na temat migrowania reguł do [!INCLUDE[wf1](../../../../includes/wf1-md.md)] w [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], zapoznaj się ze [wskazówkami dotyczącymi migracji](../migration-guidance.md).

## <a name="projects-in-this-sample"></a>Projekty w tym przykładzie

|Nazwa projektu|Opis|Pliki główne|
|-|-|-|
|ExternalizedPolicy4|Zawiera działanie ExternalizedPolicy4 i projektanta WF 4,5.|**ExternalizedPolicy4.cs**: definicja działania.<br /><br /> **ExternalizedPolicy4Designer. XAML**: niestandardowy Projektant dla działania ExternalizedPolicy4. Używa edytora reguł (<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>) z aparatu reguł WF 3,5.|
|ImperativeCodeClientSample|Przykładowa aplikacja kliencka, która konfiguruje i uruchamia przepływ pracy za pomocą C# aplikacji ExternalizedPolicy4 przy użyciu kodu bezwzględnego (bez użycia projektanta).|**ApplyDiscount. rules**: plik z definicjami reguł [!INCLUDE[wf1](../../../../includes/wf1-md.md)].<br /><br /> **Order.cs**: typ reprezentujący zamówienie klienta. Reguły są stosowane do obiektów tego typu.<br /><br /> **Program.cs**: konfiguruje i uruchamia przepływ pracy, który ma działanie Policy4 do zastosowania reguł zdefiniowanych w ApplyDiscount. rules do wystąpień obiektów Order.<br /><br /> App. config: plik konfiguracyjny ze ścieżką pliku reguł.|
|DesignerClientSample|Przykładowa aplikacja kliencka, która konfiguruje i uruchamia przepływ pracy za pomocą aplikacji ExternalPolicy4 w projektancie [!INCLUDE[wf1](../../../../includes/wf1-md.md)].|**Sequence1. XAML**: sekwencyjny przepływ pracy, który używa działania Policy4 do wykonywania obliczeń reguł.<br /><br /> **Program.cs**: uruchamia wystąpienie przepływu pracy zdefiniowanego w pliku Sequence1. XAML.|

## <a name="the-externalizedpolicy4-activity"></a>Działanie ExternalizedPolicy4

Działanie ExternalizedPolicy4 jest <xref:System.Activities.NativeActivity>, które umożliwia wykonywanie obiektów <xref:System.Workflow.Activities.Rules.RuleSet> WF 3,5 w ramach przepływów pracy programu WF 4,5. Poniższy przykład jest uproszczoną definicją publicznego modelu obiektów działania.

```csharp
public class ExternalizedPolicy4Activity<TResult>: CodeActivity
{
    public string RulesFilePath

    public string RuleSetName

    [RequiredArgument]
    public InArgument<T> TargetObject

    [RequiredArgument]
    public OutArgument<T> ResultObject

    public OutArgument<ValidationErrorCollection> ValidationErrors
}
```

|Właściwość|Opis|
|-|-|
|RuleSetFilePath|Ścieżka do pliku <xref:System.Workflow.Activities.Rules.RuleSet> .NET Framework 3,5 do oceny, gdy działanie zostanie wykonane.|
|Zestaw reguł|Nazwa <xref:System.Workflow.Activities.Rules.RuleSet>, która ma być używana w pliku reguł.|
|TargetObject|Obiekt, względem którego są oceniane obiekty <xref:System.Workflow.Activities.Rules.Rule> w <xref:System.Workflow.Activities.Rules.RuleSet>.|
|ResultObject|Obiekt wynikowy po zastosowaniu reguł (na przykład reguły są stosowane względem argumentu wejściowego, a wynik jest przechowywany w argumencie wynik.|
|ValidationError|Lista błędów walidacji zwróconych przez aparat reguł WF 3,5 podczas walidacji <xref:System.Workflow.Activities.Rules.RuleSet> względem obiektu docelowego przed wykonaniem.|

## <a name="externalizedpolicy4-activity-designer"></a>ExternalizedPolicy4, Projektant działań

Projektant ExternalizedPolicy4 umożliwia skonfigurowanie działania w taki sposób, aby korzystało z istniejącego zestawu reguł bez pisania kodu. Wystarczy ustawić ścieżkę, w której znajduje się plik. rules, a następnie określić nazwę <xref:System.Workflow.Activities.Rules.RuleSet>, która ma być używana. Umożliwia również modyfikowanie <xref:System.Workflow.Activities.Rules.RuleSet>. Po skompilowaniu rozwiązania można je znaleźć w przyborniku w sekcji Microsoft. Samples. Activities. rules. Projektant umożliwia wybranie pliku reguł i <xref:System.Workflow.Activities.Rules.RuleSet>. Po kliknięciu przycisku **Edytuj zestaw reguł** zostanie wyświetlony <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog> WF 3,5. To okno dialogowe to edytor reguł WF 3,5, który jest używany do wyświetlania i edytowania reguł wykonywanych przez działanie ExternalizedPolicy4.

## <a name="policy4-and-externalpolicy4"></a>Policy4 i ExternalPolicy4

Działanie zasad umożliwia tworzenie i wykonywanie zestawu reguł .NET Framework 3,5 w przepływie pracy WF 4,5. <xref:System.Workflow.Activities.Rules.RuleSet> jest serializowana w tekście definicji XAML działania Policy4. Przykład ExternalizedPolicy4 pokazuje, jak używać istniejącego zewnętrznego <xref:System.Workflow.Activities.Rules.RuleSet> (zawarte w pliku. Rules).

## <a name="use-this-sample"></a>Użyj tego przykładu

Nie jest wymagana żadna specjalna konfiguracja do uruchomienia tego przykładu. Otwórz rozwiązanie w programie Visual Studio, a następnie naciśnij klawisz **F5** , aby uruchomić aplikację.

Ten przykład zawiera dwie aplikacje klienckie: ImperativeCodeClientSample i DesignerClientSample. Klient ImperativeCodeClientSample pokazuje, jak skonfigurować i uruchomić działanie ExternalizedPolicy4 przy użyciu C# kodu bezwzględnego. DesignerClientSample pokazuje, jak skonfigurować i uruchomić działanie ExternalizedPolicy4 przy użyciu narzędzia Projektant.

### <a name="run-the-imperativecodeclientsample-application"></a>Uruchamianie aplikacji ImperativeCodeClientSample

1. Za pomocą programu Visual Studio Otwórz plik rozwiązania *Policy4Sample. sln* .

2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **ImperativeCodeClientSample** , a następnie wybierz pozycję **Ustaw jako projekt startowy**.

3. Aby uruchomić projekt, naciśnij klawisz **Ctrl**+**F5**.

### <a name="run-the-designerclientsample-application"></a>Uruchamianie aplikacji DesignerClientSample

1. Za pomocą programu Visual Studio Otwórz plik rozwiązania *Policy4Sample. sln* .

2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **DesignerClientSample** , a następnie wybierz pozycję **Ustaw jako projekt startowy**.

3. Naciśnij klawisz **Ctrl**+**SHIFT**+**B** , aby skompilować projekt.

4. Naciśnij klawisz **Ctrl**+**F5** , aby uruchomić projekt.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].
>
> Ten przykład znajduje się w następującym katalogu:
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`
