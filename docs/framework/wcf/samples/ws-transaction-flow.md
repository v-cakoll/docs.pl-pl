---
title: Przepływ transakcji WS
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 35af3090c0f898578a5f8dfb81d02d22a0074ad2
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46007064"
---
# <a name="ws-transaction-flow"></a>Przepływ transakcji WS
Niniejszy przykład pokazuje użycie transakcji koordynowane przez klienta i opcje klienta i serwera dla transakcji przepływu przy użyciu protokołu WS-Atomic Transaction albo OleTransactions. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator, ale operacje są przypisane do pokazują użycie `TransactionFlowAttribute` z **parametru TransactionFlowOption** wyliczenie, aby ustalić, jakie transakcji stopień przepływu jest włączone. W zakresie transakcji w dzienniku żądanych operacji zapisane w bazie danych i będzie nadal występować przed ukończeniem transakcji klienta koordynowany — Jeśli transakcja klienta nie zostanie ukończone, transakcji usługi sieci Web zapewnia, że odpowiednie aktualizacje bazy danych nie są zatwierdzone.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Po zainicjowaniu połączenia z usługi i transakcji, klient uzyskuje dostęp do kilku operacji usługi. Kontrakt usługi jest zdefiniowana w następujący sposób z każdą z operacji ukazujące inne ustawienie `TransactionFlowOption`.  

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

 Definiuje operacji w kolejności, w której mają być przetwarzane, są:  
  
-   `Add` Żądanie operacji musi zawierać transakcji.  
  
-   A `Subtract` żądanie operacji mogą obejmować transakcji.  
  
-   A `Multiply` żądanie operacji nie może zawierać transakcji poprzez jawne ustawienie NotAllowed.  
  
-   A `Divide` żądanie operacji nie może zawierać transakcji za pośrednictwem pominięcie `TransactionFlow` atrybutu.  
  
 Aby włączyć przepływu transakcji, tylko powiązania z [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) właściwość włączone, należy użyć oprócz atrybutów, operacji odpowiednie. W tym przykładzie konfiguracji usługi uwidacznia punkt końcowy protokołu TCP i punkt końcowy HTTP, oprócz punkt końcowy wymiany metadanych. Punkt końcowy protokołu TCP i punkt końcowy HTTP używają następujących powiązania, które mają [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) właściwości włączone.  
  
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
>  NetTcpBinding dostarczane przez system umożliwia określenie element transactionProtocol, natomiast wsHttpBinding dostarczane przez system używa tylko bardziej interoperacyjne protokołu WSAtomicTransactionOctober2004. OleTransactions, który protokół jest dostępna tylko dla potrzeb klientów usługi Windows Communication Foundation (WCF).  
  
 Dla klasy, która implementuje `ICalculator` interfejsu, wszystkie metody są określane za pomocą <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> właściwością `true`. To ustawienie deklaruje, że wszystkie akcje wykonywane w metodzie wystąpić w zakresie transakcji. W tym przypadku akcje wykonywane obejmują rejestrowanie do dziennika bazy danych. Jeśli żądanie operacji zawiera transakcji są wykonywane działania w zakresie transakcji przychodzących lub nowego zakresu transakcji są generowane automatycznie.  
  
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

 Na klienta, usługa `TransactionFlowOption` ustawień na operacje są odzwierciedlane w definicji wygenerowanego klienta `ICalculator` interfejsu. Ponadto usługi `transactionFlow` ustawienia właściwości są odzwierciedlane w konfiguracji aplikacji klienta. Klient może wybrać transportu i protokół, wybierając odpowiednie `endpointConfigurationName`.  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
>  Zaobserwowany zachowanie tego przykładu jest taka sama niezależnie od tego, który jest wybierany protokołu lub transportu.  
  
 Po zainicjowaniu połączenia z usługą klienta tworzy nową `TransactionScope` wokół wywołania operacji usługi.  

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

 Wywołania operacji są następujące:  
  
-   `Add` Żądania przepływu transakcji wymaganych do usługi i są wykonywane działania usługi w zakresie transakcji klienta.  
  
-   Pierwszy `Subtract` żądania również odbywa się dozwolonych transakcji do usługi i ponownie wykonywane działania usługi w zakresie transakcji klienta.  
  
-   Drugi `Subtract` żądania jest wykonywane w ramach zadeklarowany za pomocą nowego zakresu transakcji `TransactionScopeOption.Suppress` opcji. To pomija początkowej transakcji zewnętrznym klienta i żądania nie przepływu transakcji do usługi. Takie podejście umożliwia klientowi jawnie zrezygnować z i chronić przepływu transakcji do usługi, gdy nie jest wymagane. Usługi są wykonywane działania w zakresie nowych i niepołączonych transakcji.  
  
