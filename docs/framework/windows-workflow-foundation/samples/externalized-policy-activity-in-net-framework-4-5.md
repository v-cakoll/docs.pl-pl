---
title: Działanie zasad zewnętrznych w programie .NET Framework 4.5
ms.date: 03/30/2017
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
ms.openlocfilehash: 7d3c9b2bd9da7e3793479c002094504a4a556aa0
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989569"
---
# <a name="externalized-policy-activity-in-net-framework-45"></a>Działanie zasad zewnętrznych w programie .NET Framework 4.5

W tym przykładzie pokazano, jak działanie ExternalizedPolicy4 umożliwia wykonywanie [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] istniejących obiektów Windows Workflow Foundation (WF <xref:System.Workflow.Activities.Rules.RuleSet> 3,5) [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] w Windows Workflow Foundation (WF 4,5) bezpośrednio przy użyciu aparatu reguł jest dostarczany w WF 3,5. Korzystając z tego działania, można otworzyć i wykonać dowolne istniejące WF 3,5 <xref:System.Workflow.Activities.Rules.RuleSet>. Aby uzyskać więcej informacji o aparacie reguł WF 3,5 w ramach Windows Workflow Foundation, Przeczytaj [wprowadzenie do aparatu reguł Windows Workflow Foundation](https://go.microsoft.com/fwlink/?LinkId=166079). Aby uzyskać więcej informacji o migrowaniu [!INCLUDE[wf1](../../../../includes/wf1-md.md)] reguł [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]do programu w programie, zapoznaj się ze wskazówkami dotyczącymi migracji w temacie [wskazówki dotyczące migracji](../migration-guidance.md).

## <a name="projects-in-this-sample"></a>Projekty w tym przykładzie

|Nazwa projektu|Opis|Pliki główne|
|-|-|-|
|ExternalizedPolicy4|Zawiera działanie ExternalizedPolicy4 i projektanta WF 4,5.|**ExternalizedPolicy4.cs**: definicja działania.<br /><br /> **ExternalizedPolicy4Designer. XAML**: Niestandardowy Projektant dla działania ExternalizedPolicy4. Używa edytora reguł (<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>) z aparatu reguł WF 3,5.|
|ImperativeCodeClientSample|Przykładowa aplikacja kliencka, która konfiguruje i uruchamia przepływ pracy za pomocą C# aplikacji ExternalizedPolicy4 przy użyciu kodu bezwzględnego (bez użycia projektanta).|**ApplyDiscount. rules**: Plik z [!INCLUDE[wf1](../../../../includes/wf1-md.md)] definicjami reguł.<br /><br /> **Order.cs**: Typ reprezentujący zamówienie klienta. Reguły są stosowane do obiektów tego typu.<br /><br /> **Program.cs**: Służy do konfigurowania i uruchamiania przepływu pracy, który ma działanie Policy4 do zastosowania reguł zdefiniowanych w ApplyDiscount. rules do wystąpień obiektów Order.<br /><br /> App.config: Plik konfiguracyjny ze ścieżką pliku reguł.|
|DesignerClientSample|Przykładowa aplikacja kliencka, która konfiguruje i uruchamia przepływ pracy za pomocą [!INCLUDE[wf1](../../../../includes/wf1-md.md)] aplikacji ExternalPolicy4 w projektancie.|**Sequence1. XAML**: Sekwencyjny przepływ pracy, który używa działania Policy4 do wykonywania obliczeń reguł.<br /><br /> **Program.cs**: Uruchamia wystąpienie przepływu pracy zdefiniowanego w Sequence1. XAML.|

## <a name="the-externalizedpolicy4-activity"></a>Działanie ExternalizedPolicy4

Działanie ExternalizedPolicy4 to <xref:System.Activities.NativeActivity> funkcja, która umożliwia wykonywanie obiektów WF <xref:System.Workflow.Activities.Rules.RuleSet> 3,5 w ramach przepływów pracy programu WF 4,5. Poniższy przykład jest uproszczoną definicją publicznego modelu obiektów działania.

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
|RuleSetFilePath|Ścieżka do pliku .NET Framework 3,5 <xref:System.Workflow.Activities.Rules.RuleSet> do oceny, gdy działanie zostanie wykonane.|
|Zestaw reguł|Nazwa, <xref:System.Workflow.Activities.Rules.RuleSet> która ma być używana w pliku reguł.|
|TargetObject|Obiekt, względem którego <xref:System.Workflow.Activities.Rules.Rule> <xref:System.Workflow.Activities.Rules.RuleSet> są oceniane obiekty w elemencie.|
|ResultObject|Obiekt wynikowy po zastosowaniu reguł (na przykład reguły są stosowane względem argumentu wejściowego, a wynik jest przechowywany w argumencie wynik.|
|ValidationError|Lista błędów walidacji zwróconych przez aparat reguł WF 3,5 podczas walidacji <xref:System.Workflow.Activities.Rules.RuleSet> obiektu docelowego przed wykonaniem.|

## <a name="externalizedpolicy4-activity-designer"></a>ExternalizedPolicy4, Projektant działań

Projektant ExternalizedPolicy4 umożliwia skonfigurowanie działania w taki sposób, aby korzystało z istniejącego zestawu reguł bez pisania kodu. Po prostu Ustaw ścieżkę, w której znajduje się plik. rules, <xref:System.Workflow.Activities.Rules.RuleSet> a następnie określ nazwę, która ma być używana. Umożliwia również modyfikowanie <xref:System.Workflow.Activities.Rules.RuleSet>. Po skompilowaniu rozwiązania można je znaleźć w przyborniku w sekcji Microsoft. Samples. Activities. rules. Projektant umożliwia wybranie pliku. rules i <xref:System.Workflow.Activities.Rules.RuleSet>. Po kliknięciu przycisku **Edytuj zestaw reguł** zostanie wyświetlona funkcja <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog> WF 3,5. To okno dialogowe to edytor reguł WF 3,5, który jest używany do wyświetlania i edytowania reguł wykonywanych przez działanie ExternalizedPolicy4.

## <a name="policy4-and-externalpolicy4"></a>Policy4 i ExternalPolicy4

Działanie zasad umożliwia tworzenie i wykonywanie zestawu reguł .NET Framework 3,5 w przepływie pracy WF 4,5. <xref:System.Workflow.Activities.Rules.RuleSet> Jest serializowany w tekście definicji XAML działania Policy4. Przykład ExternalizedPolicy4 pokazuje, jak używać istniejącego zewnętrznego <xref:System.Workflow.Activities.Rules.RuleSet> (zawartego w pliku. Rules).

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

3. Naciśnij **klawisze CTRL**+**SHIFT**+**B** , aby skompilować projekt.

4. Naciśnij klawisz **Ctrl**+**F5** , aby uruchomić projekt.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.
>
> Ten przykład znajduje się w następującym katalogu:
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`
