---
title: Przepływ transakcji WS
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 8b037a2faa6ed5f7c77ea9347b92af7dc1ec2c27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183169"
---
# <a name="ws-transaction-flow"></a>Przepływ transakcji WS
W tym przykładzie pokazano użycie transakcji koordynowanej przez klienta oraz opcji klienta i serwera dla przepływu transakcji przy użyciu protokołu WS-Atomic Transaction lub OleTransactions. Ten przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje usługę kalkulatora, ale `TransactionFlowAttribute` operacje są przypisywane do wykazania użycia z **TransactionFlowOption** wyliczenia, aby określić, w jakim stopniu przepływ transakcji jest włączony. W zakresie transakcji przepływanej dziennik żądanych operacji jest zapisywany w bazie danych i utrzymuje się do momentu zakończenia transakcji koordynowanej przez klienta — jeśli transakcja klienta nie zostanie ukończona, transakcja usługi sieci Web zapewnia, że odpowiednie aktualizacje bazy danych nie są zatwierdzane.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Po zainicjowaniu połączenia z usługą i transakcji klient uzyskuje dostęp do kilku operacji usługi. Umowa o usługę jest zdefiniowana w następujący sposób z każdą `TransactionFlowOption`operacją wykazując inną konfigurację dla .  

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

 Definiuje to operacje w kolejności, w jakiej mają być przetwarzane:  
  
- Żądanie `Add` operacji musi zawierać przepłynęła transakcja.  
  
- Żądanie `Subtract` operacji może zawierać przepłynęła transakcja.  
  
- Żądanie `Multiply` operacji nie może zawierać prze przepływanych transakcji za pośrednictwem jawnego ustawienia Nieuprawione.  
  
- Żądanie `Divide` operacji nie może zawierać przepłynęła transakcja przez `TransactionFlow` pominięcie atrybutu.  
  
 Aby włączyć przepływ transakcji, powiązania z [ \<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) właściwość włączona musi być używana oprócz odpowiednich atrybutów operacji. W tym przykładzie konfiguracja usługi udostępnia punkt końcowy TCP i punkt końcowy HTTP oprócz punktu końcowego programu Metadata Exchange. Punkt końcowy TCP i punkt końcowy HTTP używają następujących powiązań, z których oba mają [ \<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) właściwość włączoną.  
  
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
> NetTcpBinding dostarczony przez system umożliwia specyfikację transactionProtocol, podczas gdy system dostarczony wsHttpBinding używa tylko bardziej interoperacyjnego protokołu WSAtomicTransactionOctober2004. Protokół OleTransactions jest dostępny tylko dla klientów Programu Windows Communication Foundation (WCF).  
  
 Dla klasy, która `ICalculator` implementuje interfejs, wszystkie metody <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> są `true`przypisywane z właściwością ustawioną na . To ustawienie deklaruje, że wszystkie akcje podjęte w ramach metody występują w zakresie transakcji. W takim przypadku podjęte akcje obejmują nagrywanie do bazy danych dziennika. Jeśli żądanie operacji zawiera przepłynęła transakcja, akcje występują w zakresie transakcji przychodzącej lub nowy zakres transakcji jest generowany automatycznie.  
  
> [!NOTE]
> Właściwość <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> definiuje zachowanie lokalne do implementacji metody usługi i nie definiuje zdolność klienta do lub wymagania dotyczące przepływu transakcji.  

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

 Na kliencie `TransactionFlowOption` ustawienia usługi w operacjach są odzwierciedlane w wygenerowanej `ICalculator` definicji interfejsu przez klienta. Ponadto ustawienia `transactionFlow` właściwości usługi są odzwierciedlane w konfiguracji aplikacji klienta. Klient może wybrać transport i protokół, `endpointConfigurationName`wybierając odpowiedni plik .  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> Obserwowane zachowanie tej próbki jest takie samo, bez względu na to, który protokół lub transport jest wybrany.  
  
 Po zainicjowaniu połączenia z usługą klient `TransactionScope` tworzy nowy wokół wywołań do operacji usługi.  

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
  
- Żądanie `Add` przepływa wymaganą transakcję do usługi, a akcje usługi występują w zakresie transakcji klienta.  
  
- Pierwsze `Subtract` żądanie również przepływa dozwoloną transakcję do usługi i ponownie akcje usługi występują w zakresie transakcji klienta.  
  
- Drugie `Subtract` żądanie jest wykonywane w ramach nowego `TransactionScopeOption.Suppress` zakresu transakcji zadeklarowanego z opcją. Pomija to początkową transakcję zewnętrzną klienta, a żądanie nie przepływa transakcji do usługi. Takie podejście umożliwia klientowi jawnie zrezygnować i chronić przed przepływem transakcji do usługi, gdy nie jest to wymagane. Akcje usługi występują w zakresie nowej i niepołączona transakcja.  
  
