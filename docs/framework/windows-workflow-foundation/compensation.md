---
title: Kompensacja
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 75c5ed2f5e5c3a93834632ce499a2c8195fbc6bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183003"
---
# <a name="compensation"></a>Kompensacja
Wynagrodzenie w Fundacji Przepływu Pracy systemu Windows (WF) to mechanizm, za pomocą którego wcześniej ukończona praca może zostać cofnięta lub skompensowane (zgodnie z logiką zdefiniowaną przez aplikację) po wystąpieniu kolejnej awarii. W tej sekcji opisano sposób używania kompensacji w przepływach pracy.  
  
## <a name="compensation-vs-transactions"></a>Rekompensata a transakcje  
 Transakcja umożliwia łączenie wielu operacji w jedną jednostkę pracy. Za pomocą transakcji daje aplikacji możliwość przerwania (wycofać) wszystkie zmiany wykonane z wewnątrz transakcji, jeśli wystąpią błędy podczas dowolnej części procesu transakcji. Jednak przy użyciu transakcji może nie być odpowiednie, jeśli praca jest długotrwała. Na przykład aplikacja planowania podróży jest implementowana jako przepływ pracy. Kroki przepływu pracy mogą polegać na rezerwacji lotu, oczekiwaniu na zatwierdzenie przez menedżera, a następnie opłaceniu lotu. Proces ten może potrwać wiele dni i nie jest praktyczne dla kroków rezerwacji i płacenia za lot do udziału w tej samej transakcji. W takim scenariuszu kompensacja może służyć do cofania kroku rezerwacji przepływu pracy, jeśli w dalszej części przetwarzania wystąpi błąd.  
  
> [!NOTE]
> W tym temacie opisano wynagrodzenie w przepływach pracy. Aby uzyskać więcej informacji o transakcjach [Transactions](workflow-transactions.md) w <xref:System.Activities.Statements.TransactionScope>przepływach pracy, zobacz Transakcje i . Aby uzyskać więcej informacji <xref:System.Transactions?displayProperty=nameWithType> o <xref:System.Transactions.Transaction?displayProperty=nameWithType>transakcjach, zobacz i .  
  
