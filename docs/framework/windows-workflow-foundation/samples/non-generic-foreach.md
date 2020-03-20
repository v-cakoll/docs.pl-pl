---
title: Nieogólne działanie ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 08dbac3974915f823a4f6e39f35927453a7c4b3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142709"
---
# <a name="non-generic-foreach"></a>Nieogólne działanie ForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]w swoim zestawie narzędzi znajduje się zestaw <xref:System.Activities.Statements.ForEach%601>działań control flow, <xref:System.Collections.Generic.IEnumerable%601> w tym , który umożliwia iterację poprzez kolekcje.  
  
 <xref:System.Activities.Statements.ForEach%601>wymaga, <xref:System.Activities.Statements.ForEach%601.Values%2A> aby jego <xref:System.Collections.Generic.IEnumerable%601>właściwość była typu. Uniemożliwia to użytkownikom iterację struktur danych <xref:System.Collections.Generic.IEnumerable%601> implementujących interfejs <xref:System.Collections.ArrayList>(na przykład ). Nierodzyna <xref:System.Activities.Statements.ForEach%601> wersja pokonuje to wymaganie, kosztem większej złożoności w czasie wykonywania w celu zapewnienia zgodności typów wartości w kolekcji.  
  
 W tym przykładzie pokazano, <xref:System.Activities.Statements.ForEach%601> jak zaimplementować działanie niegeneryczne i jego projektanta. To działanie może służyć do <xref:System.Collections.ArrayList>iteracji przez .  
  
## <a name="foreach-activity"></a>Aktywność ForEach  
 Instrukcja C#/Visual Basic `foreach` wylicza elementy kolekcji, wykonując osadzoną instrukcję dla każdego elementu kolekcji. Równoważne [!INCLUDE[wf1](../../../../includes/wf1-md.md)] działania `foreach` są <xref:System.Activities.Statements.ForEach%601> <xref:System.Activities.Statements.ParallelForEach%601>i . Działanie <xref:System.Activities.Statements.ForEach%601> zawiera listę wartości i treść. W czasie wykonywania lista jest iterowana, a treść jest wykonywana dla każdej wartości na liście.  
  
 W większości przypadków ogólna wersja działania powinna być preferowanym rozwiązaniem, ponieważ obejmuje większość scenariuszy, w których będzie używana i zapewnia sprawdzanie typu w czasie kompilacji. Wersja niegeneryczna może służyć do iteracji za pośrednictwem <xref:System.Collections.IEnumerable> typów, które implementują interfejs niegeneryczny.  
  
## <a name="class-definition"></a>Definicja klasy  
 Poniższy przykład kodu przedstawia definicję `ForEach` działania nierodzego.  
  
```csharp  
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
  
 Korpus (opcjonalnie)  
 Typ <xref:System.Activities.ActivityAction> <xref:System.Object>, który jest wykonywany dla każdego elementu w kolekcji. Każdy pojedynczy element jest przekazywany do Body za pośrednictwem jego `Argument` właściwości.  
  
 Wartości (opcjonalnie)  
 Kolekcja elementów, które są iterowane ponad. Upewnienie się, że wszystkie elementy kolekcji są zgodne typy odbywa się w czasie wykonywania.  
  
## <a name="example-of-using-foreach"></a>Przykład korzystania z ForEach  
 Poniższy kod pokazuje, jak używać ForEach działania w aplikacji.  
  
```csharp  
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
|Wartości są`null`|Wartość wymaganego argumentu działania "Wartości" nie została podana.|Błąd|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>Projektant ForEach  
 Projektant działania dla przykładu jest podobny wygląd do projektanta <xref:System.Activities.Statements.ForEach%601> przewidziane dla wbudowanego działania. Projektant pojawi się w przyborniku w **kategorii Przykłady**, **Działania niegeneryczne.** Projektant nosi nazwę **ForEachWithBodyFactory** w przyborniku, <xref:System.Activities.Presentation.IActivityTemplateFactory> ponieważ działanie udostępnia w przyborniku, który <xref:System.Activities.ActivityAction>tworzy działanie z prawidłowo skonfigurowanym .  
  
```csharp  
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
  
2. Tworzenie i uruchamianie projektu.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
