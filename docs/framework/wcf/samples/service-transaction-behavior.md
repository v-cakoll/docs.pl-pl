---
title: Zachowanie transakcji usługi
ms.date: 03/30/2017
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
ms.openlocfilehash: 38ad03d64d95e0653fba8018c59c62db9a698096
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715109"
---
# <a name="service-transaction-behavior"></a>Zachowanie transakcji usługi

Ten przykład ilustruje użycie transakcji skoordynowanej przez klienta oraz ustawień ServiceBehaviorAttribute i OperationBehaviorAttribute będący w celu sterowania zachowaniem transakcji usługi. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora, ale jest rozszerzony do obsługi dziennika na serwerze wykonanych operacji w tabeli bazy danych, a stanowa suma uruchamiania operacji kalkulatora. Utrwalone zapisy w tabeli dziennika serwera są zależne od wyniku skoordynowanej transakcji klienta — Jeśli transakcja klienta nie została ukończona, transakcja usługi sieci Web gwarantuje, że aktualizacje bazy danych nie zostaną zatwierdzone.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

Umowa dla usługi definiuje, że wszystkie operacje wymagają transakcji, aby można było przepływać żądania:

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

Aby włączyć przepływ transakcji przychodzących, usługa jest konfigurowana z wsHttpBinding udostępnionym przez system z atrybutem transactionFlow ustawionym na `true`. To powiązanie używa protokołu międzyoperacyjnego WSAtomicTransactionOctober2004:

```xml
<bindings>
  <wsHttpBinding>
    <binding name="transactionalBinding" transactionFlow="true" />
  </wsHttpBinding>
</bindings>
```

Po zainicjowaniu połączenia z usługą i transakcją klient uzyskuje dostęp do kilku operacji usługi w zakresie tej transakcji, a następnie kończy transakcję i zamyka połączenie:

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

W usłudze istnieją trzy atrybuty, które mają wpływ na zachowanie transakcji usługi i są one w następujący sposób:

- Na `ServiceBehaviorAttribute`:

  - Właściwość `TransactionTimeout` określa przedział czasu, w którym transakcja musi zostać zakończona. W tym przykładzie jest ustawiony na 30 sekund.

  - Właściwość `TransactionIsolationLevel` określa poziom izolacji obsługiwany przez usługę. Jest to wymagane w celu dopasowania do poziomu izolacji klienta.

  - Właściwość `ReleaseServiceInstanceOnTransactionComplete` określa, czy wystąpienie usługi jest odtwarzane po zakończeniu transakcji. Ustawiając `false`, usługa utrzymuje to samo wystąpienie usługi w ramach żądań operacji. Jest to wymagane, aby zachować sumę uruchomienia. W przypadku wybrania wartości `true`nowe wystąpienie zostanie wygenerowane po wykonaniu każdej akcji zakończonej.

  - Właściwość `TransactionAutoCompleteOnSessionClose` określa, czy oczekujące transakcje są uzupełniane po zamknięciu sesji. Ustawiając je na `false`, poszczególne operacje są wymagane do ustawienia właściwości <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> na `true` lub jawne wymaganie wywołania metody <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> w celu ukończenia transakcji. Ten przykład ilustruje oba podejścia.

- Na `ServiceContractAttribute`:

  - Właściwość `SessionMode` określa, czy usługa skorelować odpowiednie żądania w sesji logicznej. Ponieważ ta usługa obejmuje operacje, w których Właściwość TransactionAutoComplete OperationBehaviorAttribute będący jest ustawiona na wartość `false` (mnożenie i dzielenie), należy określić `SessionMode.Required`. Na przykład operacja mnożenia nie kończy transakcji i zamiast tego opiera się na późniejszej wywołaniu do dzielenia, aby zakończyć przy użyciu metody `SetTransactionComplete`. Usługa musi być w stanie określić, że te operacje są wykonywane w ramach tej samej sesji.

- Na `OperationBehaviorAttribute`:

  - Właściwość `TransactionScopeRequired` określa, czy akcje operacji powinny być wykonywane w zakresie transakcji. Ta wartość jest ustawiana na `true` dla wszystkich operacji w tym przykładzie, a ponieważ klient przepływa do wszystkich operacji, akcje są wykonywane w zakresie tej transakcji klienta.

  - Właściwość `TransactionAutoComplete` określa, czy transakcja, w której wykonywana jest metoda, jest automatycznie uzupełniana w przypadku braku nieobsłużonych wyjątków. Jak opisano wcześniej, jest to `true` dla operacji dodawania i odejmowania, ale `false` operacji mnożenia i dzielenia. Operacje dodawania i odejmowania automatycznie uzupełniają swoje akcje, podział wykonuje swoje działania za pomocą jawnego wywołania metody `SetTransactionComplete`, a mnożenie nie kończy wykonywania akcji, ale zamiast tego jest zależne od i wymaga późniejszego wywołania, takiego jak dzielenie, w celu wykonania akcji.

