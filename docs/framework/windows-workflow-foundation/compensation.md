---
title: Kompensacja
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 147da26fd297d41876815cffcc70450ae905ba85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935427"
---
# <a name="compensation"></a>Kompensacja
Kompensacja w Windows Workflow Foundation (WF) to mechanizm, za pomocą którego poprzednio ukończona czynność może zostać cofnięta lub wynagradzana (zgodnie z logiką zdefiniowaną przez aplikację) w przypadku wystąpienia kolejnego błędu. W tej sekcji opisano sposób korzystania z kompensacji w przepływach pracy.  
  
## <a name="compensation-vs-transactions"></a>Kompensacja a Transakcje  
 Transakcja umożliwia łączenie wielu operacji w pojedynczą jednostkę pracy. Użycie transakcji umożliwia aplikacji przerwanie (Przywracanie) wszystkich zmian wykonywanych w ramach transakcji w przypadku wystąpienia błędów występujących w ramach procesu transakcji. Jednak użycie transakcji może być nieodpowiednie, jeśli prace są długotrwałe. Na przykład aplikacja do planowania podróży jest zaimplementowana jako przepływ pracy. Kroki przepływu pracy mogą obejmować zarezerwowanie lotu, oczekiwanie na zatwierdzenie przez kierownika, a następnie zapłacenie za lot. Ten proces może potrwać wiele dni i nie jest praktyczny w przypadku czynności związanych z rezerwacją i uiszczeniem opłat za uczestnictwo w tej samej transakcji. W takim scenariuszu można użyć kompensacji w celu cofnięcia etapu rezerwacji przepływu pracy w przypadku wystąpienia błędu w dalszej części przetwarzania.  
  
> [!NOTE]
> W tym temacie omówiono odszkodowanie w przepływach pracy. Aby uzyskać więcej informacji o transakcjach w [](workflow-transactions.md) przepływach <xref:System.Activities.Statements.TransactionScope>pracy, zobacz transakcje i. Aby uzyskać więcej informacji na temat transakcji <xref:System.Transactions?displayProperty=nameWithType> , <xref:System.Transactions.Transaction?displayProperty=nameWithType>Zobacz i.  
  
