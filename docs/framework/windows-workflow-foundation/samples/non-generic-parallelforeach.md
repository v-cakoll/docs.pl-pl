---
title: Nieogólne działanie ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 52b851686ea2fdc8c573a0622fe91ca5e205edeb
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637733"
---
# <a name="non-generic-parallelforeach"></a>Nieogólne działanie ParallelForEach

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] jest dostarczany w przyborniku jej zestaw działań przepływu sterowania, w tym <xref:System.Activities.Statements.ParallelForEach%601>, co pozwala iteracja <xref:System.Collections.Generic.IEnumerable%601> kolekcji.

<xref:System.Activities.Statements.ParallelForEach%601> wymaga jego <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> właściwość typu <xref:System.Collections.Generic.IEnumerable%601>. Użytkownicy to wyklucza z Iterowanie struktur danych, które implementują <xref:System.Collections.Generic.IEnumerable%601> interfejsu (na przykład <xref:System.Collections.ArrayList>). Wersja nieogólnego <xref:System.Activities.Statements.ParallelForEach%601> pozwala pokonać ten wymóg, kosztem więcej złożoności środowiska wykonawczego dla zapewnienia zgodności z typów wartości w kolekcji.

Ten przykład przedstawia sposób implementowania nieogólnego <xref:System.Activities.Statements.ParallelForEach%601> działanie i jego projektanta. To działanie może służyć do iterowania po <xref:System.Collections.ArrayList>.

## <a name="parallelforeach-activity"></a>Działanie ParallelForEach

C# /VB `foreach` instrukcji wylicza elementów kolekcji, wykonywania osadzonych instrukcji dla każdego elementu kolekcji. [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Są równoważne działania <xref:System.Activities.Statements.ForEach%601> i <xref:System.Activities.Statements.ParallelForEach%601>. <xref:System.Activities.Statements.ForEach%601> Aktywności zawiera listę wartości i treść. W czasie wykonywania jest postanowiliśmy listy, a następnie zostaje wykonana dla każdej wartości na liście.

<xref:System.Activities.Statements.ParallelForEach%601> ma <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, dzięki czemu <xref:System.Activities.Statements.ParallelForEach%601> działania można ukończyć wcześnie, jeśli oceny <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> zwraca `true`. <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Jest oceniane, po zakończeniu każdej iteracji.

W większości przypadków ogólnego wersję działania powinny być preferowanym rozwiązaniem, ponieważ obejmuje większość scenariuszy, w których jest używany i zawiera typ sprawdzanie w czasie kompilacji. Wersja nieogólnego może służyć do iteracji przez typy, które implementują niepodstawowy <xref:System.Collections.IEnumerable> interfejsu.

## <a name="class-definition"></a>Definicja klasy

Poniższy przykład kodu pokazuje definicji nieogólnego `ParallelForEach` jest działanie.

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
<xref:System.Activities.ActivityAction> Typu <xref:System.Object>, które jest wykonywane dla każdego elementu w kolekcji. Każdego pojedynczego elementu jest przekazywane do treści jego właściwość argumentu.

Wartości (opcjonalnie) \
Kolekcja elementów, które są powtarzana. Upewnić się, że wszystkie elementy kolekcji są zgodnych typów odbywa się w czasie wykonywania.

CompletionCondition (opcjonalnie) \
<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Właściwość jest oceniane, po zakończeniu dowolną iterację. Jeśli daje w wyniku `true`, następnie zaplanowane do czasu iteracji są anulowane. Jeśli ta właściwość nie jest ustawiona, wszystkie działania w kolekcji gałęzi jest wykonywanie aż do zakończenia.

## <a name="example-of-using-parallelforeach"></a>Przykład użycia ParallelForEach

Poniższy kod przedstawia sposób użycia działanie ParallelForEach w aplikacji.

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

Projektant działań dla przykładu przypomina projektanta podane dla wbudowanej <xref:System.Activities.Statements.ParallelForEach%601> działania. Pojawi się okno projektanta w przyborniku, w **przykłady**, **działania Nieuniwersalne** kategorii. Projektant jest o nazwie **ParallelForEachWithBodyFactory** w przyborniku, ponieważ ujawnia działania <xref:System.Activities.Presentation.IActivityTemplateFactory> w przyborniku, który tworzy działanie z prawidłowo skonfigurowane <xref:System.Activities.ActivityAction>.

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

1. Ustaw projekt wybranego jako projekt startowy rozwiązania.

    1. **CodeTestClient** pokazuje, jak użyć działania przy użyciu kodu.

    2. **DesignerTestClient** pokazuje, jak użyć działania w projektancie.

2. Skompiluj i uruchom projekt.

> [!IMPORTANT]
> Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