Implementacja usługi z atrybutami jest następująca:

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

    // Logging method omitted for brevity
}
```

Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.

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

Rejestrowanie żądań operacji usługi jest wyświetlane w oknie konsoli usługi. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.

```console
Press <ENTER> to terminate service.
Creating new service instance...
  Writing row 1 to database: Adding 100 to 0
  Writing row 2 to database: Subtracting 45 from 100
  Writing row 3 to database: Multiplying 55 by 9
  Writing row 4 to database: Dividing 495 by 15
```

Należy pamiętać, że oprócz przechowywania sumy całkowitej obliczeń usługa zgłasza Tworzenie wystąpień (jedno wystąpienie dla tego przykładu) i rejestruje żądania operacji w bazie danych. Ze względu na to, że wszystkie żądania przepływają transakcję klienta, wszelkie niepowodzenie wykonania tej transakcji spowoduje wycofanie wszystkich operacji bazy danych. Można to przedstawić na kilka sposobów:

- Dodaj komentarz do wywołania klienta do `tx.Complete`() i uruchom ponownie — spowoduje to zamknięcie przez klienta zakresu transakcji bez wykonywania transakcji.

- Dodaj komentarz do wywołania operacji dzielenia usługi — spowoduje to uniemożliwienie akcji zainicjowanej przez operację mnożenia i w ten sposób zakończenie transakcji klienta kończy się niepowodzeniem.

- Zgłoś nieobsługiwany wyjątek w dowolnym miejscu w zakresie transakcji klienta — w podobny sposób uniemożliwia klientowi wykonywanie transakcji.

Wynik któregokolwiek z tych elementów polega na tym, że żadna z operacji wykonywanych w ramach tego zakresu nie zostanie zatwierdzona, a liczba wierszy utrwalonych w bazie danych nie jest zwiększana.

> [!NOTE]
> W ramach procesu kompilacji plik bazy danych jest kopiowany do folderu bin. Należy przyjrzeć się tej kopii pliku bazy danych, aby obserwować wiersze, które są utrwalane w dzienniku, a nie plik, który jest zawarty w projekcie programu Visual Studio.

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że zainstalowano SQL Server 2005 Express Edition lub SQL Server 2005. W pliku App. config usługi można ustawić `connectionString` bazy danych lub można wyłączyć interakcje z bazą danych, ustawiając wartość ustawienia appSettings `usingSql` na `false`.

2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

W przypadku uruchamiania przykładu między maszynami należy skonfigurować usługę Microsoft Distributed Transaction Coordinator (MSDTC), aby włączyć przepływ transakcji sieciowych i użyć narzędzia WsatConfig. exe w celu włączenia sieci Windows Communication Foundation (WCF) pomocy.

### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a>Aby skonfigurować Distributed Transaction Coordinator firmy Microsoft (MSDTC) do obsługi przykładowego między maszynami

1. Na maszynie usługi Skonfiguruj usługę MSDTC w taki sposób, aby zezwalała na przychodzące transakcje sieciowe.

    1. W menu **Start** przejdź do **Panelu sterowania**, a następnie **Narzędzia administracyjne**, a następnie **usługi składowe**.

    2. Kliknij prawym przyciskiem myszy pozycję **mój komputer** , a następnie wybierz pozycję **Właściwości**.

    3. Na karcie **MSDTC** kliknij pozycję **Konfiguracja zabezpieczeń**.

    4. Sprawdź **dostęp do usługi Network DTC** i **Zezwalaj na ruch przychodzący**.

    5. Kliknij przycisk **tak** , aby ponownie uruchomić usługę MS DTC, a następnie kliknij przycisk **OK**.

    6. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.

2. Na maszynie usługi i na komputerze klienckim Skonfiguruj zaporę systemu Windows w taki sposób, aby zawierała Distributed Transaction Coordinator firmy Microsoft (MSDTC) do listy wykluczonych aplikacji:

    1. Uruchom aplikację Zapora systemu Windows z panelu sterowania.

    2. Na karcie **wyjątki** kliknij pozycję **Dodaj program**.

    3. Przejdź do folderu C:\WINDOWS\System32.

    4. Wybierz pozycję MSDTC. exe i kliknij przycisk **Otwórz**.

    5. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Dodawanie programu** , a następnie kliknij przycisk **OK** ponownie, aby zamknąć aplet Zapora systemu Windows.

3. Na komputerze klienckim Skonfiguruj usługę MSDTC tak, aby zezwalała na wychodzące transakcje sieciowe:

    1. W menu **Start** przejdź do **Panelu sterowania**, a następnie **Narzędzia administracyjne**, a następnie **usługi składowe**.

    2. Kliknij prawym przyciskiem myszy pozycję **mój komputer** , a następnie wybierz pozycję **Właściwości**.

    3. Na karcie **MSDTC** kliknij pozycję **Konfiguracja zabezpieczeń**.

    4. Sprawdź **dostęp do usługi Network DTC** i **Zezwalaj na ruch wychodzący**.

    5. Kliknij przycisk **tak** , aby ponownie uruchomić usługę MS DTC, a następnie kliknij przycisk **OK**.

    6. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`
