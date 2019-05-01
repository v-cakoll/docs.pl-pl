---
title: Kompensacja
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: af29ba61ff5bede9208f2ab706f5e0ce1ff12274
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774286"
---
# <a name="compensation"></a>Kompensacja
Rekompensaty w Windows Workflow Foundation (WF) to mechanizm, za pomocą którego wcześniej Praca wykonana można cofnąć lub płatne (następujących logiki, zdefiniowany przez aplikację) podczas kolejnych awarii. W tej sekcji opisano sposób użycia rekompensaty w przepływach pracy.  
  
## <a name="compensation-vs-transactions"></a>Vs wynagrodzenia. Transakcje  
 Transakcja pozwala połączyć wiele operacji w pojedynczą jednostkę pracy. Przy użyciu transakcji daje aplikacji możliwość Przerwij wszystkie zmiany wykonane z w ramach transakcji, jeśli wystąpią błędy podczas dowolnej części procesu transakcji (wycofanie). Jednak za pomocą transakcji może nie być odpowiednie, jeżeli praca jest długo działające. Na przykład aplikacja planowania podróży została zaimplementowana jako przepływ pracy. Kroki przepływu pracy może składać się z rezerwacji lotu, oczekiwanie na zatwierdzenie przez menedżera i następnie płacić lotu. Może to zająć wiele dni, a nie jest praktyczne kroki rezerwacji i płacić za lot do wzięcia udziału w ramach jednej transakcji. W przypadku takich wynagrodzenie może służyć do cofnąć kroku rezerwacji przepływu pracy, jeśli wystąpi awaria w dalszej części przetwarzania.  
  
> [!NOTE]
>  W tym temacie omówiono rekompensaty w przepływach pracy. Aby uzyskać więcej informacji na temat transakcji w przepływach pracy, zobacz [transakcji](workflow-transactions.md) i <xref:System.Activities.Statements.TransactionScope>. Aby uzyskać więcej informacji na temat transakcji, zobacz <xref:System.Transactions?displayProperty=nameWithType> i <xref:System.Transactions.Transaction?displayProperty=nameWithType>.  
  
