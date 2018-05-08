---
title: Przepływ transakcji WS
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 699ba3efad0c8b98aacfc4b64f2fdf03270478b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ws-transaction-flow"></a>Przepływ transakcji WS
W tym przykładzie przedstawiono użycie transakcji koordynowane przez klienta i opcji na kliencie i serwerze dla transakcji przepływu przy użyciu protokołu WS-Atomic Transaction albo OleTransactions. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator, ale operacje są przypisane do przedstawiają sposób używania `TransactionFlowAttribute` z **właściwość TransactionFlowOption** wyliczenie, aby ustalić, jakie transakcji stopnia przepływu jest włączone. W zakresie transakcji dziennik żądanych operacji są zapisywane do bazy danych i będzie się powtarzał dopiero po ukończeniu transakcji klienta koordynowane — Jeśli transakcja klienta nie zostanie ukończone, transakcja usługi sieci Web zapewnia, że odpowiednie aktualizacje bazy danych nie są przekazywane.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Po zainicjowaniu połączenia usługi i transakcji, klient uzyskuje dostęp do wielu operacji usługi. Kontrakt usługi jest zdefiniowana w następujący sposób z każdej operacji prezentacja inne ustawienie `TransactionFlowOption`.  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Allowed)]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.NotAllowed)]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);   
}  
```

 Definiuje operacje w kolejności, które mają być przetwarzane:  
  
-   `Add` Żądanie operacji musi zawierać przesłanej transakcji.  
  
-   A `Subtract` żądanie operacji mogą obejmować przesłanej transakcji.  
  
-   A `Multiply` żądanie operacji nie może zawierać przesłanej transakcji przez jawne ustawienie NotAllowed.  
  
-   A `Divide` żądanie operacji nie może zawierać przesłanej transakcji przez pominięcie `TransactionFlow` atrybutu.  
  
 Aby włączyć przepływu transakcji, powiązania z [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) właściwość włączone, należy użyć oprócz atrybutów odpowiednie działania. W tym przykładzie konfiguracji usługi przedstawia punktu końcowego TCP i punkt końcowy HTTP oprócz punkt końcowy wymiany metadanych. Punkt końcowy protokołu TCP i punkt końcowy HTTP należy użyć następujących powiązania, które mają [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) właściwości włączone.  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding name="transactionalOleTransactionsTcpBinding"  
             transactionFlow="true"  
             transactionProtocol="OleTransactions"/>  
  </netTcpBinding>  
  <wsHttpBinding>  
    <binding name="transactionalWsatHttpBinding"  
             transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
> [!NOTE]
>  NetTcpBinding dostarczane przez system umożliwia specyfikacji element transactionProtocol, natomiast wsHttpBinding dostarczane przez system używa tylko więcej współdziałanie protokołu WSAtomicTransactionOctober2004. OleTransactions, który protokół jest dostępna tylko dla potrzeb klientów usługi Windows Communication Foundation (WCF).  
  
 Dla klasy implementującej `ICalculator` interfejsu, wszystkie metody atrybut z <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> ustawioną właściwość `true`. To ustawienie deklaruje, że wszystkie akcje wykonywane w metodzie występuje w zakresie transakcji. W takim przypadku akcje wykonywane obejmują rejestrowanie do dziennika bazy danych. Jeśli żądanie operacji zawiera przesłanej transakcji zachodzą akcje w zakresie transakcji przychodzącej lub nowego zakresu transakcji są generowane automatycznie.  
  
> [!NOTE]
>  <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> Właściwość definiuje zachowanie lokalnej do implementacji metody usługi i nie definiuje możliwość klienta lub wymaganie przepływu transakcji.  

```csharp
// Service class that implements the service contract.  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Add(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Subtract(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n2, n1));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Multiply(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Divide(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
    // Logging method omitted for brevity  
}  
```

 Na klienta, usługa `TransactionFlowOption` ustawień na operacje są uwzględniane w definicji wygenerowanego klienta `ICalculator` interfejsu. Ponadto usługi `transactionFlow` ustawienia właściwości są uwzględniane w konfiguracji aplikacji klienta. Klient może wybrać transportu i protokół przez wybranie odpowiedniej `endpointConfigurationName`.  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
>  Obserwowanych zachowanie w tym przykładzie jest taka sama niezależnie od tego, który jest wybierany protokołu lub transportu.  
  
 Po zainicjowaniu połączenia z usługą Klient tworzy nową `TransactionScope` wokół wywołania do operacji usługi.  

```csharp
// Start a transaction scope  
using (TransactionScope tx =  
            new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation  
    //  - generatedClient will flow the required active transaction  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("  Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation  
    //  - generatedClient will flow the allowed active transaction  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Start a transaction scope that suppresses the current transaction  
    using (TransactionScope txSuppress =  
                new TransactionScope(TransactionScopeOption.Suppress))  
    {  
        // Call the Subtract service operation  
        //  - the active transaction is suppressed from the generatedClient  
        //    and no transaction will flow  
        value1 = 21.05D;  
        value2 = 42.16D;  
        result = client.Subtract(value1, value2);  
        Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
        // Complete the suppressed scope  
        txSuppress.Complete();  
    }  
  
    // Call the Multiply service operation  
    // - generatedClient will not flow the active transaction  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("  Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    // - generatedClient will not flow the active transaction  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("  Divide({0},{1}) = {2}", value1, value2, result);  
  
    // Complete the transaction scope  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
```

 Wywołania do operacji są następujące:  
  
-   `Add` Żądania przepływu transakcji wymagane do usługi i są wykonywane działania usługi w zakresie transakcji klienta.  
  
-   Pierwszy `Subtract` żądania przepływa również dozwolonych transakcji do usługi i ponownie wykonywane działania usługi w zakresie transakcji klienta.  
  
-   Drugi `Subtract` żądania odbywa się w zakresie nowych transakcji zadeklarowana z `TransactionScopeOption.Suppress` opcji. Pomija to początkowa transakcji zewnętrznej klienta i żądania nie przepływu transakcji z usługą. Takie podejście umożliwia klientowi jawnie zrezygnować z i chronić przepływu transakcji do usługi, po którym nie jest wymagana. Akcje usługi występuje w zakresie nowych i odłączony transakcji.  
  
-   `Multiply` Żądania nie przepływu transakcji do usługi, ponieważ klient obiektu wygenerowana definicji `ICalculator` interfejs zawiera <xref:System.ServiceModel.TransactionFlowAttribute> ustawioną <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`.  
  
-   `Divide` Żądania nie przepływu transakcji do usługi, ponieważ ponownie klienta do wygenerowanych definicji `ICalculator` nie ma interfejsu `TransactionFlowAttribute`. W zakresie nowych i odłączony transakcja wykonywane ponownie działania usługi.  
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Starting transaction  
  Add(100,15.99) = 115.99  
  Subtract(145,76.54) = 68.46  
  Subtract(21.05,42.16) = -21.11  
  Multiply(9,81.25) = 731.25  
  Divide(22,7) = 3.14285714285714  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 Rejestrowanie żądań operacji usługi są wyświetlane w oknie konsoli usługi. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 Po pomyślnym wykonaniu kończy zakresu transakcji klienta, a wszystkie akcje wykonywane w ramach tego zakresu są zatwierdzone. W szczególności dostrzeżone 5 rekordów są zachowywane w bazie danych usługi. Pierwsze 2 one wystąpiły w zakresie transakcji klienta.  
  
 Jeśli wystąpił wyjątek dowolne miejsce w ramach klienta `TransactionScope` , a następnie nie może ukończyć transakcji. Powoduje to, że rekordy zarejestrowane w ramach tego zakresu, które mają nie być przekazane do bazy danych. W tym celu można zaobserwować, powtarzając próbki po komentowania limit wywołania do wykonania zewnętrznego `TransactionScope`. Takie uruchomieniu tylko ostatnich 3 akcje (od drugiego `Subtract`, `Multiply` i `Divide` żądań) są rejestrowane, ponieważ transakcja klienta nie przepływać do tych.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Aby utworzyć wersję języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)  
  
