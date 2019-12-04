---
title: Nieogólny ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 33e0c8ef8c04b7d58815760ae1152f63891fdfd5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715643"
---
# <a name="non-generic-parallelforeach"></a>Nieogólny ParallelForEach

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] dostarcza w swoim przyborniku zestaw działań przepływu sterowania, w tym <xref:System.Activities.Statements.ParallelForEach%601>, które umożliwiają iterację przez kolekcje <xref:System.Collections.Generic.IEnumerable%601>.

<xref:System.Activities.Statements.ParallelForEach%601> wymaga, aby Właściwość <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> była typu <xref:System.Collections.Generic.IEnumerable%601>. Uniemożliwia to użytkownikom iterację struktur danych, które implementują interfejs <xref:System.Collections.Generic.IEnumerable%601> (na przykład <xref:System.Collections.ArrayList>). Nieogólna wersja <xref:System.Activities.Statements.ParallelForEach%601> przekroczy to wymaganie, kosztem większej złożoności w czasie wykonywania w celu zapewnienia zgodności typów wartości w kolekcji.

Ten przykład pokazuje, jak zaimplementować nieogólne działanie <xref:System.Activities.Statements.ParallelForEach%601> i jego projektanta. To działanie może służyć do iterowania przez <xref:System.Collections.ArrayList>.

## <a name="parallelforeach-activity"></a>Działanie ParallelForEach

Instrukcja C#/VB `foreach` wylicza elementy kolekcji, wykonując osadzoną instrukcję dla każdego elementu kolekcji. [!INCLUDE[wf1](../../../../includes/wf1-md.md)] równoważne działania są <xref:System.Activities.Statements.ForEach%601> i <xref:System.Activities.Statements.ParallelForEach%601>. Działanie <xref:System.Activities.Statements.ForEach%601> zawiera listę wartości i treść. W czasie wykonywania lista jest powtarzana i jest wykonywana dla każdej wartości na liście.

<xref:System.Activities.Statements.ParallelForEach%601> ma <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, dzięki czemu działanie <xref:System.Activities.Statements.ParallelForEach%601> może zakończyć się wcześnie, jeśli Obliczanie <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> zwraca `true`. <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> jest oceniane po zakończeniu każdej iteracji.

W większości przypadków ogólna wersja działania powinna być preferowanym rozwiązaniem, ponieważ obejmuje większość scenariuszy, w których jest używana, i zapewnia kontrolę typu w czasie kompilacji. Wersja nieogólna może być używana do iterowania za pomocą typów implementujących nieogólny interfejs <xref:System.Collections.IEnumerable>.

## <a name="class-definition"></a>Definicja klasy

Poniższy przykład kodu pokazuje definicję działania nieogólnego `ParallelForEach`.

```csharp
[ContentProperty("Body")]
public class ParallelForEach : NativeActivity
{
    [RequiredArgument]
    [DefaultValue(null)]
    InArgument<IEnumerable> Values { get; set; }

    [DefaultValue(null)]
    [DependsOn("Values")]
    public Activity<bool> CompletionCondition
    [DefaultValue(null)]
    [DependsOn("CompletionCondition")]
    ActivityAction<object> Body { get; set; }
}
```

Treść (opcjonalnie) \
<xref:System.Activities.ActivityAction> typu <xref:System.Object>, który jest wykonywany dla każdego elementu w kolekcji. Każdy pojedynczy element jest przesyłany do treści za pomocą jego właściwości argument.

Wartości (opcjonalnie) \
Kolekcja elementów, które są powtarzane. Upewnienie się, że wszystkie elementy kolekcji są zgodne typy wykonywane w czasie wykonywania.

CompletionCondition (opcjonalnie) \
Właściwość <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> jest szacowana po zakończeniu każdej iteracji. Jeśli zostanie obliczona `true`, zaplanowane oczekujące iteracje zostaną anulowane. Jeśli ta właściwość nie jest ustawiona, wszystkie działania w kolekcji gałęzi są wykonywane do momentu ukończenia.

## <a name="example-of-using-parallelforeach"></a>Przykład użycia ParallelForEach

Poniższy kod ilustruje sposób używania działania ParallelForEach w aplikacji.

```csharp
string[] names = { "bill", "steve", "ray" };

DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };

Activity sampleUsage =
    new ParallelForEach
    {
       Values = new InArgument<IEnumerable>(c=> names),
       Body = new ActivityAction<object>
       {
           Argument = iterationVariable,
           Handler = new WriteLine
           {
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))
           }
       }
   };
```

## <a name="parallelforeach-designer"></a>Projektant ParallelForEach

Projektant działań dla przykładu jest podobny do projektanta dostępnego dla wbudowanego działania <xref:System.Activities.Statements.ParallelForEach%601>. Projektant pojawia się w przyborniku w kategorii **przykłady**, **nieogólne działania** . Projektant ma nazwę **ParallelForEachWithBodyFactory** w przyborniku, ponieważ działanie uwidacznia <xref:System.Activities.Presentation.IActivityTemplateFactory> w przyborniku, który tworzy działanie z prawidłowo skonfigurowanym <xref:System.Activities.ActivityAction>.

```csharp
public sealed class ParallelForEachWithBodyFactory : IActivityTemplateFactory
{
    public Activity Create(DependencyObject target)
    {
        return new Microsoft.Samples.Activities.Statements.ParallelForEach()
        {
            Body = new ActivityAction<object>()
            {
                Argument = new DelegateInArgument<object>()
                {
                    Name = "item"
                }
            }
        };
    }
}
```

## <a name="to-run-the-sample"></a>Aby uruchomić przykład

1. Ustaw wybrany projekt jako projekt startowy rozwiązania.

    1. **CodeTestClient** pokazuje, jak używać działania przy użyciu kodu.

    2. **DesignerTestClient** pokazuje, jak używać działania w projektancie.

2. Skompiluj i Uruchom projekt.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
