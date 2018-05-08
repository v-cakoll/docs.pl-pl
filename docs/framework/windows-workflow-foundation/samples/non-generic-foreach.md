---
title: ForEach inny niż ogólny
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: c67f6e3c3afb893f7bb5713d64ce2f119eebc157
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="non-generic-foreach"></a>ForEach inny niż ogólny
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] jest dostarczany w przyborniku jego zestaw działań przepływu sterowania, w tym <xref:System.Activities.Statements.ForEach%601>, dzięki czemu iteracja <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` kolekcji.  
  
 <xref:System.Activities.Statements.ForEach%601> wymaga jego <xref:System.Activities.Statements.ForEach%601.Values%2A> właściwości typu <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`. To wyklucza użytkowników z Iterowanie za pośrednictwem struktury danych, które implementują <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` interfejsu (na przykład <xref:System.Collections.ArrayList>). Wersja nieogólnego <xref:System.Activities.Statements.ForEach%601> pozwala pokonać to wymaganie, kosztem bardziej złożona czasu wykonywania dla zapewnienia zgodności z typów wartości w kolekcji.  
  
 W tym przykładzie pokazano, jak wdrożyć nieogólnego <xref:System.Activities.Statements.ForEach%601> działanie i jego projektanta. To działanie może służyć do iterowania po <xref:System.Collections.ArrayList>.  
  
## <a name="foreach-activity"></a>Działania ForEach  
 C# /VB `foreach` instrukcji wylicza elementy kolekcji, wykonywania osadzona instrukcja dla każdego elementu w kolekcji. [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Równoważne działania `foreach` są <xref:System.Activities.Statements.ForEach%601> i <xref:System.Activities.Statements.ParallelForEach%601>. <xref:System.Activities.Statements.ForEach%601> Działania zawiera listę wartości i treść. W czasie wykonywania jest iterowane listy i treść jest wykonywane dla każdej wartości na liście.  
  
 W większości przypadków ogólnego wersja działania powinny być preferowane rozwiązanie, ponieważ obejmuje większość scenariuszy, w których on mają być używane i zawiera typ sprawdzania w czasie kompilacji. Wersja nieogólnego może służyć do iteracji typów, które implementują nieogólnego <xref:System.Collections.IEnumerable> interfejsu.  
  
## <a name="class-definition"></a>Definicja klasy  
 Poniższy przykładowy kod przedstawia definicję nieogólnego `ForEach` działania.  
  
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
 <xref:System.Activities.ActivityAction> Typu <xref:System.Object>, który jest wykonywany dla każdego elementu w kolekcji. Każdy element poszczególnych została przekazana do treści za pośrednictwem jego `Argument` właściwości.  
  
 Wartości (opcjonalnie)  
 Kolekcja elementów, które są iterowane za pośrednictwem. Zapewnienie, że wszystkie elementy kolekcji są zgodnych typów odbywa się w czasie wykonywania.  
  
## <a name="example-of-using-foreach"></a>Przykład za pomocą instrukcji ForEach  
 Poniższy kod przedstawia sposób użycia działania ForEach w aplikacji.  
  
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
  
|Warunek|Komunikat|Ważność|Typ wyjątku|  
|---------------|-------------|--------------|--------------------|  
|Wartości to `null`|Nie podano wartości dla wymaganego argumentu działania "Wartości".|Błąd|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>Projektant ForEach  
 Projektant działań przykładowej przypomina do projektanta przewidzianych wbudowane <xref:System.Activities.Statements.ForEach%601> działania. Projektant jest wyświetlany w przyborniku w **przykłady**, **inne niż ogólne działania** kategorii. Projektant nosi nazwę **ForEachWithBodyFactory** w przyborniku ponieważ ujawnia działania <xref:System.Activities.Presentation.IActivityTemplateFactory> w przyborniku, co powoduje działania z odpowiednio skonfigurowanego <xref:System.Activities.ActivityAction>.  
  
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
  
1.  Ustaw projekt wybranych przez użytkownika jako projekt uruchamiania rozwiązania:  
  
    1.  **CodeTestClient** przedstawia sposób użycia działanie przy użyciu kodu.  
  
    2.  **DesignerTestClient** przedstawia sposób użycia działanie w projektancie.  
  
2.  Tworzenie i uruchamianie projektu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