2.  Upewnij się, że zainstalowano program SQL Server Express Edition lub SQL Server i czy ciąg połączenia został poprawnie ustawiony w pliku konfiguracyjnym aplikacji usługi. Aby uruchomić przykładowy bez korzystania z bazy danych, ustaw `usingSql` wartości w pliku konfiguracyjnym aplikacji usługi do `false`  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Do konfiguracji między komputerami Włącz Koordynator transakcji rozproszonych, korzystając z poniższych instrukcji, a narzędzie WsatConfig.exe z zestawu Windows SDK, aby włączyć obsługę sieci transakcji WCF. Zobacz [Konfigurowanie obsługi transakcji protokołu WS-AT](http://go.microsoft.com/fwlink/?LinkId=190370) informacji na temat konfigurowania WsatConfig.exe.  
  
 Czy można uruchomić przykład na tym samym komputerze lub na różnych komputerach, należy skonfigurować MSDTC Microsoft Distributed Transaction Coordinator () do włączenia przepływu transakcji sieci i włączyć za pomocą narzędzia WsatConfig.exe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transakcji Obsługa sieci.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a>Aby skonfigurować MSDTC Microsoft Distributed Transaction Coordinator () do obsługi systemem próbki  
  
1.  Na maszynie usługi z systemem Windows Server 2003 lub Windows XP należy skonfigurować usługi MSDTC umożliwia przychodzących transakcji sieci, wykonując następujące instrukcje.  
  
    1.  Z **Start** menu, przejdź do **Panelu sterowania**, następnie **narzędzia administracyjne**, a następnie **usługi składowe**.  
  
    2.  Rozwiń węzeł **usługi składowe**. Otwórz **komputery** folderu.  
  
    3.  Kliknij prawym przyciskiem myszy **Mój komputer** i wybierz **właściwości**.  
  
    4.  Na **MSDTC** , kliknij pozycję **konfiguracji zabezpieczeń**.  
  
    5.  Sprawdź **sieci dostęp do usługi DTC** i **Zezwalaj na przychodzące**.  
  
    6.  Kliknij przycisk **OK**, następnie kliknij przycisk **tak** ponowne uruchomienie usługi MSDTC.  
  
    7.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
2.  Na maszynie usługi z systemem Windows Server 2008 lub Windows Vista należy skonfigurować usługi MSDTC umożliwia przychodzących transakcji sieci, wykonując następujące instrukcje.  
  
    1.  Z **Start** menu, przejdź do **Panelu sterowania**, następnie **narzędzia administracyjne**, a następnie **usługi składowe**.  
  
    2.  Rozwiń węzeł **usługi składowe**. Otwórz **komputery** folderu. Wybierz **Koordynator transakcji rozproszonych**.  
  
    3.  Kliknij prawym przyciskiem myszy **koordynator usługi DTC** i wybierz **właściwości**.  
  
    4.  Na **zabezpieczeń** karcie wyboru **usługa DTC Network Access** i **Zezwalaj na przychodzące**.  
  
    5.  Kliknij przycisk **OK**, następnie kliknij przycisk **tak** ponowne uruchomienie usługi MSDTC.  
  
    6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
3.  Na komputerze klienckim należy skonfigurować usługi MSDTC, aby umożliwić wychodzących transakcji sieci:  
  
    1.  Z **Start** menu, przejdź do `Control Panel`, następnie **narzędzia administracyjne**, a następnie **usługi składowe**.  
  
    2.  Kliknij prawym przyciskiem myszy **Mój komputer** i wybierz **właściwości**.  
  
    3.  Na **MSDTC** , kliknij pozycję **konfiguracji zabezpieczeń**.  
  
    4.  Sprawdź **sieci dostęp do usługi DTC** i **Zezwalaj na wychodzące**.  
  
    5.  Kliknij przycisk **OK**, następnie kliknij przycisk **tak** ponowne uruchomienie usługi MSDTC.  
  
    6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