-   `Multiply` Żądania nie przepływu transakcji do usługi, ponieważ klient firmy wygenerowana definicja `ICalculator` interfejs zawiera <xref:System.ServiceModel.TransactionFlowAttribute> równa <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`.  
  
-   `Divide` Żądania nie przepływu transakcji do usługi, ponieważ ponownie klienta użytkownika wygenerowana definicja `ICalculator` nie ma interfejsu `TransactionFlowAttribute`. Usługi ponownie są wykonywane działania w zakresie nowych i niepołączonych transakcja.  
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
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
  
 Rejestrowanie żądania operacji usług są wyświetlane w oknie konsoli tej usługi. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 Po pomyślnym wykonaniu kończy zakres transakcji klienta, i wszystkie akcje wykonane w tym zakresie są zatwierdzone. W szczególności dostrzeżone 5 rekordy są zachowywane w bazie danych usługi. Pierwsze 2 one miały miejsce w zakresie transakcji klienta.  
  
 Jeśli wystąpił wyjątek, dowolnym miejscu w ramach klienta `TransactionScope` , a następnie nie może ukończyć transakcji. To powoduje, że rekordy zarejestrowane w tym zakresie nie zostać zatwierdzony w bazie danych. W tym celu można zaobserwować, powtarzając przykładowe uruchomienia po zakomentowując na ukończenie zewnętrzny wywołania `TransactionScope`. Takie przebieg 3 ostatnich działań (od drugiego `Subtract`, `Multiply` i `Divide` żądań) są rejestrowane, ponieważ transakcja klienta nie przepływać do tych.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Aby skompilować wersji rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)  
  
2.  Upewnij się, że zainstalowano program SQL Server Express Edition lub SQL Server i czy parametry połączenia został prawidłowo ustawiony w pliku konfiguracyjnym aplikacji usługi. Aby uruchomić przykład, bez korzystania z bazy danych, należy ustawić `usingSql` wartości w pliku konfiguracji aplikacji usługi do `false`  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Dla konfiguracji między komputerami Włącz usługi Koordynator transakcji rozproszonych wykonując poniższe instrukcje, a narzędzie WsatConfig.exe z zestawu Windows SDK można włączyć obsługę sieci transakcji WCF. Zobacz [Konfigurowanie obsługi protokołu WS-Atomic Transaction](https://go.microsoft.com/fwlink/?LinkId=190370) informacji na temat konfigurowania WsatConfig.exe.  
  
 Czy na tym samym komputerze lub na różnych komputerach można uruchomić próbkę, należy skonfigurować transakcję Koordynator MSDTC (Microsoft Distributed) Włączanie przepływu transakcji sieci i użyć narzędzia WsatConfig.exe, aby włączyć obsługę sieci transakcji WCF.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a>Aby skonfigurować transakcję Koordynator MSDTC (Microsoft Distributed) do obsługi działa aplikacja przykładowa  
  
1.  Na komputerze usługi z systemem Windows Server 2003 lub Windows XP należy skonfigurować usługi MSDTC, aby zezwolić na przychodzące transakcje sieciowe, wykonując następujące instrukcje.  
  
    1.  Z **Start** menu, przejdź do **Panelu sterowania**, następnie **narzędzia administracyjne**, a następnie **usługi składowe**.  
  
    2.  Rozwiń **usługi składowe**. Otwórz **komputerów** folderu.  
  
    3.  Kliknij prawym przyciskiem myszy **Mój komputer** i wybierz **właściwości**.  
  
    4.  Na **MSDTC** kliknij pozycję **konfiguracji zabezpieczeń**.  
  
    5.  Sprawdź **DTC dostęp sieciowy** i **zezwolić na przychodzący**.  
  
    6.  Kliknij przycisk **OK**, następnie kliknij przycisk **tak** ponownego uruchomienia usługi MSDTC.  
  
    7.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
2.  Na komputerze usługi z systemem Windows Server 2008 lub Windows Vista należy skonfigurować usługi MSDTC, aby zezwolić na przychodzące transakcje sieciowe, wykonując następujące instrukcje.  
  
    1.  Z **Start** menu, przejdź do **Panelu sterowania**, następnie **narzędzia administracyjne**, a następnie **usługi składowe**.  
  
    2.  Rozwiń **usługi składowe**. Otwórz **komputerów** folderu. Wybierz **Koordynator transakcji rozproszonych**.  
  
    3.  Kliknij prawym przyciskiem myszy **koordynator DTC** i wybierz **właściwości**.  
  
    4.  Na **zabezpieczeń** karcie wyboru **dostępu do sieci usługi DTC** i **Zezwalaj na przychodzące**.  
  
    5.  Kliknij przycisk **OK**, następnie kliknij przycisk **tak** ponownego uruchomienia usługi MSDTC.  
  
    6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
3.  Na komputerze klienckim należy skonfigurować usługi MSDTC, aby zezwolić na wychodzące transakcje sieciowe:  
  
    1.  Z **Start** menu, przejdź do `Control Panel`, następnie **narzędzia administracyjne**, a następnie **usługi składowe**.  
  
    2.  Kliknij prawym przyciskiem myszy **Mój komputer** i wybierz **właściwości**.  
  
    3.  Na **MSDTC** kliknij pozycję **konfiguracji zabezpieczeń**.  
  
    4.  Sprawdź **DTC dostęp sieciowy** i **Zezwalaj na wychodzące**.  
  
    5.  Kliknij przycisk **OK**, następnie kliknij przycisk **tak** ponownego uruchomienia usługi MSDTC.  
  
    6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
