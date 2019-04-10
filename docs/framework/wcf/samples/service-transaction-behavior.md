---
title: Zachowanie transakcji usługi
ms.date: 03/30/2017
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
ms.openlocfilehash: db120df1b2efd28cc484c3749bb22fc2196e9dd4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339947"
---
# <a name="service-transaction-behavior"></a>Zachowanie transakcji usługi
Niniejszy przykład pokazuje użycie transakcji koordynowane przez klienta i ustawień ServiceBehaviorAttribute i gdy, aby kontrolować zachowanie transakcji usługi. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementuje usługi Kalkulator, ale jest rozszerzony do obsługi operacji wykonywanych w tabeli bazy danych i stanowe, Suma operacji Kalkulator dziennika serwera. Utrwalonych zapisy do tabeli dziennika serwera są zależne od wyniku transakcji klienta koordynowany — Jeśli transakcja klienta nie zostanie ukończone, transakcji usługi sieci Web zapewnia aktualizacji do bazy danych nie są przekazywane.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Kontrakt usługi określa, że wszystkie operacje wymagają przepływu za pomocą żądań transakcji:  
  
```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples",  
                    SessionMode = SessionMode.Required)]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Subtract(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Multiply(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Divide(double n);  
}  
```  
  
 Aby umożliwić ruch przychodzący transakcji, usługa jest skonfigurowana z wsHttpBinding dostarczane przez system za pomocą atrybutu transactionFlow równa `true`. Międzyoperacyjne protokołu WSAtomicTransactionOctober2004 używa tego powiązania:  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="transactionalBinding" transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
 Po zainicjowaniu zarówno połączenia usługi i transakcji, klient uzyskuje dostęp do kilku operacji usługi w zakresie transakcji wykonuje transakcję i zamyka połączenie:  
  
```csharp
// Create a client  
CalculatorClient client = new CalculatorClient();  
  
// Create a transaction scope with the default isolation level of Serializable  
using (TransactionScope tx = new TransactionScope())  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation.  
    double value = 100.00D;  
    Console.WriteLine("  Adding {0}, running total={1}",  
                                        value, client.Add(value));  
  
    // Call the Subtract service operation.  
    value = 45.00D;  
    Console.WriteLine("  Subtracting {0}, running total={1}",  
                                        value, client.Subtract(value));  
  
    // Call the Multiply service operation.  
    value = 9.00D;  
    Console.WriteLine("  Multiplying by {0}, running total={1}",  
                                        value, client.Multiply(value));  
  
    // Call the Divide service operation.  
    value = 15.00D;  
    Console.WriteLine("  Dividing by {0}, running total={1}",  
                                        value, client.Divide(value));  
  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
  
// Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
 W usłudze istnieją trzy atrybuty, które wpływają na zachowanie transakcji usługi i mogą to zrobić w następujący sposób:  
  
-   Na `ServiceBehaviorAttribute`:  
  
    -   `TransactionTimeout` Właściwości określa okres czasu, w którym należy wykonać transakcję. W tym przykładzie jest ustawiona na 30 sekund.  
  
    -   `TransactionIsolationLevel` Właściwość określa poziom izolacji, który obsługuje usługę. Jest to wymagane, aby dopasować poziom izolacji klienta.  
  
    -   `ReleaseServiceInstanceOnTransactionComplete` Właściwość określa, czy wystąpienie usługi zostanie odtworzony po zakończeniu transakcji. Ustawiając wartość `false`, usługa zapewnia tego samego wystąpienia usługi przez żądania operacji. Jest to wymagane, aby zachować łączna liczba uruchomionych. Jeśli ustawiono `true`, nowe wystąpienie jest generowany po wykonaniu każdej akcji.  
  
    -   `TransactionAutoCompleteOnSessionClose` Właściwość określa, czy zaległe transakcje odbywa się po zamknięciu sesji. Ustawiając wartość `false`, poszczególnych operacji są wymagane do któryś zbiór <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> właściwości `true` lub jawnie wymaga wywołania <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> metody do realizowania transakcji. W przykładzie pokazano oba podejścia.  
  
-   Na `ServiceContractAttribute`:  
  
    -   `SessionMode` Właściwość określa, czy usługa jest skorelowane odpowiednich żądań do sesji logicznej. Ponieważ ta usługa obejmuje operacje, w których ustawiono właściwość wartość gdy TransactionAutoComplete `false` mnożenia i dzielenia, `SessionMode.Required` musi być określona. Na przykład mnożenie operacji transakcji nie zostanie zakończone i zamiast tego opiera się na nowszych wywołanie dzielenia można wykonać przy użyciu `SetTransactionComplete` metody; usługa musi być możliwe ustalenie, czy te operacje są wykonywane w ramach tej samej sesji.  
  
-   Na `OperationBehaviorAttribute`:  
  
    -   `TransactionScopeRequired` Właściwość określa, czy wykonać operację akcji powinny być wykonywane w zakresie transakcji. Jest ono ustawione na `true` dla wszystkich operacji w tym przykładowy i, ponieważ klient przepływy transakcji do wszystkich operacji, w zakresie transakcji klienta mają być wykonywane akcje.  
  
    -   `TransactionAutoComplete` Właściwość określa, czy transakcji, w którym metoda jest wykonywana jest wprowadzana automatycznie, jeśli wystąpi żaden nieobsługiwany wyjątek. Jak opisano wcześniej, jest ono ustawione na `true` operacji dodawania i odejmowania, ale `false` Multiply i operacji dzielenia. Automatyczne ukończenie operacji dodawania i odejmowania ich działania, dzielenia ukończeniu akcji za pomocą jawnego wywołania `SetTransactionComplete` metoda Multiply swoje działania nie zostanie ukończone, ale zamiast tego opiera się na i wymaga nowszej wywołanie, takich jak Podziel do wykonania akcji.  
  
 Implementacja opartego na atrybutach usługi jest w następujący sposób:  
  
```csharp
[ServiceBehavior(  
    TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
    TransactionTimeout = "00:00:30",  
    ReleaseServiceInstanceOnTransactionComplete = false,  
    TransactionAutoCompleteOnSessionClose = false)]  
