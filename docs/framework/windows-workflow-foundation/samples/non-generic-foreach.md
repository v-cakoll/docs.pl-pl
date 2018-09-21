---
title: Nieogólne działanie ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 0274cd5b87e6039ff40afa3108986ffd113fc4fb
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46478321"
---
# <a name="non-generic-foreach"></a>Nieogólne działanie ForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] jest dostarczany w przyborniku jej zestaw działań przepływu sterowania, w tym <xref:System.Activities.Statements.ForEach%601>, co pozwala iteracja <xref:System.Collections.Generic.IEnumerable%601> kolekcji.  
  
 <xref:System.Activities.Statements.ForEach%601> wymaga jego <xref:System.Activities.Statements.ForEach%601.Values%2A> właściwość typu <xref:System.Collections.Generic.IEnumerable%601>. Użytkownicy to wyklucza z Iterowanie struktur danych, które implementują <xref:System.Collections.Generic.IEnumerable%601> interfejsu (na przykład <xref:System.Collections.ArrayList>). Wersja nieogólnego <xref:System.Activities.Statements.ForEach%601> pozwala pokonać ten wymóg, kosztem więcej złożoności środowiska wykonawczego dla zapewnienia zgodności z typów wartości w kolekcji.  
  
 Ten przykład przedstawia sposób implementowania nieogólnego <xref:System.Activities.Statements.ForEach%601> działanie i jego projektanta. To działanie może służyć do iterowania po <xref:System.Collections.ArrayList>.  
  
## <a name="foreach-activity"></a>Działanie ForEach  
 C# /VB `foreach` instrukcji wylicza elementów kolekcji, wykonywania osadzonych instrukcji dla każdego elementu kolekcji. [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Równoważne działania `foreach` są <xref:System.Activities.Statements.ForEach%601> i <xref:System.Activities.Statements.ParallelForEach%601>. <xref:System.Activities.Statements.ForEach%601> Aktywności zawiera listę wartości i treść. W czasie wykonywania jest postanowiliśmy listy, a następnie zostaje wykonana dla każdej wartości na liście.  
  
 W większości przypadków ogólnego wersję działania powinny być preferowanym rozwiązaniem, ponieważ obejmuje większość scenariuszy, w których go będzie używana i oferuje typu sprawdzanie w czasie kompilacji. Wersja nieogólnego może służyć do iteracji przez typy, które implementują niepodstawowy <xref:System.Collections.IEnumerable> interfejsu.  
  
## <a name="class-definition"></a>Definicja klasy  
 Poniższy przykład kodu pokazuje definicji nieogólnego `ForEach` działania.  
  
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
 <xref:System.Activities.ActivityAction> Typu <xref:System.Object>, które jest wykonywane dla każdego elementu w kolekcji. Każdego pojedynczego elementu jest przekazywany do treści za pośrednictwem jego `Argument` właściwości.  
  
 Wartości (opcjonalnie)  
 Kolekcja elementów, które są powtarzana. Upewnić się, że wszystkie elementy kolekcji są zgodnych typów odbywa się w czasie wykonywania.  
  
## <a name="example-of-using-foreach"></a>Przykład Używanie instrukcji ForEach  
 Poniższy kod przedstawia sposób użycia działanie ForEach w aplikacji.  
  
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
|Wartości `null`|Nieprawidłowa wartość argumentu wymagane działania "Wartości".|Błąd|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>Projektant ForEach  
 Projektant działań dla przykładu przypomina projektanta podane dla wbudowanej <xref:System.Activities.Statements.ForEach%601> działania. Pojawi się okno projektanta w przyborniku, w **przykłady**, **działania Nieuniwersalne** kategorii. Projektant jest o nazwie **ForEachWithBodyFactory** w przyborniku, ponieważ ujawnia działania <xref:System.Activities.Presentation.IActivityTemplateFactory> w przyborniku, co powoduje utworzenie działania z prawidłowo skonfigurowane <xref:System.Activities.ActivityAction>.  
  
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
  
1.  Ustaw projekt wybranego jako projekt startowy rozwiązania:  
  
    1.  **CodeTestClient** pokazuje, jak użyć działania przy użyciu kodu.  
  
    2.  **DesignerTestClient** pokazuje, jak użyć działania w projektancie.  
  
2.  Skompiluj i uruchom projekt.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
