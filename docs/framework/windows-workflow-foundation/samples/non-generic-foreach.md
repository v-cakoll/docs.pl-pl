---
title: Nieogólne działanie ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: e467534ba2b233f1f3c279e89badf12846c6b7f7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038075"
---
# <a name="non-generic-foreach"></a>Nieogólne działanie ForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]dostarcza w swoim przyborniku zestaw działań przepływu sterowania, w tym <xref:System.Activities.Statements.ForEach%601>, które umożliwiają iterację <xref:System.Collections.Generic.IEnumerable%601> za pomocą kolekcji.  
  
 <xref:System.Activities.Statements.ForEach%601>wymaga, aby <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Activities.Statements.ForEach%601.Values%2A> Właściwość była typu. Uniemożliwia to użytkownikom iterację struktur danych, które implementują <xref:System.Collections.Generic.IEnumerable%601> interfejs (na <xref:System.Collections.ArrayList>przykład). Nieogólna wersja przechodziła <xref:System.Activities.Statements.ForEach%601> z tego wymagania, kosztem większej złożoności w czasie wykonywania w celu zapewnienia zgodności typów wartości w kolekcji.  
  
 Ten przykład pokazuje sposób implementacji działania nieogólnego <xref:System.Activities.Statements.ForEach%601> i jego projektanta. To działanie może służyć do iteracji przez <xref:System.Collections.ArrayList>.  
  
## <a name="foreach-activity"></a>Działanie ForEach  
 Instrukcja C#/VB `foreach` wylicza elementy kolekcji, wykonując osadzoną instrukcję dla każdego elementu kolekcji. Równoważne działania z `foreach` są <xref:System.Activities.Statements.ForEach%601> i .<xref:System.Activities.Statements.ParallelForEach%601> [!INCLUDE[wf1](../../../../includes/wf1-md.md)] <xref:System.Activities.Statements.ForEach%601> Działanie zawiera listę wartości i treść. W czasie wykonywania lista jest powtarzana i jest wykonywana dla każdej wartości na liście.  
  
 W większości przypadków ogólna wersja działania powinna być preferowanym rozwiązaniem, ponieważ obejmuje większość scenariuszy, w których będzie używana, i zapewnia kontrolę typu w czasie kompilacji. Wersja nieogólna może być używana do iterowania przez typy implementujące interfejs nieogólny <xref:System.Collections.IEnumerable> .  
  
## <a name="class-definition"></a>Definicja klasy  
 Poniższy przykład kodu pokazuje definicję działania nierodzajowego `ForEach` .  
  
```  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }   
}  
```  
  
 Treść (opcjonalnie)  
 <xref:System.Activities.ActivityAction> Typ<xref:System.Object>, który jest wykonywany dla każdego elementu w kolekcji. Każdy pojedynczy element jest przesyłany do treści za pomocą `Argument` jego właściwości.  
  
 Wartości (opcjonalne)  
 Kolekcja elementów, które są powtarzane. Upewnienie się, że wszystkie elementy kolekcji są zgodne typy wykonywane w czasie wykonywania.  
  
## <a name="example-of-using-foreach"></a>Przykład użycia polecenia ForEach  
 Poniższy kod ilustruje sposób używania działania ForEach w aplikacji.  
  
```  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
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
  
|Warunek|Message|Ważność|Typ wyjątku|  
|---------------|-------------|--------------|--------------------|  
|Wartości to`null`|Nie podano wartości dla wymaganego argumentu działania "Values".|Błąd|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>Projektant ForEach  
 Projektant działań dla przykładu jest podobny do projektanta dostępnego dla <xref:System.Activities.Statements.ForEach%601> działania wbudowanego. Projektant pojawia się w przyborniku w kategorii **przykłady**, **nieogólne działania** . Projektant ma nazwę **ForEachWithBodyFactory** w przyborniku, ponieważ działanie uwidacznia <xref:System.Activities.Presentation.IActivityTemplateFactory> w przyborniku, który tworzy działanie z prawidłową konfiguracją. <xref:System.Activities.ActivityAction>  
  
```  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
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
  
#### <a name="to-run-this-sample"></a>Aby uruchomić ten przykład  
  
1. Ustaw wybrany projekt jako projekt startowy rozwiązania:  
  
    1. **CodeTestClient** pokazuje, jak używać działania przy użyciu kodu.  
  
    2. **DesignerTestClient** pokazuje, jak używać działania w projektancie.  
  
2. Skompiluj i uruchom projekt.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