- Żądanie `Multiply` nie przepływa transakcji do usługi, ponieważ wygenerowana `ICalculator` przez klienta <xref:System.ServiceModel.TransactionFlowAttribute> definicja interfejsu zawiera zestaw do <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`.  
  
- Żądanie `Divide` nie przepływa transakcji do usługi, ponieważ ponownie wygenerowana `ICalculator` definicja interfejsu `TransactionFlowAttribute`klienta nie zawiera pliku . Akcje usługi ponownie występują w ramach innej nowej i niepołączona transakcja.  
  
 Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```console  
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
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 Po pomyślnym wykonaniu zakres transakcji klienta kończy się i wszystkie akcje podjęte w tym zakresie są zatwierdzane. W szczególności zauważyć 5 rekordy są zachowywane w bazie danych usługi. Pierwsze 2 z nich miały miejsce w ramach transakcji klienta.  
  
 Jeśli wystąpił wyjątek w dowolnym `TransactionScope` miejscu w obrębie klienta, transakcja nie może zakończyć. Powoduje to, że rekordy rejestrowane w tym zakresie nie są zobowiązane do bazy danych. Efekt ten można zaobserwować, powtarzając przebieg próbki po skomentowaniu `TransactionScope`wywołania w celu ukończenia zewnętrznego . W takim uruchomieniu tylko ostatnie 3 akcje `Subtract`(od `Multiply` drugiego `Divide` , i żądania) są rejestrowane, ponieważ transakcja klienta nie przepływa do nich.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Aby utworzyć wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w [tworzeniu przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)  
  
2. Upewnij się, że zainstalowano program SQL Server Express Edition lub SQL Server oraz że parametry połączenia zostały poprawnie ustawione w pliku konfiguracyjnym aplikacji usługi. Aby uruchomić próbkę bez użycia `usingSql` bazy danych, ustaw wartość w pliku konfiguracyjnym aplikacji usługi na`false`  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > W przypadku konfiguracji między komputerami włącz koordynatora transakcji rozproszonych przy użyciu poniższych instrukcji i użyj narzędzia WsatConfig.exe z zestawu Windows SDK, aby włączyć obsługę sieciową Transakcje WCF. Aby uzyskać informacje dotyczące konfigurowania programu WsatConfig.exe, zobacz [Konfigurowanie obsługi transakcji WS-Atomic](../feature-details/configuring-ws-atomic-transaction-support.md).  
  
 Niezależnie od tego, czy próbka jest uruchamiana na tym samym komputerze, czy na różnych komputerach, należy skonfigurować koordynatora transakcji rozproszonych firmy Microsoft (MSDTC), aby włączyć przepływ transakcji sieciowych i użyć narzędzia WsatConfig.exe, aby włączyć obsługę sieciową transakcji WCF.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a>Aby skonfigurować koordynatora transakcji rozproszonych firmy Microsoft (MSDTC) do obsługi uruchamiania przykładu  
  
1. Na komputerze serwisowym z systemem Windows Server 2003 lub Windows XP skonfiguruj usługę MSDTC, aby zezwalała na przychodzące transakcje sieciowe, postępując zgodnie z tymi instrukcjami.  
  
    1. Z menu **Start** przejdź do **Panelu sterowania**, następnie do pozycji **Narzędzia administracyjne**, a następnie **usługi składowe**.  
  
    2. Rozwiń **węzeł Usługi składowe**. Otwórz folder **Komputery.**  
  
    3. Kliknij prawym przyciskiem myszy **pozycję Mój komputer** i wybierz polecenie **Właściwości**.  
  
    4. Na karcie **MSDTC** kliknij pozycję **Konfiguracja zabezpieczeń**.  
  
    5. Sprawdź **dostęp do usługi DTC sieci** i **zezwalaj na przychodzących**.  
  
    6. Kliknij **przycisk OK**, a następnie kliknij przycisk **Tak,** aby ponownie uruchomić usługę MSDTC.  
  
    7. Kliknij przycisk **OK**, aby zamknąć okno dialogowe.  
  
2. Na komputerze serwisowym z systemem Windows Server 2008 lub Windows Vista należy skonfigurować usługę MSDTC, aby zezwalała na przychodzące transakcje sieciowe, postępując zgodnie z tymi instrukcjami.  
  
    1. Z menu **Start** przejdź do **Panelu sterowania**, następnie do pozycji **Narzędzia administracyjne**, a następnie **usługi składowe**.  
  
    2. Rozwiń **węzeł Usługi składowe**. Otwórz folder **Komputery.** Wybierz **koordynatora transakcji rozproszonych**.  
  
    3. Kliknij prawym przyciskiem myszy **pozycję Koordynator dtc** i wybierz polecenie **Właściwości**.  
  
    4. Na karcie **Zabezpieczenia** zaznacz pozycję **Dostęp do usługi DTC sieci** i **zezwalaj na przychodzących**.  
  
    5. Kliknij **przycisk OK**, a następnie kliknij przycisk **Tak,** aby ponownie uruchomić usługę MSDTC.  
  
    6. Kliknij przycisk **OK**, aby zamknąć okno dialogowe.  
  
3. Na komputerze klienckim skonfiguruj usługa MSDTC, aby zezwalała na wychodzące transakcje sieciowe:  
  
    1. W menu **Start** przejdź `Control Panel`do pozycji , następnie do **pozycji Narzędzia administracyjne**, a następnie do usługi **składowe**.  
  
    2. Kliknij prawym przyciskiem myszy **pozycję Mój komputer** i wybierz polecenie **Właściwości**.  
  
    3. Na karcie **MSDTC** kliknij pozycję **Konfiguracja zabezpieczeń**.  
  
    4. Sprawdź **dostęp do usługi DTC sieci** i **zezwalaj na ruch wychodzący**.  
  
    5. Kliknij **przycisk OK**, a następnie kliknij przycisk **Tak,** aby ponownie uruchomić usługę MSDTC.  
  
    6. Kliknij przycisk **OK**, aby zamknąć okno dialogowe.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