## <a name="using-compensableactivity"></a>Korzystanie z działanie CompensableActivity  
 <xref:System.Activities.Statements.CompensableActivity>to podstawowe działanie związane z kompensacją w programie [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Wszelkie działania wykonujące zadania, które mogą być wymagane do uzyskania wynagrodzenia, są umieszczane <xref:System.Activities.Statements.CompensableActivity.Body%2A> w <xref:System.Activities.Statements.CompensableActivity>. W tym przykładzie etap rezerwacji zakupu lotu jest umieszczany w <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> a, a anulowanie <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>rezerwacji jest umieszczane w. Natychmiast po <xref:System.Activities.Statements.CompensableActivity> przeniesieniu do przepływu pracy są dwa działania, które oczekują na zatwierdzenie przez Menedżera, a następnie ukończą krok zakupu lotu. Jeśli warunek błędu powoduje, że przepływ pracy zostanie anulowany po <xref:System.Activities.Statements.CompensableActivity> pomyślnym zakończeniu, wówczas działania w ramach <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> programu obsługi są zaplanowane, a lot zostanie anulowany.  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 Poniższy przykład to przepływ pracy w języku XAML.  
  
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
  
 Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu.  
  
 **ReserveFlight: Bilet jest zarezerwowany.**  
**ManagerApproval: Odebrano zatwierdzenie przez Menedżera.**    
**PurchaseFlight: Zakupiony bilet.**    
**Przepływ pracy został pomyślnie ukończony ze stanem: Napis.**    
> [!NOTE]
> Przykładowe działania w tym temacie, takie jak `ReserveFlight` wyświetlanie ich nazwy i przeznaczenia do konsoli programu, aby ułatwić zilustrowanie kolejności, w której działania są wykonywane, gdy nastąpi kompensacja.  
  
### <a name="default-workflow-compensation"></a>Domyślna kompensacja przepływu pracy  
 Domyślnie, jeśli przepływ pracy zostanie anulowany, logika kompensacji jest uruchamiana dla wszystkich działań kompensacyjne, które zostały pomyślnie kompletne i nie zostały jeszcze potwierdzone lub wynagradzane.  
  
> [!NOTE]
> Po potwierdzeniu, nie można już wywołać kompensaty dla działania. <xref:System.Activities.Statements.CompensableActivity> Proces potwierdzania został opisany w dalszej części tej sekcji.  
  
 W tym przykładzie wyjątek jest zgłaszany po zarezerwacji lotu, ale przed etapem zatwierdzania przez Menedżera.  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 Ten przykład to przepływ pracy w języku XAML.  
  
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
  
 Gdy przepływ pracy jest wywoływany, wyjątek symulowanego warunku błędu jest obsługiwany przez aplikację hosta w <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, przepływ pracy zostanie anulowany, a logika kompensacji jest wywoływana.  
  
 **ReserveFlight: Bilet jest zarezerwowany.**  
**SimulatedErrorCondition: Zgłaszanie elementu ApplicationException.**    
**Nieobsługiwany wyjątek przepływu pracy:**    
**System. ApplicationException: Symulowany warunek błędu w przepływie pracy.**    
**CancelFlight: Bilet został anulowany.**    
**Przepływ pracy został pomyślnie ukończony ze stanem: Szkodliw.**    
### <a name="cancellation-and-compensableactivity"></a>Anulowanie i działanie CompensableActivity  
 Jeśli działania w <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> ramach programu nie zostały ukończone i działanie zostało anulowane <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> , działania w programie są wykonywane.  
  
> [!NOTE]
> Jest <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> wywoływana tylko w przypadku, gdy działania <xref:System.Activities.Statements.CompensableActivity.Body%2A> z programu <xref:System.Activities.Statements.CompensableActivity> nie zostały ukończone i działanie zostało anulowane. Jest wykonywane tylko wtedy, gdy działania <xref:System.Activities.Statements.CompensableActivity.Body%2A> z programu <xref:System.Activities.Statements.CompensableActivity> zostały pomyślnie wykonane i wynagrodzenie jest następnie wywoływane dla działania. <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>  
  
 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Daje autorom przepływu pracy możliwość zapewnienia odpowiedniej logiki anulowania. W poniższym przykładzie wyjątek jest zgłaszany podczas wykonywania <xref:System.Activities.Statements.CompensableActivity.Body%2A>, a <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> następnie wywoływany.  
  
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
  
 Ten przykład to przepływ pracy w języku XAML  
  
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
  
 Gdy przepływ pracy jest wywoływany, wyjątek symulowanego warunku błędu jest obsługiwany przez aplikację hosta w <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, przepływ pracy zostanie anulowany, a logika <xref:System.Activities.Statements.CompensableActivity> anulowania jest wywoływana. W tym przykładzie logika kompensacji i logika anulowania mają różne cele. Jeśli zakończyło się <xref:System.Activities.Statements.CompensableActivity.Body%2A> pomyślnie, oznacza to, że opłata za kartę kredytową została naliczona i jest ona księgowana zgodnie z zapisem, dlatego należy cofnąć obie czynności. (W tym przykładzie anulowanie lotu automatycznie anuluje opłaty za kartę kredytową). Jeśli <xref:System.Activities.Statements.CompensableActivity> jednak zostanie anulowana, oznacza to, że <xref:System.Activities.Statements.CompensableActivity.Body%2A> nie została ukończona, a <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> więc logika musi być w stanie określić, jak najlepiej obsłużyć anulowanie. W tym przykładzie <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> anuluje opłaty za kartę kredytową, ale od czasu `ReserveFlight` ostatniego działania w programie <xref:System.Activities.Statements.CompensableActivity.Body%2A>nie jest podejmowana próba anulowania lotu. Ponieważ `ReserveFlight` była ostatnią aktywnością <xref:System.Activities.Statements.CompensableActivity.Body%2A>w programie, w przypadku pomyślnego wykonania <xref:System.Activities.Statements.CompensableActivity.Body%2A> operacji zostałaby ukończona i nie będzie możliwe jej anulowanie.  
  
 **ChargeCreditCard: Opłata za kartę kredytową dla lotu.**  
**SimulatedErrorCondition: Zgłaszanie elementu ApplicationException.**    
**Nieobsługiwany wyjątek przepływu pracy:**    
**System. ApplicationException: Symulowany warunek błędu w przepływie pracy.**    
**CancelCreditCard: Anuluj opłaty za karty kredytowe.**    
**Przepływ pracy został pomyślnie ukończony ze stanem: Szkodliw.**  Aby uzyskać więcej informacji na temat anulowania, zobacz [anulowania](modeling-cancellation-behavior-in-workflows.md).  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a>Jawne wynagrodzenie przy użyciu działania kompensacja  
 W poprzedniej sekcji podano niejawną kompensację. Niejawne kompensacje mogą być odpowiednie w przypadku prostych scenariuszy, ale jeśli jest wymagana bardziej jawna kontrola nad planowaniem <xref:System.Activities.Statements.Compensate> obsługi kompensacji, działanie może być używane. W celu zainicjowania procesu <xref:System.Activities.Statements.Compensate> kompensacji działania <xref:System.Activities.Statements.CompensationToken> należy użyć elementu <xref:System.Activities.Statements.CompensableActivity> , dla którego jest wymagana kompensacja. Działanie może służyć do inicjowania kompensaty dla wszystkich ukończonych <xref:System.Activities.Statements.CompensableActivity> , które nie zostały potwierdzone lub wynagradzane. <xref:System.Activities.Statements.Compensate> Na przykład <xref:System.Activities.Statements.Compensate> działanie może być używane <xref:System.Activities.Statements.TryCatch.Catches%2A> w sekcji <xref:System.Activities.Statements.TryCatch> działania lub w dowolnym momencie po <xref:System.Activities.Statements.CompensableActivity> zakończeniu. W tym przykładzie <xref:System.Activities.Statements.Compensate> działanie jest używane <xref:System.Activities.Statements.TryCatch.Catches%2A> w sekcji <xref:System.Activities.Statements.TryCatch> działania w celu odwrócenia akcji <xref:System.Activities.Statements.CompensableActivity>.  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 Ten przykład to przepływ pracy w języku XAML.  
  
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
  
 Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu.  
  
 **ReserveFlight: Bilet jest zarezerwowany.**  
**SimulatedErrorCondition: Zgłaszanie elementu ApplicationException.**    
**CancelFlight: Bilet został anulowany.**    
**Przepływ pracy został pomyślnie ukończony ze stanem: Napis.**    
### <a name="confirming-compensation"></a>Potwierdzanie kompensaty  
 Domyślnie działania kompensacyjne mogą być kompensowane w dowolnym momencie po zakończeniu. W niektórych scenariuszach może to nie być odpowiednie. W poprzednim przykładzie wynagrodzenie związane z odświadczeniem biletu zostało anulowane. Jednak po ukończeniu lotu ten krok kompensaty nie jest już ważny. Potwierdzenie działania kompensacyjne wywołuje działanie określone przez <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>. Jednym z tych możliwości jest umożliwienie wszelkim zasobom, które są niezbędne do zwolnienia wyrównania. Po potwierdzeniu działania kompensacyjne nie jest możliwe jego kompensowanie, a jeśli zostanie podjęta próba <xref:System.InvalidOperationException> , zostanie zgłoszony wyjątek. Gdy przepływ pracy zakończy się pomyślnie, wszystkie niepotwierdzone i niekompensowane działania kompensacyjne, które zostały zakończone pomyślnie, są potwierdzone w odwrotnej kolejności uzupełniania. W tym przykładzie lot jest zastrzeżony, zakupiony i zakończony, a następnie działanie kompensacyjne zostało potwierdzone. Aby potwierdzić <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Confirm> Użyj <xref:System.Activities.Statements.CompensationToken> działania<xref:System.Activities.Statements.CompensableActivity> i określ, aby potwierdzić.  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 Ten przykład to przepływ pracy w języku XAML.  
  
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
  
Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu.  
  
**ReserveFlight: Bilet jest zarezerwowany.**  
**ManagerApproval: Odebrano zatwierdzenie przez Menedżera.**    
**PurchaseFlight: Zakupiony bilet.**    
**TakeFlight: Działanie lotu zostało zakończone.**    
**ConfirmFlight: Nastąpiło przeprowadzenie lotu, bez możliwości dokonania kompensacji.**    
**Przepływ pracy został pomyślnie ukończony ze stanem: Napis.**   

## <a name="nesting-compensation-activities"></a>Zagnieżdżanie działań związanych z kompensacją  

Można umieścić w sekcji innej <xref:System.Activities.Statements.CompensableActivity>. <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> Nie może być umieszczony w procedurze obsługi innej <xref:System.Activities.Statements.CompensableActivity>. <xref:System.Activities.Statements.CompensableActivity> Zadaniem nadrzędnym <xref:System.Activities.Statements.CompensableActivity> jest upewnienie się, że gdy zostanie on anulowany, potwierdzony lub wynagradzany, wszystkie podrzędne działania kompensacyjne, które zostały zakończone pomyślnie i nie zostały jeszcze potwierdzone lub kompensowane, muszą zostać potwierdzone lub kompensowane przed zakończeniem anulowania, potwierdzenia lub kompensacji elementu nadrzędnego. Jeśli nie jest to jawnie modelowane, obiekt <xref:System.Activities.Statements.CompensableActivity> nadrzędny będzie niejawnie kompensować podrzędne działania kompensacyjne, jeśli element nadrzędny otrzymał sygnał Cancel lub kompensacja. Jeśli element nadrzędny otrzymał sygnał Confirm, element nadrzędny będzie niejawnie potwierdzał podrzędne działania kompensacyjne. Jeśli logika do obsługi anulowania, potwierdzenia lub kompensacji jest jawnie modelowana w procedurze obsługi elementu nadrzędnego <xref:System.Activities.Statements.CompensableActivity>, wszelkie elementy podrzędne, które nie zostały jawnie obsłużone, zostaną niejawnie potwierdzone.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