public class CalculatorService : ICalculator  
{  
    double runningTotal;  
  
    public CalculatorService()  
    {  
        Console.WriteLine("Creating new service instance...");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Add(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n, runningTotal));  
        runningTotal = runningTotal + n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Subtract(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n, runningTotal));  
        runningTotal = runningTotal - n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Multiply(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal * n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Divide(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal / n;  
        OperationContext.Current.SetTransactionComplete();  
        return runningTotal;  
    }  
  
    // Logging method ommitted for brevity  
}   
```  
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```console  
Starting transaction  
Performing calculations...  
  Adding 100, running total=100  
  Subtracting 45, running total=55  
  Multiplying by 9, running total=495  
  Dividing by 15, running total=33  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 Rejestrowanie żądania operacji usług są wyświetlane w oknie konsoli tej usługi. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```console  
Press <ENTER> to terminate service.  
Creating new service instance...  
  Writing row 1 to database: Adding 100 to 0  
  Writing row 2 to database: Subtracting 45 from 100  
  Writing row 3 to database: Multiplying 55 by 9  
  Writing row 4 to database: Dividing 495 by 15  
```  
  
 Należy pamiętać, że oprócz utrzymywanie łączna liczba uruchomionych obliczeń, usługa raporty tworzenia wystąpień (jednego wystąpienia w tym przykładzie) i rejestruje żądania operacji bazy danych. Ponieważ wszystkie żądania przepływu transakcji klienta, jakiekolwiek niepowodzenie, aby ukończyć tej transakcji powoduje we wszystkich operacji wycofywane w bazie danych. To mogą być przedstawiane na kilka sposobów:  
  
-   Komentarz wywołania klienta `tx.Complete`() i ponownie uruchom - skutkiem klienta Kończenie zakresu transakcji bez ukończenie jego transakcji.  
  
