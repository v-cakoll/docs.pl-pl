---
title: kompensacji
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 861e0c9eb4e9afa5f9924160efed428d565bac4e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="compensation"></a>kompensacji
W systemie Windows Workflow Foundation (WF) kompensacji jest mechanizm, za pomocą której wcześniej ukończona Praca można cofnąć lub Skompensowane (po logiki zdefiniowane przez aplikację) po wystąpieniu awarii kolejne. W tej sekcji opisano sposób użycia kompensacji w przepływach pracy.  
  
## <a name="compensation-vs-transactions"></a>Vs kompensacji. Transakcje  
 Transakcja umożliwia łączenie wielu operacji w pojedynczą jednostkę pracy. Przy użyciu transakcji daje możliwość przerwania (wycofywania), wszystkie zmiany wykonane z w obrębie transakcji, jeśli wystąpią błędy podczas realizowania transakcji dowolnej części aplikacji. Jednak przy użyciu transakcji nie może być odpowiednie, jeśli praca jest długo działające. Na przykład aplikację planowania podróży jest implementowany jako przepływ pracy. Czynności przepływu pracy może składać się z rezerwacji lot, oczekiwanie na zatwierdzenie przez menedżera i następnie płatność za lot. Ten proces może zająć wiele dni i nie jest praktyczne instrukcje rezerwacji i płatności dla transmitowane do udziału w tej samej transakcji. W przypadku takich jak ta kompensacji może służyć do cofnąć krok rezerwacji przepływu pracy w przypadku awarii później podczas przetwarzania.  
  
> [!NOTE]
>  W tym temacie omówiono kompensacji w przepływach pracy. [!INCLUDE[crabout](../../../includes/crabout-md.md)] transakcje w przepływach pracy, zobacz [transakcji](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) i <xref:System.Activities.Statements.TransactionScope>. [!INCLUDE[crabout](../../../includes/crabout-md.md)] transakcje, zobacz <xref:System.Transactions?displayProperty=nameWithType> i <xref:System.Transactions.Transaction?displayProperty=nameWithType>.  
  
