---
title: Wybierz działanie
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: b6a49207c6c2e800c2e894f6223abdf0f5f6820d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="pick-activity"></a>Wybierz działanie
<xref:System.Activities.Statements.Pick> Działania upraszcza modelowania zestawu wyzwalaczy zdarzeń oraz ich odpowiednich programów obsługi.  A <xref:System.Activities.Statements.Pick> działania zawiera kolekcję <xref:System.Activities.Statements.PickBranch> działań, gdzie każdy <xref:System.Activities.Statements.PickBranch> jest parowanie między <xref:System.Activities.Statements.PickBranch.Trigger%2A> działania i <xref:System.Activities.Statements.PickBranch.Action%2A> działania.  W czasie wykonywania Wyzwalacze dla wszystkie gałęzie są wykonywane równolegle.  Po zakończeniu jednego wyzwalacza, następnie wykonywane jest jego działanie, a wszystkie inne wyzwalacze zostały anulowane.  Zachowanie [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> działanie przypomina [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <xref:System.Workflow.Activities.ListenActivity> działania.  
  
 Poniższy zrzut ekranu z [za pomocą działania wybierz](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md) przykład zestawu SDK zawiera czynności pobrania z dwóch gałęziach.  Jedna gałąź ma wyzwalacz o nazwie **odczytu danych wejściowych**, niestandardowe działanie, które odczytuje dane wejściowe z wiersza polecenia. Drugi gałęzi ma <xref:System.Activities.Statements.Delay> działania wyzwalacza. Jeśli **odczytu danych wejściowych** działania odbiera dane przed <xref:System.Activities.Statements.Delay> zakończenie działania <xref:System.Activities.Statements.Delay> opóźnienie zostanie anulowane i powitanie zostanie wyświetlony w konsoli.  W przeciwnym razie, jeśli **odczytu danych wejściowych** działania nie odbiera danych w wyznaczonym czasie, a następnie zostanie anulowane i komunikat o limicie czasu zostanie wyświetlony w konsoli.  Jest to wspólnego wzorca użyte do dodania do dowolnej akcji przekroczenie limitu czasu.  
  
 ![Wybierz działanie](../../../docs/framework/windows-workflow-foundation/media/pickconceptual.JPG "PickConceptual")  
  
## <a name="best-practices"></a>Najlepsze praktyki  
 Używając pobrania gałęzi, która wykonuje jest gałęzi, w której wyzwalacz zakończeniu najpierw.  Koncepcyjnie wyzwalacze wszystkie wykonywane równolegle, a jeden wyzwalacz mogło zostać wykonane większość swojej logiki przed została anulowana po zakończeniu innego wyzwalacza.  Pamiętając o tym ogólne wytyczne do wykonania w przypadku używania działania pobrania jest zaliczenie wyzwalacza reprezentujący pojedyncze zdarzenie i poddane jako ilością logiki możliwie go.  Najlepiej, jeśli wyzwalacz powinien zawierać wystarczającego logikę do odbierania zdarzeń i przetwarzania zdarzenia należy przejść do akcji gałęzi.  Ta metoda pozwala zmniejszyć nakładania się wykonanie wyzwalacze.  Rozważmy na przykład <xref:System.Activities.Statements.Pick> z dwóch wyzwalaczy, w którym każdy wyzwalacz zawiera <xref:System.ServiceModel.Activities.Receive> działania następuje dodatkową logikę.  Jeśli dodatkową logikę wprowadza bezczynności punkt, istnieje możliwość zarówno <xref:System.ServiceModel.Activities.Receive> pomyślne zakończenie działania.  Jeden wyzwalacz zostanie w pełni ukończone podczas będzie inny częściowo ukończone.  W niektórych scenariuszach jest nie do przyjęcia akceptowanie komunikatu i częściowo ukończenia przetwarzania go.  W związku z tym gdy przy użyciu działań WF wbudowanych obsługi wiadomości, takich jak <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply>, podczas <xref:System.ServiceModel.Activities.Receive> jest często używana w wyzwalacza, <xref:System.ServiceModel.Activities.SendReply> i innych logiki należy umieścić w akcji, o ile to możliwe.  
  
## <a name="using-the-pick-activity-in-the-designer"></a>Za pomocą działania pobranie w Projektancie  
 Aby użyć pobrania w projektancie, Znajdź **wybierz** i **PickBranch** w przyborniku.  Przeciągnij i upuść **wybierz** na kanwę.  Domyślnie nowy **wybierz** działania w Projektancie będzie zawierać dwóch gałęziach.  Aby dodać dodatkowe gałęzie, przeciągnij **PickBranch** działania i upuść go obok istniejących gałęzi. Działania mogą być upuszczone na **wybierz** działania w jednej **wyzwalacza** obszaru lub **akcji** obszaru dowolnego **PickBranch**.  
  
## <a name="using-the-pick-activity-in-code"></a>Za pomocą działania pobrania w kodzie  
 <xref:System.Activities.Statements.Pick> Działania jest używana przez wypełnianie jej <xref:System.Activities.Statements.Pick.Branches%2A> kolekcji z <xref:System.Activities.Statements.PickBranch> działań. <xref:System.Activities.Statements.PickBranch> Działania każdego mają <xref:System.Activities.Statements.PickBranch.Trigger%2A> właściwości typu <xref:System.Activities.Activity>. Po ukończeniu określonego działania wykonywania, <xref:System.Activities.Statements.PickBranch.Action%2A> wykonuje.  
  
 Poniższy przykład kodu pokazuje sposób użycia <xref:System.Activities.Statements.Pick> działanie, aby zaimplementować przekroczenie limitu czasu dla działania odczytuje wiersz z konsoli.  
  
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