## <a name="using-compensableactivity"></a>Korzystanie z compensableActivity  
 <xref:System.Activities.Statements.CompensableActivity>jest podstawową działalnością kompensacyjną w [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Wszelkie działania, które wykonują pracę, która może wymagać rekompensaty są umieszczane w <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity>pliku . W tym przykładzie etap rezerwacji zakupu lotu <xref:System.Activities.Statements.CompensableActivity.Body%2A> jest <xref:System.Activities.Statements.CompensableActivity> umieszczany w a, a <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>anulowanie rezerwacji jest umieszczane w pliku . Natychmiast po <xref:System.Activities.Statements.CompensableActivity> w przepływie pracy są dwa działania, które czekają na zatwierdzenie menedżera, a następnie zakończyć etap zakupu lotu. Jeśli warunek błędu powoduje, że przepływ pracy <xref:System.Activities.Statements.CompensableActivity> zostanie anulowany po pomyślnym <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> zakończeniu, a następnie działania w programie obsługi są zaplanowane i lot jest anulowany.  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 Poniższy przykład jest przepływ pracy w XAML.  
  
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
  
 Po wywołaniu przepływu pracy do konsoli są wyświetlane następujące dane wyjściowe.  
  
 **ReserveFlight: Bilet jest zarezerwowany.**  
**ManagerApproval: Otrzymano zatwierdzenie menedżera.** 
 **PurchaseFlight: Bilet jest zakupiony.** 
 **Przepływ pracy został pomyślnie zakończony ze stanem: Zamknięte.**
> [!NOTE]
> Przykładowe działania w tym `ReserveFlight` temacie, takie jak wyświetlanie ich nazwy i celu w konsoli, aby pomóc zilustrować kolejność wykonywania działań w przypadku wystąpienia rekompensaty.  
  
### <a name="default-workflow-compensation"></a>Domyślna kompensacja przepływu pracy  
 Domyślnie, jeśli przepływ pracy zostanie anulowany, logika kompensacji jest uruchamiana dla każdego działania wyrównawczego, które zostało pomyślnie całkowicie potwierdzone i nie zostało jeszcze potwierdzone lub zrekompensowane.  
  
> [!NOTE]
> <xref:System.Activities.Statements.CompensableActivity> Po *potwierdzeniu*, rekompensata za działanie nie może być już wywoływana. Proces potwierdzenia jest opisany w dalszej części tej sekcji.  
  
 W tym przykładzie wyjątek jest zgłaszany po zarezerwuje lot, ale przed krokiem zatwierdzenia menedżera.  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 W tym przykładzie jest przepływ pracy w języku XAML.  
  
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
  
 [!code-csharp[CFX_CompensationExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 Po wywołaniu przepływu pracy symulowany wyjątek warunku błędu jest <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>obsługiwany przez aplikację hosta w , przepływ pracy jest anulowany, a logika kompensacji jest wywoływana.  
  
 **ReserveFlight: Bilet jest zarezerwowany.**  
**SymulowaneErrorCondition: Throwing ApplicationException.** 
 **Nieobsługiwał się wyjątek:**
**System.ApplicationException: Symulowany warunek błędu w przepływie pracy.** 
 **CancelFlight: Bilet został anulowany.** 
 **Przepływ pracy został pomyślnie zakończony ze stanem: Anulowano.**
### <a name="cancellation-and-compensableactivity"></a>Anulowanie i wyrównawcza aktywność  
 Jeśli działania w <xref:System.Activities.Statements.CompensableActivity.Body%2A> a <xref:System.Activities.Statements.CompensableActivity> nie zostały zakończone, a działanie zostanie anulowane, działania w są <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> wykonywane.  
  
> [!NOTE]
> Wywoływane <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> jest tylko wtedy, gdy <xref:System.Activities.Statements.CompensableActivity.Body%2A> działania <xref:System.Activities.Statements.CompensableActivity> w nie zostały zakończone, a działanie zostanie anulowane. Jest <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> wykonywany tylko wtedy, gdy <xref:System.Activities.Statements.CompensableActivity.Body%2A> działania <xref:System.Activities.Statements.CompensableActivity> w pomyślnie zakończone i rekompensata jest następnie wywoływana na działanie.  
  
 Daje <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> autorom przepływu pracy możliwość zapewnienia odpowiedniej logiki anulowania. W poniższym przykładzie wyjątek jest zgłaszany podczas wykonywania <xref:System.Activities.Statements.CompensableActivity.Body%2A>, a następnie <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> jest wywoływany.  
  
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
  
 W tym przykładzie jest przepływ pracy w języku XAML  
  
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
  
 Gdy przepływ pracy jest wywoływany, symulowany wyjątek warunku <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>błędu jest obsługiwany przez aplikację hosta w <xref:System.Activities.Statements.CompensableActivity> , przepływ pracy jest anulowany, a logika anulowania jest wywoływana. W tym przykładzie logiki wynagrodzeń i logiki anulowania mają różne cele. Jeśli <xref:System.Activities.Statements.CompensableActivity.Body%2A> ukończono pomyślnie, oznacza to, że karta kredytowa została obciążona i lot zarezerwowany, więc odszkodowanie powinno cofnąć oba kroki. (W tym przykładzie anulowanie lotu powoduje automatyczne anulowanie opłat za kartę kredytową). Jednak jeśli <xref:System.Activities.Statements.CompensableActivity> jest anulowane, oznacza <xref:System.Activities.Statements.CompensableActivity.Body%2A> to, że nie została <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> ukończona, a więc logika musi być w stanie określić, jak najlepiej obsługiwać anulowanie. W tym przykładzie <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> anuluje obciążenie kartą kredytową, ale ponieważ `ReserveFlight` była to ostatnia czynność w <xref:System.Activities.Statements.CompensableActivity.Body%2A>, nie próbuje anulować lotu. Ponieważ `ReserveFlight` była to ostatnia działalność w <xref:System.Activities.Statements.CompensableActivity.Body%2A>, <xref:System.Activities.Statements.CompensableActivity.Body%2A> gdyby została pomyślnie zakończona, to by się zakończyła i nie byłoby możliwe anulowanie.  
  
 **ChargeCreditCard: Obciąż kartę kredytową za lot.**  
**SymulowaneErrorCondition: Throwing ApplicationException.** 
 **Nieobsługiwał się wyjątek:**
**System.ApplicationException: Symulowany warunek błędu w przepływie pracy.** 
 **CancelCreditCard: Anuluj opłaty za karty kredytowe.** 
 **Przepływ pracy został pomyślnie zakończony ze stanem: Anulowano.**  Aby uzyskać więcej informacji na temat anulowania, zobacz [Anulowanie](modeling-cancellation-behavior-in-workflows.md).  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a>Jawna kompensacja przy użyciu działania kompensacji  
 W poprzedniej sekcji uwzględniono niejawną rekompensatę. Niejawna kompensacja może być odpowiednia dla prostych scenariuszy, ale jeśli <xref:System.Activities.Statements.Compensate> bardziej jawna kontrola jest wymagana w harmonogramie obsługi wynagrodzeń, działanie może być używane. Aby rozpocząć proces rekompensaty <xref:System.Activities.Statements.Compensate> z <xref:System.Activities.Statements.CompensationToken> działalnością, stosuje się rekompensatę, <xref:System.Activities.Statements.CompensableActivity> dla której wymagana jest rekompensata. Działanie <xref:System.Activities.Statements.Compensate> może służyć do inicjowania <xref:System.Activities.Statements.CompensableActivity> rekompensaty za wszystkie ukończone, które nie zostały potwierdzone lub zrekompensowane. Na przykład <xref:System.Activities.Statements.Compensate> działanie może być <xref:System.Activities.Statements.TryCatch.Catches%2A> używane w <xref:System.Activities.Statements.TryCatch> sekcji działania lub <xref:System.Activities.Statements.CompensableActivity> w dowolnym momencie po zakończeniu. W <xref:System.Activities.Statements.Compensate> tym przykładzie działanie jest <xref:System.Activities.Statements.TryCatch.Catches%2A> używane <xref:System.Activities.Statements.TryCatch> w sekcji działania, <xref:System.Activities.Statements.CompensableActivity>aby odwrócić akcję .  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 W tym przykładzie jest przepływ pracy w języku XAML.  
  
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
  
 Po wywołaniu przepływu pracy do konsoli są wyświetlane następujące dane wyjściowe.  
  
 **ReserveFlight: Bilet jest zarezerwowany.**  
**SymulowaneErrorCondition: Throwing ApplicationException.** 
 **CancelFlight: Bilet został anulowany.** 
 **Przepływ pracy został pomyślnie zakończony ze stanem: Zamknięte.**
### <a name="confirming-compensation"></a>Potwierdzenie odszkodowania  
 Domyślnie działania podlegające kompensacji można zrekompensować w dowolnym momencie po ich zakończeniu. W niektórych scenariuszach może to nie być właściwe. W poprzednim przykładzie rekompensatą za rezerwację biletu było anulowanie rezerwacji. Jednak po zakończeniu lotu ten etap rekompensaty nie jest już ważny. Potwierdzenie działania kompensacyjnego wywołuje działanie określone <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>przez . Jednym z możliwych zastosowań jest umożliwienie wszelkich zasobów, które są niezbędne do wykonania rekompensaty, które mają zostać zwolnione. Po potwierdzenie działania kompensacyjnego nie jest możliwe, aby uzyskać rekompensatę, <xref:System.InvalidOperationException> a jeśli jest to próba wyjątek. Po pomyślnym zakończeniu przepływu pracy wszystkie nieuwarzanowane i niekompensowane działania kompensacyjne, które zakończyły się pomyślnie, są potwierdzane w odwrotnej kolejności. W tym przykładzie lot jest zarezerwowany, zakupiony i ukończony, a następnie działanie wyrównawalne zostaje potwierdzone. Aby <xref:System.Activities.Statements.CompensableActivity>potwierdzić , <xref:System.Activities.Statements.Confirm> użyj działania <xref:System.Activities.Statements.CompensationToken> i <xref:System.Activities.Statements.CompensableActivity> określ to, aby potwierdzić.  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 W tym przykładzie jest przepływ pracy w języku XAML.  
  
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
  
Po wywołaniu przepływu pracy do konsoli są wyświetlane następujące dane wyjściowe.  
  
**ReserveFlight: Bilet jest zarezerwowany.**  
**ManagerApproval: Otrzymano zatwierdzenie menedżera.** 
 **PurchaseFlight: Bilet jest zakupiony.** 
 **TakeFlight: Lot jest zakończony.** 
 **Potwierdź Lot: Lot został wykonany, nie ma możliwości odszkodowania.** 
 **Przepływ pracy został pomyślnie zakończony ze stanem: Zamknięte.**

## <a name="nesting-compensation-activities"></a>Zagnieżdżanie działań kompensacyjnych  

A <xref:System.Activities.Statements.CompensableActivity> można umieścić <xref:System.Activities.Statements.CompensableActivity.Body%2A> w sekcji <xref:System.Activities.Statements.CompensableActivity>innego . A <xref:System.Activities.Statements.CompensableActivity> nie mogą być umieszczone <xref:System.Activities.Statements.CompensableActivity>w obsłudze innego . Obowiązkiem rodzica <xref:System.Activities.Statements.CompensableActivity> jest zapewnienie, że po anulowaniu, potwierdzeniu lub wypłacie odszkodowania wszystkie czynności podlegające wyrównaniu dziecka, które zostały zakończone pomyślnie i nie zostały jeszcze potwierdzone lub zrekompensowane, muszą zostać potwierdzone lub zrekompensowane przed zakończeniem przez rodzica anulowania, potwierdzenia lub odszkodowania. Jeśli nie jest to modelowane <xref:System.Activities.Statements.CompensableActivity> jawnie nadrzędny będzie niejawnie kompensować podrzędnych compensable działań, jeśli rodzic otrzymał anuluj lub kompensować sygnał. Jeśli rodzic otrzymał sygnał potwierdzenia, rodzic niejawnie potwierdzi podrzędne działania podlegające kompensacjom. Jeśli logika do obsługi anulowania, potwierdzenia lub odszkodowania jest jawnie wzorowany w programie obsługi nadrzędnego, <xref:System.Activities.Statements.CompensableActivity>każdy element podrzędny nie jawnie obsługiwane zostaną niejawnie potwierdzone.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
