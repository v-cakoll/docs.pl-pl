---
title: "Działania ParallelForEach inny niż ogólny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 266e9468eef0a78f87b37f75ed19c5d5d3b99994
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="non-generic-parallelforeach"></a>Działania ParallelForEach inny niż ogólny
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]jest dostarczany w przyborniku jego zestaw działań przepływu sterowania, w tym <xref:System.Activities.Statements.ParallelForEach%601>, dzięki czemu iteracja <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` kolekcji.  
  
 <xref:System.Activities.Statements.ParallelForEach%601>wymaga jego <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> właściwości typu <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`. To wyklucza użytkowników z Iterowanie za pośrednictwem struktury danych, które implementują <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` interfejsu (na przykład <xref:System.Collections.ArrayList>). Wersja nieogólnego <xref:System.Activities.Statements.ParallelForEach%601> pozwala pokonać to wymaganie, kosztem bardziej złożona czasu wykonywania dla zapewnienia zgodności z typów wartości w kolekcji.  
  
 W tym przykładzie pokazano, jak wdrożyć nieogólnego <xref:System.Activities.Statements.ParallelForEach%601> działanie i jego projektanta. To działanie może służyć do iterowania po <xref:System.Collections.ArrayList>.  
  
## <a name="parallelforeach-activity"></a>Działania ParallelForEach działania  
 C# /VB `foreach` instrukcji wylicza elementy kolekcji, wykonywania osadzona instrukcja dla każdego elementu w kolekcji. [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Są równoważne działania <xref:System.Activities.Statements.ForEach%601> i <xref:System.Activities.Statements.ParallelForEach%601>. <xref:System.Activities.Statements.ForEach%601> Działania zawiera listę wartości i treść. W czasie wykonywania jest iterowane listy i treść jest wykonywane dla każdej wartości na liście.  
  
 <xref:System.Activities.Statements.ParallelForEach%601>ma <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, dzięki czemu <xref:System.Activities.Statements.ParallelForEach%601> może ukończyć działania wczesne Jeśli oceny <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> zwraca `true`. <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Jest oceniane po zakończeniu każdej iteracji.  
  
 W większości przypadków ogólnego wersja działania powinny być preferowane rozwiązanie, ponieważ obejmuje większość scenariuszy, w których jest używany i zawiera typ sprawdzania w czasie kompilacji. Wersja nieogólnego może służyć do iteracji typów, które implementują nieogólnego <xref:System.Collections.IEnumerable> interfejsu.  
  
## <a name="class-definition"></a>Definicja klasy  
 Poniższy przykładowy kod przedstawia definicję nieogólnego `ParallelForEach` jest działania.  
  
```  
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
  
 Treść (opcjonalnie)  
 <xref:System.Activities.ActivityAction> Typu <xref:System.Object>, który jest wykonywany dla każdego elementu w kolekcji. Każdy element poszczególnych jest przekazywana do treści jego właściwość argumentu.  
  
 Wartości (opcjonalnie)  
 Kolekcja elementów, które są iterowane za pośrednictwem. Zapewnienie, że wszystkie elementy kolekcji są zgodnych typów odbywa się w czasie wykonywania.  
  
 CompletionCondition (opcjonalnie)  
 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Właściwości jest oceniane po zakończeniu dowolną iterację. Jeśli daje w wyniku `true`, następnie zaplanowanego czasu iteracji zostały anulowane. Jeśli ta właściwość nie jest ustawiona, wszystkie działania w kolekcji gałęzie wykonywanie do momentu zakończenia.  
  
## <a name="example-of-using-parallelforeach"></a>Przykład użycia działania ParallelForEach  
 Poniższy kod przedstawia sposób użycia działania działania ParallelForEach w aplikacji.  
  
```  
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
  
## <a name="parallelforeach-designer"></a>Projektant działania ParallelForEach  
 Projektant działań przykładowej przypomina do projektanta przewidzianych wbudowane <xref:System.Activities.Statements.ParallelForEach%601> działania. Projektant jest wyświetlany w przyborniku w **przykłady**, **inne niż ogólne działania** kategorii. Projektant nosi nazwę **ParallelForEachWithBodyFactory** w przyborniku ponieważ ujawnia działania <xref:System.Activities.Presentation.IActivityTemplateFactory> w przyborniku tworzy działanie z odpowiednio skonfigurowanego <xref:System.Activities.ActivityAction>.  
  
```  
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
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Ustaw projekt wybranych przez użytkownika jako projekt startowy rozwiązania.  
  
    1.  **CodeTestClient** przedstawia sposób użycia działanie przy użyciu kodu.  
  
    2.  **DesignerTestClient** przedstawia sposób użycia działanie w projektancie.  
  
2.  Tworzenie i uruchamianie projektu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
