---
title: Wybieranie działania
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: 672de5fd3df5e8dde6c54118503bf2a11353b116
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182892"
---
# <a name="pick-activity"></a>Wybieranie działania
Działanie <xref:System.Activities.Statements.Pick> upraszcza modelowanie zestawu wyzwalaczy zdarzeń, po których następuje ich odpowiednie programy obsługi.  Działanie <xref:System.Activities.Statements.Pick> zawiera zbiór <xref:System.Activities.Statements.PickBranch> działań, gdzie <xref:System.Activities.Statements.PickBranch> każdy jest parowanie między działaniem <xref:System.Activities.Statements.PickBranch.Trigger%2A> a działaniem. <xref:System.Activities.Statements.PickBranch.Action%2A>  W czasie wykonywania wyzwalacze dla wszystkich gałęzi są wykonywane równolegle.  Po zakończeniu jednego wyzwalacza, a następnie jego odpowiednie działanie jest wykonywane, a wszystkie inne wyzwalacze są anulowane.  Zachowanie [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> działania jest podobny do działania .NET Framework <xref:System.Workflow.Activities.ListenActivity> 3.5.  
  
 Poniższy zrzut ekranu z przy użyciu przy [użyciu przystawek SDK działania](./samples/using-the-pick-activity.md) pokazuje Działanie pobrania z dwóch gałęzi.  Jedna gałąź ma wyzwalacz o nazwie **Odczyt danych wejściowych**, działanie niestandardowe, które odczytuje dane wejściowe z wiersza polecenia. Druga gałąź <xref:System.Activities.Statements.Delay> ma wyzwalacz działania. Jeśli działanie **do odczytu danych wejściowych** odbiera dane przed <xref:System.Activities.Statements.Delay> zakończeniem działania, <xref:System.Activities.Statements.Delay> Opóźnienie zostanie anulowane, a powitanie zostanie zapisane na konsoli.  W przeciwnym razie jeśli działanie **do odczytu danych wejściowych** nie odbierze danych w wyznaczonym czasie, zostanie ono anulowane, a na konsoli zostanie zapisany komunikat limitu czasu.  Jest to typowy wzorzec używany do dodawania limitu czasu do dowolnej akcji.  
  
 ![Wybieranie działania](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a>Najlepsze rozwiązania  
 Podczas korzystania z Pick, gałąź, która wykonuje jest gałąź, której wyzwalacz kończy się jako pierwszy.  Koncepcyjnie wszystkie wyzwalacze są wykonywane równolegle, a jeden wyzwalacz mógł wykonać większość jego logiki, zanim zostanie anulowany przez ukończenie innego wyzwalacza.  Mając to na uwadze, ogólne wytyczne do naśladowania podczas korzystania z Pick działania jest traktowanie wyzwalacza jako reprezentujący pojedyncze zdarzenie i umieścić jak najmniej logiki, jak to możliwe do niego.  W idealnym przypadku wyzwalacz powinien zawierać wystarczającą ilość logiki, aby otrzymać zdarzenie, a całe przetwarzanie tego zdarzenia powinno przejść do akcji gałęzi.  Ta metoda minimalizuje ilość nakładania się między wykonywanie wyzwalaczy.  Na przykład należy <xref:System.Activities.Statements.Pick> wziąć pod uwagę z dwóch <xref:System.ServiceModel.Activities.Receive> wyzwalaczy, gdzie każdy wyzwalacz zawiera działanie, a następnie dodatkowe logiki.  Jeśli dodatkowa logika wprowadza punkt bezczynności, istnieje możliwość, <xref:System.ServiceModel.Activities.Receive> że oba działania zostaną pomyślnie ukończone.  Jeden wyzwalacz zostanie w pełni ukończony, podczas gdy drugi zostanie częściowo ukończony.  W niektórych scenariuszach akceptowanie wiadomości, a następnie częściowe jej przetwarzanie jest niedopuszczalne.  W związku z tym podczas korzystania z wbudowanej <xref:System.ServiceModel.Activities.SendReply>obsługi <xref:System.ServiceModel.Activities.Receive> wiadomości WF, takich <xref:System.ServiceModel.Activities.SendReply> jak <xref:System.ServiceModel.Activities.Receive> i , podczas gdy jest powszechnie używany w wyzwalaczu i inne logiki powinny być wprowadzane w akcji, gdy jest to możliwe.  
  
## <a name="using-the-pick-activity-in-the-designer"></a>Korzystanie z działania Pobranie w projektancie  
 Aby użyć opcji Wybierz w projektancie, znajdź **przycisk Wybierz** i **Wybierz** w przyborniku.  Przeciągnij i upuść **Wybierz** na kanwę.  Domyślnie nowe działanie **pobrania** w projektancie będzie zawierać dwie gałęzie.  Aby dodać dodatkowe gałęzie, przeciągnij działanie **PickBranch** i upuść je obok istniejących gałęzi. Działania można upuścić na **działanie pobrania** w obszarze **Wyzwalacz** lub w obszarze **Akcja** dowolnego **pickbrancha**.  
  
## <a name="using-the-pick-activity-in-code"></a>Korzystanie z działania pobrania w kodzie  
 Działanie <xref:System.Activities.Statements.Pick> jest używane przez wypełnianie <xref:System.Activities.Statements.Pick.Branches%2A> <xref:System.Activities.Statements.PickBranch> jego kolekcji działaniami. Działania <xref:System.Activities.Statements.PickBranch> mają <xref:System.Activities.Statements.PickBranch.Trigger%2A> właściwość typu <xref:System.Activities.Activity>. Po zakończeniu wykonywania określonego działania, <xref:System.Activities.Statements.PickBranch.Action%2A> wykonuje.  
  
 Poniższy przykład kodu pokazuje, <xref:System.Activities.Statements.Pick> jak używać działania do implementacji limitu czasu dla działania, które odczytuje wiersz z konsoli.  
  
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
