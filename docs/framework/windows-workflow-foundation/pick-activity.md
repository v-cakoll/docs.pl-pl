---
title: Wybieranie działania
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: 51caf020042212b570ae915ead00a4225df2c588
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283180"
---
# <a name="pick-activity"></a>Wybieranie działania
Działanie <xref:System.Activities.Statements.Pick> upraszcza modelowanie zestawu wyzwalaczy zdarzeń, a następnie odpowiadające im procedury obsługi.  Działanie <xref:System.Activities.Statements.Pick> zawiera kolekcję działań <xref:System.Activities.Statements.PickBranch>, gdzie każda <xref:System.Activities.Statements.PickBranch> jest parowaniem między działaniem <xref:System.Activities.Statements.PickBranch.Trigger%2A> a działaniem <xref:System.Activities.Statements.PickBranch.Action%2A>.  W czasie wykonywania wyzwalacze dla wszystkich rozgałęzień są wykonywane równolegle.  Po zakończeniu jednego wyzwalacza odpowiednia akcja jest wykonywana i wszystkie pozostałe wyzwalacze są anulowane.  Zachowanie [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> działa podobnie jak działanie <xref:System.Workflow.Activities.ListenActivity> .NET Framework 3,5.  
  
 Na poniższym zrzucie ekranu z poziomu zestawu SDK [działania wybierz](./samples/using-the-pick-activity.md) zostanie wyświetlona czynność pobrania z dwoma gałęziami.  Jedna gałąź ma wyzwalacz o nazwie **Odczyt wejściowy**, działanie niestandardowe, które odczytuje dane wejściowe z wiersza polecenia. Druga gałąź ma <xref:System.Activities.Statements.Delay> wyzwalaczem działania. Jeśli działanie **odczytu danych wejściowych** odbiera dane przed zakończeniem działania <xref:System.Activities.Statements.Delay>, opóźnienie <xref:System.Activities.Statements.Delay> zostanie anulowane, a powitanie zostanie zapisany w konsoli.  W przeciwnym razie, jeśli działanie **Odczytaj dane wejściowe** nie odbiera danych w wyznaczonym czasie, zostanie anulowane, a w konsoli zostanie zapisany komunikat o limicie czasu.  Jest to typowy wzorzec służący do dodawania limitu czasu do dowolnej akcji.  
  
 ![Wybieranie działania](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a>Najlepsze rozwiązania  
 W przypadku korzystania z funkcji wybierz gałąź, która jest wykonywana, jest gałęzią, której wyzwalacz zostaje zakończony jako pierwszy.  Koncepcyjnie wszystkie wyzwalacze są wykonywane równolegle, a jeden wyzwalacz może wykonać większość jego logiki przed anulowaniem przez zakończenie innego wyzwalacza.  Z tego względu ogólne wytyczne, które należy wykonać podczas korzystania z działania pobrania, to traktowanie wyzwalacza w postaci pojedynczego zdarzenia i umieszczenie jak najmniejszej logiki.  W idealnym przypadku wyzwalacz powinien zawierać tylko wystarczającą logikę, aby można było odebrać zdarzenie, a wszystkie przetwarzanie tego zdarzenia powinno nastąpić do działania gałęzi.  Ta metoda minimalizuje ilość nakładania się między wykonaniem wyzwalaczy.  Rozważmy na przykład <xref:System.Activities.Statements.Pick> z dwoma wyzwalaczami, gdzie każdy wyzwalacz zawiera działanie <xref:System.ServiceModel.Activities.Receive>, a następnie dodatkową logikę.  Jeśli dodatkowa logika wprowadza punkt bezczynności, istnieje możliwość pomyślnego zakończenia działania obu <xref:System.ServiceModel.Activities.Receive>.  Jeden wyzwalacz zostanie w pełni ukończony, podczas gdy inny zostanie częściowo ukończony.  W niektórych scenariuszach zaakceptowanie komunikatu, a następnie częściowe zakończenie jego przetwarzania jest nieakceptowalne.  W związku z tym podczas korzystania z wbudowanych działań związanych z obsługą mechanizmu WF, takich jak <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply>, podczas gdy <xref:System.ServiceModel.Activities.Receive> jest często używany w wyzwalaczu, <xref:System.ServiceModel.Activities.SendReply> i inne logiki należy umieścić w akcji zawsze wtedy, gdy jest to możliwe.  
  
## <a name="using-the-pick-activity-in-the-designer"></a>Korzystanie z działania pobrania w projektancie  
 Aby użyć **funkcji wybierz w projektancie, Znajdź pozycję** find and **PickBranch** w przyborniku.  Przeciągnij i upuść **wybór** na kanwie.  Domyślnie nowe działanie **pobrania** w projektancie będzie zawierać dwie gałęzie.  Aby dodać dodatkowe gałęzie, przeciągnij działanie **PickBranch** i upuść je obok istniejących gałęzi. Działania można porzucić do działania **pobrania** w obszarze **wyzwalacza** lub w obszarze **akcji** dowolnego **PickBranch**.  
  
## <a name="using-the-pick-activity-in-code"></a>Korzystanie z działania pobrania w kodzie  
 Działanie <xref:System.Activities.Statements.Pick> służy do wypełniania swojej kolekcji <xref:System.Activities.Statements.Pick.Branches%2A> z działaniami <xref:System.Activities.Statements.PickBranch>. Każdy <xref:System.Activities.Statements.PickBranch> działania ma właściwość <xref:System.Activities.Statements.PickBranch.Trigger%2A> typu <xref:System.Activities.Activity>. Gdy określone działanie zakończy wykonywanie, <xref:System.Activities.Statements.PickBranch.Action%2A> wykonuje.  
  
 Poniższy przykład kodu ilustruje sposób użycia działania <xref:System.Activities.Statements.Pick> w celu zaimplementowania limitu czasu dla działania, które odczytuje wiersz z konsoli.  
  
```csharp  
Sequence body = new Sequence()  
{  
    Variables = { name },  
    Activities =   
   {  
       new System.Activities.Statements.Pick  
        {  
           Branches =   
           {  
               new PickBranch  
               {  
                   Trigger = new ReadLine  
                   {  
                      Result = name,  
                      BookmarkName = "name"  
                   },  
                   Action = new WriteLine   
                   {   
                       Text = ExpressionServices.Convert<string>(ctx => "Hello " +   
                           name.Get(ctx))   
                   }  
               },  
               new PickBranch  
               {  
                   Trigger = new Delay  
                   {  
                      Duration = new TimeSpan(0, 0, 5)  
                   },  
                   Action = new WriteLine  
                   {  
                      Text = "Time is up."  
                   }  
               }  
           }  
       }  
   }  
};  
```  
  
```xaml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:String" Name="username" />  
  </Sequence.Variables>  
  <Pick>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <ReadLine BookmarkName="name" Result="username" />  
      </PickBranch.Trigger>  
      <WriteLine>[String.Concat("Hello ", username)]</WriteLine>  
    </PickBranch>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <Delay>00:00:05</Delay>  
      </PickBranch.Trigger>  
      <WriteLine>Time is up.</WriteLine>  
    </PickBranch>  
  </Pick>  
</Sequence>  
```
