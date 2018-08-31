---
title: Działanie zasad zewnętrznych w programie .NET Framework 4.5
ms.date: 03/30/2017
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
ms.openlocfilehash: a98dedace72ef9d43d9b65335b462f6ad4f649b0
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254410"
---
# <a name="externalized-policy-activity-in-net-framework-45"></a>Działanie zasad zewnętrznych w programie .NET Framework 4.5

Niniejszy przykład pokazuje, jak działanie ExternalizedPolicy4 zezwala na wykonywanie istniejącej [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Windows Workflow Foundation (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> obiekty w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Windows Workflow Foundation (WF 4.5) bezpośrednio przy użyciu aparatu reguł który jest dostarczany w WF 3.5. Korzystając z tego działania, można otwierać i wykonać wszelkie istniejące 3.5 WF <xref:System.Workflow.Activities.Rules.RuleSet>. Aby uzyskać więcej informacji na temat aparatu reguł 3.5 WF wchodzącego w skład Windows Workflow Foundation, przeczytaj [wprowadzenie do aparatu reguł programu Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkId=166079). Aby uzyskać więcej informacji o migrowaniu reguły do [!INCLUDE[wf1](../../../../includes/wf1-md.md)] w [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], należy przeczytać wskazówki dotyczące migracji w [wskazówek dotyczących migracji](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md).

## <a name="projects-in-this-sample"></a>Projekty w tym przykładzie

|Nazwa projektu|Opis|Pliki główne|
|-|-|-|
|ExternalizedPolicy4|Zawiera działanie ExternalizedPolicy4 i swojego projektanta 4.5 programu WF.|**ExternalizedPolicy4.cs**: definicji działania.<br /><br /> **ExternalizedPolicy4Designer.xaml**: niestandardowego projektanta ExternalizedPolicy4 działania. Użyto Edytora reguł (<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>) od aparatu reguł programu WF 3.5.|
|ImperativeCodeClientSample|Przykładowa aplikacja kliencka, konfiguruje, która uruchamia przepływ pracy przy użyciu aplikacji ExternalizedPolicy4 przy użyciu języka C# kodu imperatywnego (Projektant nie jest używany).|**ApplyDiscount.rules**: plik z [!INCLUDE[wf1](../../../../includes/wf1-md.md)] reguły definicji.<br /><br /> **ORDER.cs**: typ, który reprezentuje zamówienia klienta. Reguły są stosowane do obiektów tego typu.<br /><br /> **Plik program.cs**: konfiguruje i uruchamia przepływ pracy, który ma działanie Policy4 można zastosować reguł zdefiniowanych w ApplyDiscount.rules do wystąpień obiektów zamówienia.<br /><br /> Pliku App.config: Plik konfiguracji ze ścieżką do pliku reguł.|
|DesignerClientSample|Przykładowa aplikacja kliencka, która umożliwia skonfigurowanie i uruchamia przepływ pracy przy użyciu aplikacji ExternalPolicy4 w [!INCLUDE[wf1](../../../../includes/wf1-md.md)] projektanta.|**Sequence1.XAML**: sekwencyjny przepływ pracy, który używa działania Policy4 podczas przeprowadzania oceny reguł.<br /><br /> **Plik program.cs**: uruchamia wystąpienie przepływu pracy zdefiniowane w Sequence1.xaml.|

## <a name="the-externalizedpolicy4-activity"></a>Działanie ExternalizedPolicy4

To działanie ExternalizedPolicy4 <xref:System.Activities.NativeActivity> umożliwiająca wykonywanie WF 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> obiektów w ramach przepływów pracy WF 4.5. Poniższy przykład jest uproszczone definicję modelu obiektu publicznego działania.

```
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
|RuleSetFilePath|Ścieżka do programu .NET Framework 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> plik ma zostać obliczone, gdy jest wykonywane działanie.|
|RuleSetName|Nazwa <xref:System.Workflow.Activities.Rules.RuleSet> do użycia w pliku rules.|
|TargetObject|Obiekt, dla którego <xref:System.Workflow.Activities.Rules.Rule> obiekty w <xref:System.Workflow.Activities.Rules.RuleSet> zostaną ocenione względem.|
|Obiektu wyników wystąpiły pełne|Wynikowy obiekt po zastosowaniu zasad (na przykład reguły są stosowane względem argumentu dane wejściowe i wynik jest przechowywany w argumencie wynik.|
|ValidationError|Lista błędów sprawdzania poprawności zwrócony przez aparat reguł WF 3.5, podczas sprawdzania poprawności <xref:System.Workflow.Activities.Rules.RuleSet> względem obiektu docelowego, przed wykonaniem.|

## <a name="externalizedpolicy4-activity-designer"></a>ExternalizedPolicy4, Projektant działań

Projektant ExternalizedPolicy4 umożliwia skonfigurowanie działania, aby użyć istniejącego zestawu reguł bez konieczności pisania kodu. Po prostu Ustaw ścieżkę, w którym znajduje się plik Rules i określ <xref:System.Workflow.Activities.Rules.RuleSet> nazwa ma zostać użyta. Umożliwia również modyfikowanie <xref:System.Workflow.Activities.Rules.RuleSet>. Po utworzeniu rozwiązania, znajdują się on w przyborniku w sekcji Microsoft.Samples.Activities.Rules. Projektant umożliwia wybranie pliku Rules i <xref:System.Workflow.Activities.Rules.RuleSet>. Gdy **Edytuj zestaw reguł** przycisku, programu WF 3.5 <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog> jest wyświetlana. To okno dialogowe jest ponownie hostowanej edytora reguł WF 3.5 i jest używany do wyświetlania i edytowania reguły, które wykonuje działania ExternalizedPolicy4.

## <a name="policy4-and-externalpolicy4"></a>Policy4 i ExternalPolicy4

[Działanie zasad w programie .NET Framework 4.5](../../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) działanie umożliwia tworzenie i wykonywanie zestawu reguł .NET Framework 3.5 w przepływie pracy programu WF 4.5. <xref:System.Workflow.Activities.Rules.RuleSet> Jest serializowane wbudowanych w działaniu Policy4 definicji XAML. Przykładowe ExternalizedPolicy4 pokazuje, jak użyć istniejącej zewnętrznych <xref:System.Workflow.Activities.Rules.RuleSet> (znajdujących się w pliku Rules).

## <a name="use-this-sample"></a>Użyj tego przykładu

Nie specjalne konfiguracji wymaganej do uruchomienia tego przykładu. Otwórz rozwiązanie w programie Visual Studio, a następnie naciśnij klawisz **F5** do uruchomienia aplikacji.

Ten przykład zawiera dwie aplikacje klienckie: ImperativeCodeClientSample i DesignerClientSample. Klient ImperativeCodeClientSample pokazuje, jak skonfigurować i uruchomić działanie ExternalizedPolicy4 przy użyciu kodu imperatywnego C#. DesignerClientSample pokazuje, jak skonfigurować i uruchomić działanie ExternalizedPolicy4 za pomocą projektanta.

### <a name="run-the-imperativecodeclientsample-application"></a>Uruchom aplikację ImperativeCodeClientSample

1.  Za pomocą programu Visual Studio, otwórz *Policy4sample.sln* pliku rozwiązania.

2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ImperativeCodeClientSample** projektu, a następnie wybierz pozycję **Ustaw jako projekt startowy**.

3.  Aby uruchomić projekt, naciśnij klawisz **Ctrl**+**F5**.

### <a name="run-the-designerclientsample-application"></a>Uruchom aplikację DesignerClientSample

1.  Za pomocą programu Visual Studio, otwórz *Policy4sample.sln* pliku rozwiązania.

2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DesignerClientSample** projektu, a następnie wybierz pozycję **Ustaw jako projekt startowy**.

3.  Naciśnij klawisz **Ctrl**+**Shift**+**B** do skompilowania projektu.

4.  Naciśnij klawisz **Ctrl**+**F5** Aby uruchomić projekt.

> [!IMPORTANT]
> Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.
>
> W tym przykładzie znajduje się w następującym katalogu:
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`