## <a name="using-compensableactivity"></a>Za pomocą działania CompensableActivity  
 <xref:System.Activities.Statements.CompensableActivity> działanie kompensacji core w [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Każde działanie, które wykonywania pracy, który może być konieczne kompensowane są umieszczane w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity>. W tym przykładzie umieszczane rezerwacji krok zakupu lot <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> i anulowania rezerwacji jest umieszczany w <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>. Bezpośrednio po <xref:System.Activities.Statements.CompensableActivity> w przepływie pracy są dwa działania, które czekać na zatwierdzenie manager, a następnie Zakończ zakupów kroku lot. Jeśli warunek błędu powoduje uruchomienie przepływu pracy można anulować po <xref:System.Activities.Statements.CompensableActivity> została pomyślnie zakończona, następnie działania w <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> obsługi są zaplanowane i połączenie zostało anulowane.  
  
 [!code-csharp[CFX_CompensationExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 Poniższy przykład jest przepływ pracy w języku XAML.  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
  
 **ReserveFlight: Biletu jest zarezerwowana.**  
**ManagerApproval: Zgoda menedżera Odebrano.**   
**PurchaseFlight: Biletu została zakupiona.**   
**Przepływ pracy został ukończony pomyślnie o stanie: zamknięte.**    
> [!NOTE]
>  Przykładowe działania w tym temacie, takich jak `ReserveFlight` wyświetlić nazwy użytkownika i cel w konsoli, ułatwiające zidentyfikowanie kolejność wykonywania działań, gdy wystąpi kompensacji.  
  
### <a name="default-workflow-compensation"></a>Domyślne kompensacji przepływu pracy  
 Domyślnie jeśli przepływu pracy zostało anulowane, logiki kompensacji jest wykonywane dla compensable działalności, która została pomyślnie całkowicie i nie jest jeszcze potwierdzenia lub skompensowane.  
  
> [!NOTE]
>  Gdy <xref:System.Activities.Statements.CompensableActivity> jest *potwierdzone*, nie można wywołać kompensacji działania. Proces potwierdzenia jest opisano wcześniej w tej sekcji.  
  
 W tym przykładzie jest zgłaszany wyjątek, po lot jest zarezerwowana, ale przed wykonaniem kroku zatwierdzenia menedżera.  
  
 [!code-csharp[CFX_CompensationExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 W tym przykładzie przedstawiono przepływ pracy w języku XAML.  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:SimulatedErrorCondition />  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 [!code-csharp[CFX_CompensationExample#100](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 Po wywołaniu przepływu pracy obsługi wyjątku warunku błędu symulowane przez aplikację hosta w <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, przepływ pracy zostanie anulowane i logiki kompensacji jest wywoływany.  
  
 **ReserveFlight: Biletu jest zarezerwowana.**  
**SimulatedErrorCondition: Zgłaszanie ApplicationException.**   
**Przepływ pracy nieobsługiwany wyjątek:**   
**System.ApplicationException: Symulowane błąd w przepływie pracy.**   
**CancelFlight: Biletu zostało anulowane.**   
**Przepływ pracy został ukończony pomyślnie o stanie: anulowane.**    
### <a name="cancellation-and-compensableactivity"></a>Anulowanie i działanie CompensableActivity  
 Jeśli działania w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> ma nie zostało ukończone i działanie zostało anulowane, działania w <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> są wykonywane.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Jest wywoływana tylko w przypadku działania w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> nie została ukończona i działanie zostało anulowane. <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> Jest wykonywana tylko w przypadku działania w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> zostały pomyślnie ukończone i kompensacji następnie jest wywoływana w działaniu.  
  
 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Daje możliwość zapewnienia wszelka logika anulowania odpowiednie autorów przepływu pracy. W poniższym przykładzie jest zgłaszany wyjątek podczas wykonywania <xref:System.Activities.Statements.CompensableActivity.Body%2A>, a następnie <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> jest wywoływana.  
  
```csharp  
Activity wf = new Sequence()  
{  
    Activities =  
    {  
        new CompensableActivity  
        {  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new ChargeCreditCard(),  
                    new SimulatedErrorCondition(),  
                    new ReserveFlight()  
                }  
            },  
            CompensationHandler = new CancelFlight(),  
            CancellationHandler = new CancelCreditCard()  
        },  
        new ManagerApproval(),  
        new PurchaseFlight()  
    }  
};  
```  
  
 W tym przykładzie przedstawiono przepływ pracy w języku XAML  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <Sequence>  
      <c:ChargeCreditCard />  
      <c:SimulatedErrorCondition />  
      <c:ReserveFlight />  
    </Sequence>  
    <CompensableActivity.CancellationHandler>  
      <c:CancelCreditCard />  
    </CompensableActivity.CancellationHandler>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 Po wywołaniu przepływu pracy obsługi wyjątku warunku błędu symulowane przez aplikację hosta w <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, przepływu pracy zostało anulowane, a logika anulowania <xref:System.Activities.Statements.CompensableActivity> jest wywoływana. W tym przykładzie logiki kompensacji i logiki anulowania mają różnych celów. Jeśli <xref:System.Activities.Statements.CompensableActivity.Body%2A> zakończyła się pomyślnie, a następnie oznacza to, karta kredytowa została obciążona i lot rezerwacji, więc rekompensaty należy cofnąć obu czynności. (W tym przykładzie anulowanie lot automatycznie anuluje obciążenia karty kredytowej.) Jednak jeśli <xref:System.Activities.Statements.CompensableActivity> zostało anulowane, oznacza to, że <xref:System.Activities.Statements.CompensableActivity.Body%2A> została nie pełny i tak logiki <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> musi być możliwe ustalenie sposobu obsługi najlepiej anulowania. W tym przykładzie <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> anuluje opłaty karty kredytowej, ale ponieważ `ReserveFlight` został ostatniego działania <xref:System.Activities.Statements.CompensableActivity.Body%2A>, nie próbuje anulować lot. Ponieważ `ReserveFlight` został ostatniego działania <xref:System.Activities.Statements.CompensableActivity.Body%2A>, jeśli pomyślnie ukończył, a następnie <xref:System.Activities.Statements.CompensableActivity.Body%2A> czy wykonali i anulowania nie jest możliwe.  
  
 **ChargeCreditCard: Karty kredytowej opłat transmitowane.**  
**SimulatedErrorCondition: Zgłaszanie ApplicationException.**   
**Przepływ pracy nieobsługiwany wyjątek:**   
**System.ApplicationException: Symulowane błąd w przepływie pracy.**   
**CancelCreditCard: Anulowanie obciążenia karty kredytowej.**   
**Przepływ pracy został ukończony pomyślnie o stanie: anulowane.**  [!INCLUDE[crabout](../../../includes/crabout-md.md)] Anulowanie, zobacz [anulowania](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a>Za pomocą jawnego kompensacji kompensacji działania  
 W poprzedniej sekcji objęte niejawne kompensacji. Niejawne kompensacji może być odpowiednie dla scenariuszy prostego, ale jeśli dokładniejsze wymagana jest kontrola nad planowaniem następnie Obsługa kompensacji <xref:System.Activities.Statements.Compensate> działanie może być używane. Aby zainicjować proces kompensacji z <xref:System.Activities.Statements.Compensate> działania, <xref:System.Activities.Statements.CompensationToken> z <xref:System.Activities.Statements.CompensableActivity> dla których kompensacji jest pożądane jest używana. <xref:System.Activities.Statements.Compensate> Działanie może być używane do inicjowania kompensacji na dowolnym ukończone <xref:System.Activities.Statements.CompensableActivity> który nie został potwierdzone lub skompensowane. Na przykład <xref:System.Activities.Statements.Compensate> działanie może być używane w <xref:System.Activities.Statements.TryCatch.Catches%2A> sekcji <xref:System.Activities.Statements.TryCatch> działania lub w dowolnym momencie po <xref:System.Activities.Statements.CompensableActivity> zostało ukończone. W tym przykładzie <xref:System.Activities.Statements.Compensate> działania jest używana w <xref:System.Activities.Statements.TryCatch.Catches%2A> sekcji <xref:System.Activities.Statements.TryCatch> działania, aby odwrócić akcję <xref:System.Activities.Statements.CompensableActivity>.  
  
 [!code-csharp[CFX_CompensationExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 W tym przykładzie przedstawiono przepływ pracy w języku XAML.  
  
```xaml  
<TryCatch  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:s="clr-namespace:System;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <TryCatch.Variables>  
    <Variable  
       x:TypeArguments="CompensationToken"  
       x:Name="__ReferenceID0"  
       Name="token1" />  
  </TryCatch.Variables>  
  <TryCatch.Try>  
    <Sequence>  
      <CompensableActivity>  
        <CompensableActivity.Result>  
          <OutArgument  
             x:TypeArguments="CompensationToken">  
            <VariableReference  
               x:TypeArguments="CompensationToken"  
               Variable="{x:Reference __ReferenceID0}">  
              <VariableReference.Result>  
                <OutArgument  
                   x:TypeArguments="Location(CompensationToken)" />  
              </VariableReference.Result>  
            </VariableReference>  
          </OutArgument>  
        </CompensableActivity.Result>  
        <CompensableActivity.CompensationHandler>  
          <c:CancelFlight />  
        </CompensableActivity.CompensationHandler>  
        <CompensableActivity.ConfirmationHandler>  
          <c:ConfirmFlight />  
        </CompensableActivity.ConfirmationHandler>  
        <c:ReserveFlight />  
      </CompensableActivity>  
      <c:SimulatedErrorCondition />  
      <c:ManagerApproval />  
      <c:PurchaseFlight />  
    </Sequence>  
  </TryCatch.Try>  
  <TryCatch.Catches>  
    <Catch  
       x:TypeArguments="s:ApplicationException">  
      <ActivityAction  
         x:TypeArguments="s:ApplicationException">  
        <Compensate>  
          <Compensate.Target>  
            <InArgument  
               x:TypeArguments="CompensationToken">  
              <VariableValue  
                 x:TypeArguments="CompensationToken"  
                 Variable="{x:Reference __ReferenceID0}">  
                <VariableValue.Result>  
                  <OutArgument  
                     x:TypeArguments="CompensationToken" />  
                </VariableValue.Result>  
              </VariableValue>  
            </InArgument>  
          </Compensate.Target>  
        </Compensate>  
      </ActivityAction>  
    </Catch>  
  </TryCatch.Catches>  
</TryCatch>  
```  
  
 Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
  
 **ReserveFlight: Biletu jest zarezerwowana.**  
**SimulatedErrorCondition: Zgłaszanie ApplicationException.**   
**CancelFlight: Biletu zostało anulowane.**   
**Przepływ pracy został ukończony pomyślnie o stanie: zamknięte.**    
### <a name="confirming-compensation"></a>Potwierdzenie kompensacji  
 Domyślnie compensable działania kompensowane mogą być dowolnym momencie po zakończeniu. W niektórych scenariuszach to może nie być odpowiednie. W poprzednim przykładzie kompensacji do rezerwowania bilet był anulowania rezerwacji. Jednak po ukończeniu lot ten krok kompensacji nie jest już prawidłowy. Potwierdzenie compensable działania wywołuje aktywność, określony przez <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>. Jedno możliwe użycie tego jest umożliwienie wszystkie zasoby, które są niezbędne do wykonania kompensacji do zwolnienia. Po potwierdzeniu compensable działania, nie jest możliwe na jej kompensowane i to próbie <xref:System.InvalidOperationException> wyjątku. Po pomyślnym zakończeniu przepływu pracy, wszystkich potwierdzone — równoważone compensable działań i pomyślnie wykonanych zostało potwierdzone w odwrotnej kolejności wykonania. W tym przykładzie lot jest zastrzeżone, zakupione i ukończone, a następnie compensable działania został potwierdzony. Aby potwierdzić <xref:System.Activities.Statements.CompensableActivity>, użyj <xref:System.Activities.Statements.Confirm> działania i określ <xref:System.Activities.Statements.CompensationToken> z <xref:System.Activities.Statements.CompensableActivity> o potwierdzenie.  
  
 [!code-csharp[CFX_CompensationExample#4](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 W tym przykładzie przedstawiono przepływ pracy w języku XAML.  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
  </Sequence.Variables>  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken">  
        <VariableReference  
           x:TypeArguments="CompensationToken">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(CompensationToken)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="CompensationToken"  
               x:Name="__ReferenceID0"  
               Name="token1" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <CompensableActivity.ConfirmationHandler>  
      <c:ConfirmFlight />  
    </CompensableActivity.ConfirmationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
  <c:TakeFlight />  
  <Confirm>  
    <Confirm.Target>  
      <InArgument  
         x:TypeArguments="CompensationToken">  
        <VariableValue  
           x:TypeArguments="CompensationToken"  
           Variable="{x:Reference __ReferenceID0}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="CompensationToken" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </Confirm.Target>  
  </Confirm>  
</Sequence>  
```  
  
 Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
  
 **ReserveFlight: Biletu jest zarezerwowana.**  
**ManagerApproval: Zgoda menedżera Odebrano.**   
**PurchaseFlight: Biletu została zakupiona.**   
**TakeFlight: Transmitowane zostanie ukończona.**   
**ConfirmFlight: Transmitowane nie podjęto, nie kompensacji możliwe.**   
**Przepływ pracy został ukończony pomyślnie o stanie: zamknięte.**   
## <a name="nesting-compensation-activities"></a>Zagnieżdżanie kompensacji działania  
 A <xref:System.Activities.Statements.CompensableActivity> mogą być umieszczane w <xref:System.Activities.Statements.CompensableActivity.Body%2A> sekcji innego <xref:System.Activities.Statements.CompensableActivity>. A <xref:System.Activities.Statements.CompensableActivity> nie mogą być wprowadzane do obsługi innego <xref:System.Activities.Statements.CompensableActivity>. Jest odpowiedzialny za elementem nadrzędnym <xref:System.Activities.Statements.CompensableActivity> aby upewnić się, że gdy jest anulowane, potwierdzone lub skompensowane, wszystkie działania compensable podrzędne, które zostały ukończone pomyślnie i jeszcze nie zostały potwierdzone lub skompensowane musi zostać potwierdzone lub Skompensowane przed zakończeniem nadrzędnego kompensacji, potwierdzenia lub anulowania. Jeśli nie jest to wyraźnie modelowane nadrzędnego <xref:System.Activities.Statements.CompensableActivity> zostanie niejawnie kompensacji działania compensable podrzędne odebranie nadrzędnego Anuluj lub kompensacji sygnału. Jeśli element nadrzędny Odebrano sygnał Potwierdź nadrzędnego niejawnie potwierdzi compensable działań podrzędnych. Jeśli logika obsługi kompensacji, potwierdzenia lub anulowania jawnie w modelu obsługi elementu nadrzędnego <xref:System.Activities.Statements.CompensableActivity>, podrzędny nie jest jawnie obsługiwany zostanie potwierdzone niejawnie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.Statements.CompensableActivity>  
 <xref:System.Activities.Statements.Compensate>  
 <xref:System.Activities.Statements.Confirm>  
 <xref:System.Activities.Statements.CompensationToken>  
 [Działanie kompensacyjne](../../../docs/framework/windows-workflow-foundation/samples/compensable-activity-sample.md)