-   Komentarz dotyczący out wywołania operacji usługi dzielenia — powoduje to zapobiec akcji zainicjowanej przez mnożenia ukończenie operacji i dlatego transakcji klienta ostatecznie również nie powiedzie się.  
  
-   Throw Wystąpił nieobsługiwany wyjątek w dowolnym miejscu w zakresie transakcji klienta — podobnie zapobiega to klient ukończenie jego transakcji.  
  
 Wynikiem tych jest czy żaden z operacji wykonywanych w tym zakresie nie jest zatwierdzona i liczbę wierszy utrwalone w bazie danych zwiększa się.  
  
> [!NOTE]
>  Jako część procesu kompilacji pliku bazy danych jest kopiowany do folderu bin. Należy Przyjrzyj się tej kopii pliku bazy danych do obserwowania wierszy, które są zachowywane w dzienniku, a nie plik, który znajduje się w projekcie programu Visual Studio.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że zainstalowano program SQL Server 2005 Express Edition lub SQL Server 2005. W pliku App.config usługi bazy danych `connectionString` może być zestaw lub bazy danych, interakcje mogą być wyłączone przez ustawienia appSettings `usingSql` wartość `false`.  
  
2. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Po uruchomieniu przykładu na komputerach, należy skonfigurować transakcję Koordynator MSDTC (Microsoft Distributed) Włączanie przepływu transakcji sieci i włączanie usługi Windows Communication Foundation (WCF) transakcji sieci za pomocą narzędzia WsatConfig.exe Pomoc techniczna.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a>Aby skonfigurować transakcji Koordynator MSDTC (Microsoft Distributed) do obsługi działa aplikacja przykładowa na komputerach  
  
1. Na komputerze usługi należy skonfigurować usługi MSDTC, aby zezwolić na przychodzące transakcje sieciowe.  
  
    1.  Z **Start** menu, przejdź do **Panelu sterowania**, następnie **narzędzia administracyjne**, a następnie **usługi składowe**.  
  
    2.  Kliknij prawym przyciskiem myszy **Mój komputer** i wybierz **właściwości**.  
  
    3.  Na **MSDTC** kliknij pozycję **konfiguracji zabezpieczeń**.  
  
    4.  Sprawdź **DTC dostęp sieciowy** i **zezwolić na przychodzący**.  
  
    5.  Kliknij przycisk **tak** Uruchom ponownie usługę MS DTC, a następnie kliknij przycisk **OK**.  
  
    6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
2. Na komputerze usługi i komputerze klienckim należy skonfigurować zaporę Windows obejmujący transakcji Koordynator MSDTC (Microsoft Distributed) do listy aplikacji wyjątku:  
  
    1.  Uruchom aplikację Zapora Windows z poziomu Panelu sterowania.  
  
    2.  Z **wyjątki** kliknij pozycję **Dodaj Program**.  
  
    3.  Przejdź do folderu C:\WINDOWS\System32.  
  
    4.  Msdtc.exe wybierz i kliknij przycisk **Otwórz**.  
  
    5.  Kliknij przycisk **OK** zamknąć **Dodaj Program** okno dialogowe, a następnie kliknij przycisk **OK** ponownie, aby zamknąć aplet Zapora Windows.  
  
3. Na komputerze klienckim należy skonfigurować usługi MSDTC, aby zezwolić na wychodzące transakcje sieciowe:  
  
    1.  Z **Start** menu, przejdź do **Panelu sterowania**, następnie **narzędzia administracyjne**, a następnie **usługi składowe**.  
  
    2.  Kliknij prawym przyciskiem myszy **Mój komputer** i wybierz **właściwości**.  
  
    3.  Na **MSDTC** kliknij pozycję **konfiguracji zabezpieczeń**.  
  
    4.  Sprawdź **DTC dostęp sieciowy** i **Zezwalaj na wychodzące**.  
  
    5.  Kliknij przycisk **tak** Uruchom ponownie usługę MS DTC, a następnie kliknij przycisk **OK**.  
  
    6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`  