## <a name="using-compensableactivity"></a>Za pomocą CompensableActivity  
 <xref:System.Activities.Statements.CompensableActivity> jest podstawowym działaniem rekompensaty w [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Każde działanie, które wykonują pracę, która może być konieczne można skompensować są umieszczane w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity>. W tym przykładzie kroku rezerwacji lotu kupowaniu jest umieszczana w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> i anulowania rezerwacji jest umieszczana w <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>. Natychmiast po <xref:System.Activities.Statements.CompensableActivity> w przepływie pracy są dwa działania, które czekać na zatwierdzenie przez menedżera, a następnie Zakończ zakupu kroku podczas lotu. Jeśli warunek błędu powoduje, że przepływ pracy zostaną anulowane po <xref:System.Activities.Statements.CompensableActivity> zostanie pomyślnie zakończony, następnie działania w <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> obsługi są planowane i lotu zostało anulowane.  
  
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
  
 Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
  
 **ReserveFlight: Bilet jest zarezerwowana.**  
**ManagerApproval: Odebrane zatwierdzenia przez menedżera.**   
**PurchaseFlight: Bilet jest sprzedawana.**   
**Przepływ pracy została pomyślnie ukończona ze stanem: Zamknięte.**    
> [!NOTE]
>  Przykładowe działania w tym temacie, takie jak `ReserveFlight` wyświetlane nazwy użytkownika i przeznaczenia konsoli ilustrujących kolejność wykonywania działań, po wystąpieniu wynagrodzenia.  
  
### <a name="default-workflow-compensation"></a>Domyślne Kompensacja przepływu pracy  
 Domyślnie jeśli przepływ pracy zostanie anulowane, logiki wyrównującej jest uruchamiana dla działanie kompensacyjne, który został pomyślnie całkowicie i nie jest jeszcze potwierdzenia lub płatne.  
  
> [!NOTE]
>  Gdy <xref:System.Activities.Statements.CompensableActivity> jest *potwierdzone*, już nie może być wywoływany wynagrodzenia dla działania. Proces potwierdzenia jest później opisane w tej sekcji.  
  
 W tym przykładzie wyjątek jest generowany po lotu jest zastrzeżona, ale przed wykonaniem kroku zatwierdzenia menedżera.  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 W tym przykładzie przedstawiono przepływ pracy w XAML.  
  
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
  
 Po wywołaniu przepływu pracy wyjątek warunku symulowanego błędu jest obsługiwany przez aplikację hosta w <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, przepływ pracy zostanie anulowane i logiki wyrównującej jest wywoływana.  
  
 **ReserveFlight: Bilet jest zarezerwowana.**  
**SimulatedErrorCondition: Zgłaszanie applicationexception —.**   
**Przepływ pracy nieobsługiwany wyjątek:**   
**System.ApplicationException: Symulowane warunek błędu w przepływie pracy.**   
**CancelFlight: Zgłoszenie zostało anulowane.**   
**Przepływ pracy została pomyślnie ukończona ze stanem: Anulowane.**    
### <a name="cancellation-and-compensableactivity"></a>Anulowanie i CompensableActivity  
 Jeśli działania w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> mają nie zakończone i zostanie anulowane działania, działania w <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> są wykonywane.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Jest wywoływana tylko w przypadku działania w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> nie została ukończona i działanie zostało anulowane. <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> Jest wykonywana tylko w przypadku działania w <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> zostało wykonane pomyślnie ukończone i rekompensaty jest później wywoływana działania.  
  
 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Zapewnia przedstawienie dowolnej logiki anulowania odpowiednie autorzy przepływu pracy. W poniższym przykładzie, zgłaszany jest wyjątek podczas wykonywania <xref:System.Activities.Statements.CompensableActivity.Body%2A>, a następnie <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> zostanie wywołana.  
  
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
  
 W tym przykładzie przedstawiono przepływ pracy w XAML  
  
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
  
 Po wywołaniu przepływu pracy wyjątek warunku symulowanego błędu jest obsługiwany przez aplikację hosta w <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, przepływ pracy zostanie anulowane i logikę anulowania <xref:System.Activities.Statements.CompensableActivity> zostanie wywołana. W tym przykładzie logiki wyrównującej i logikę anulowania mają inne cele. Jeśli <xref:System.Activities.Statements.CompensableActivity.Body%2A> zakończone pomyślnie, a następnie oznacza to, karta kredytowa została obciążona i rezerwacji lotu, dlatego rekompensaty należy cofnąć oba kroki. (W tym przykładzie anulowanie lotu automatycznie anuluje obciążenia karty kredytowej.) Jednak jeśli <xref:System.Activities.Statements.CompensableActivity> zostanie anulowane, oznacza to, że <xref:System.Activities.Statements.CompensableActivity.Body%2A> została nie kompletne i dlatego logiki <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> musi być możliwe ustalenie, jak najlepiej obsługiwać anulowanie. W tym przykładzie <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> anuluje opłata kartą kredytową, ale ponieważ `ReserveFlight` został ostatniego działania <xref:System.Activities.Statements.CompensableActivity.Body%2A>, nie próbuje anulować lotu. Ponieważ `ReserveFlight` został ostatniego działania <xref:System.Activities.Statements.CompensableActivity.Body%2A>, jeśli pomyślnie ukończył, a następnie <xref:System.Activities.Statements.CompensableActivity.Body%2A> czy zostały wykonane i anulowania nie byłoby możliwe.  
  
 **ChargeCreditCard: Opłata za karty kredytowej na potrzeby lotu.**  
**SimulatedErrorCondition: Zgłaszanie applicationexception —.**   
**Przepływ pracy nieobsługiwany wyjątek:**   
**System.ApplicationException: Symulowane warunek błędu w przepływie pracy.**   
**CancelCreditCard: Anuluj obciążenia karty kredytowej.**   
**Przepływ pracy została pomyślnie ukończona ze stanem: Anulowane.**  Aby uzyskać więcej informacji dotyczących anulowania, zobacz [anulowania](modeling-cancellation-behavior-in-workflows.md).  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a>Za pomocą jawnego wynagrodzenie kompensacji działania  
 W poprzedniej sekcji objęte niejawne wynagrodzenia. Niejawne wynagrodzenie może być odpowiednie dla prostych scenariuszy, ale jeśli dokładniejsze wymagana jest kontrola nad planowaniem wynagrodzenie obsługi następnie <xref:System.Activities.Statements.Compensate> działanie może być używane. Aby zainicjować proces odszkodowania za pomocą <xref:System.Activities.Statements.Compensate> działania, <xref:System.Activities.Statements.CompensationToken> z <xref:System.Activities.Statements.CompensableActivity> wynagrodzenie, która jest pożądane jest używany. <xref:System.Activities.Statements.Compensate> Działanie może być używane do inicjowania rekompensaty w przypadku dowolnego ukończone <xref:System.Activities.Statements.CompensableActivity> który nie został potwierdzony lub płatne. Na przykład <xref:System.Activities.Statements.Compensate> działanie może być używane w <xref:System.Activities.Statements.TryCatch.Catches%2A> części <xref:System.Activities.Statements.TryCatch> działania lub w dowolnym momencie po <xref:System.Activities.Statements.CompensableActivity> zostało zakończone. W tym przykładzie <xref:System.Activities.Statements.Compensate> działania jest używana w <xref:System.Activities.Statements.TryCatch.Catches%2A> części <xref:System.Activities.Statements.TryCatch> działania, aby odwrócić Akcja <xref:System.Activities.Statements.CompensableActivity>.  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 W tym przykładzie przedstawiono przepływ pracy w XAML.  
  
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
  
 **ReserveFlight: Bilet jest zarezerwowana.**  
**SimulatedErrorCondition: Zgłaszanie applicationexception —.**   
**CancelFlight: Zgłoszenie zostało anulowane.**   
**Przepływ pracy została pomyślnie ukończona ze stanem: Zamknięte.**    
### <a name="confirming-compensation"></a>Trwa Potwierdzanie Kompensacja  
 Domyślnie kompensacyjne działań można skompensować dowolnej chwili po zakończeniu. W niektórych przypadkach może to nie być odpowiednie. W poprzednim przykładzie wynagrodzenie do rezerwowania--ticket był anulowania rezerwacji. Jednak po ukończeniu lotu tego kroku wynagrodzenie nie jest już prawidłowy. Potwierdzanie działanie kompensacyjne wywołuje działanie określonego przez <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>. Jedno możliwe użycie tego jest umożliwienie wszystkie zasoby, które są niezbędne do wykonania wynagrodzenie, które mogą być wprowadzane. Po potwierdzeniu działanie kompensacyjne nie jest możliwe, aby mogła być wyrównane, a jeśli to jest podejmowana próba <xref:System.InvalidOperationException> jest zgłaszany wyjątek. Po pomyślnym zakończeniu działania przepływu pracy, wszystkie-potwierdzone i skompensować kompensacyjne działania, które zakończyły się pomyślnie potwierdzone w odwrotnej kolejności wykonania. W tym przykładzie lotu jest zarezerwowana, zakupu i ukończone, a następnie działanie kompensacyjne został potwierdzony. Aby upewnić się, <xref:System.Activities.Statements.CompensableActivity>, użyj <xref:System.Activities.Statements.Confirm> działania i określ <xref:System.Activities.Statements.CompensationToken> z <xref:System.Activities.Statements.CompensableActivity> o potwierdzenie.  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 W tym przykładzie przedstawiono przepływ pracy w XAML.  
  
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
  
**ReserveFlight: Bilet jest zarezerwowana.**  
**ManagerApproval: Odebrane zatwierdzenia przez menedżera.**   
**PurchaseFlight: Bilet jest sprzedawana.**   
**TakeFlight: Został ukończony lot.**   
**ConfirmFlight: Lotu jest zajęty, żadne wynagrodzenie możliwe.**   
**Przepływ pracy została pomyślnie ukończona ze stanem: Zamknięte.**   

## <a name="nesting-compensation-activities"></a>Zagnieżdżanie działania Kompensacja  

A <xref:System.Activities.Statements.CompensableActivity> mogą być umieszczane <xref:System.Activities.Statements.CompensableActivity.Body%2A> części innego <xref:System.Activities.Statements.CompensableActivity>. A <xref:System.Activities.Statements.CompensableActivity> nie mogą być wprowadzane do obsługi innego <xref:System.Activities.Statements.CompensableActivity>. Jest odpowiedzialny za elementem nadrzędnym <xref:System.Activities.Statements.CompensableActivity> aby upewnić się, że gdy jest anulowane, potwierdzony lub skompensować, wszystkie działania kompensacyjne podrzędne, które zostały zakończone powodzeniem i nie zostały potwierdzone lub płatne musi zostać potwierdzone lub wyrównane przed zakończeniem obiektu nadrzędnego, wynagrodzenie, potwierdzenie lub anulowania. Jeśli nie jest to jawnie modelowane nadrzędnego <xref:System.Activities.Statements.CompensableActivity> zostanie niejawnie kompensacji kompensacyjne działania podrzędne, jeśli element nadrzędny otrzymuje anulowanie lub kompensacji sygnału. Jeśli element nadrzędny otrzymał sygnał Potwierdź nadrzędnego niejawnie potwierdzi kompensacyjne działania podrzędne. Jeśli logika obsługi anulowania, potwierdzenia lub odszkodowania jawnie w modelu obsługi nadrzędnego <xref:System.Activities.Statements.CompensableActivity>, wszystkie podrzędne nie są jawnie obsługiwane zostanie potwierdzone niejawnie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
