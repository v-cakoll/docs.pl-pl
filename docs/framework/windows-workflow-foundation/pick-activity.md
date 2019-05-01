---
title: Wybieranie działania
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: b9ee6c06377760d27bc54d39c1d1f3ecf67ea0d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909428"
---
# <a name="pick-activity"></a>Wybieranie działania
<xref:System.Activities.Statements.Pick> Działania upraszcza modelowania zestawu wyzwalaczy zdarzeń, następuje ich odpowiednie programy obsługi.  A <xref:System.Activities.Statements.Pick> aktywności zawiera zbiór <xref:System.Activities.Statements.PickBranch> działań, gdzie każdy <xref:System.Activities.Statements.PickBranch> jest powiązany między <xref:System.Activities.Statements.PickBranch.Trigger%2A> działania i <xref:System.Activities.Statements.PickBranch.Action%2A> działania.  W czasie wykonywania wyzwalaczy dla wszystkich oddziałów są wykonywane równolegle.  Po zakończeniu jeden wyzwalacz, następnie jest wykonywany swoje działania odpowiednie, a inne wyzwalacze są anulowane.  Zachowanie [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> działanie jest podobne do [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <xref:System.Workflow.Activities.ListenActivity> działania.  
  
 Poniższy zrzut ekranu z [przy użyciu działania wybierz](./samples/using-the-pick-activity.md) Przykładowy zestaw SDK zawiera działania Pick, za pomocą dwóch gałęzi.  Jedna gałąź ma wyzwalacza o nazwie **odczytu danych wejściowych**, niestandardowe działanie, które odczytuje dane wejściowe z wiersza polecenia. Drugi gałęzi ma <xref:System.Activities.Statements.Delay> działania wyzwalacza. Jeśli **odczytu danych wejściowych** działania odbiera dane przed <xref:System.Activities.Statements.Delay> zakończy działanie <xref:System.Activities.Statements.Delay> opóźnienie zostanie anulowane i powitanie zostanie zapisany do konsoli.  W przeciwnym razie, jeśli **odczytu danych wejściowych** działania nie odbiera danych w wyznaczonym czasie, a następnie zostanie anulowane i komunikat o limicie czasu będą zapisywane w konsoli programu.  Jest to typowy wzorzec używany do zwiększenia limitu czasu żadnych działań.  
  
 ![Wybieranie działania](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a>Najlepsze rozwiązania  
 Korzystając z pobrań, gałęzi, który jest wykonywany jest gałęzi, w której wyzwalacz zakończy się najpierw.  Koncepcyjnie wszystkie wyzwalacze są wykonywane równolegle, a jeden wyzwalacz może zostać wykonane większość swojej logiki zanim zostanie anulowane po zakończeniu kolejnego wyzwalacza.  Mając to na uwadze ogólne wytyczne, które należy wykonać podczas używanie działania Pick jest zaliczenie reprezentujący pojedyncze zdarzenie wyzwalacza i zostać umieszczona jako nieco logiki możliwie go.  W idealnym przypadku wyzwalacz powinien zawierać wystarczający logikę w celu odbierania zdarzeń, a przetwarzanie zdarzenia powinny należeć do akcji w gałęzi.  Ta metoda pozwala zmniejszyć nakładania się wykonywanie wyzwalacze.  Na przykład, rozważmy <xref:System.Activities.Statements.Pick> za pomocą dwóch wyzwalaczy, w którym każdy wyzwalacz ma <xref:System.ServiceModel.Activities.Receive> aktywności następuje dodatkowej logiki.  Jeśli dodatkowej logiki wprowadza punkt bezczynności, a następnie jest możliwość zarówno <xref:System.ServiceModel.Activities.Receive> działania pomyślne zakończenie działania.  Jeden wyzwalacz będzie w pełni zakończeniu podczas będzie innego częściowo ukończone.  W niektórych scenariuszach akceptowania wiadomości, a częściowo ukończenie przetwarzania go jest nie do przyjęcia.  W związku z tym korzystając z wbudowanych działań dotyczących komunikatów WF takich jak <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply>, podczas gdy <xref:System.ServiceModel.Activities.Receive> jest powszechnie używana do wyzwalacza <xref:System.ServiceModel.Activities.SendReply> oraz innych logik należy umieścić w akcji, jeśli to możliwe.  
  
## <a name="using-the-pick-activity-in-the-designer"></a>Używanie działania Pick w Projektancie  
 Aby użyć wyboru w projektancie, Znajdź **wybierz** i **PickBranch** w przyborniku.  Przeciąganie i upuszczanie **wybierz** na kanwę.  Domyślnie nowy **wybierz** działania w Projektancie będzie zawierać dwie gałęzie.  Aby dodać dodatkowe gałęzie, przeciągnij **PickBranch** działania i upuść je obok istniejącej gałęzi. Działania mogą być upuszczone na **wybierz** działanie do albo **wyzwalacza** obszaru lub **akcji** obszar dowolnego **PickBranch**.  
  
## <a name="using-the-pick-activity-in-code"></a>Używanie działania wybierz w kodzie  
 <xref:System.Activities.Statements.Pick> Działania jest używana przez wypełnianie jej <xref:System.Activities.Statements.Pick.Branches%2A> kolekcji z <xref:System.Activities.Statements.PickBranch> działań. <xref:System.Activities.Statements.PickBranch> Działania każdego mają <xref:System.Activities.Statements.PickBranch.Trigger%2A> właściwości typu <xref:System.Activities.Activity>. Podczas działania określonego kończy wykonywanie, <xref:System.Activities.Statements.PickBranch.Action%2A> wykonuje.  
  
 Poniższy przykład kodu demonstruje sposób używania <xref:System.Activities.Statements.Pick> działanie, aby zaimplementować limitu czasu dla działania, który odczytuje wiersz z konsoli.  
  
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
