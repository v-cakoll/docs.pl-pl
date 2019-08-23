---
title: Przepływ transakcji WS
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: e6fd84d9cc1f7df397e26e41c55f51d45406228d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942169"
---
# <a name="ws-transaction-flow"></a>Przepływ transakcji WS
Ten przykład ilustruje użycie transakcji skoordynowanej przez klienta oraz opcji klienta i serwera dla przepływu transakcji przy użyciu protokołu transakcji WS-lub OleTransactions. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługę kalkulatora, ale operacje są przypisywane w celu zademonstrowania użycia `TransactionFlowAttribute` z wyliczeniem **parametru TransactionFlowOption** w celu określenia stopnia przepływ transakcji jest włączony. W ramach przetworzonej transakcji dziennik żądanych operacji jest zapisywana w bazie danych i utrzymuje się do momentu ukończenia transakcji skoordynowanej klienta — Jeśli transakcja klienta nie zostanie ukończona, transakcja usługi sieci Web gwarantuje, że odpowiednie aktualizacje bazy danych nie są zatwierdzone.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Po zainicjowaniu połączenia z usługą i transakcją klient uzyskuje dostęp do kilku operacji usługi. Umowa dla usługi jest definiowana w następujący sposób z każdą operacją, która wykazuje inne ustawienia dla `TransactionFlowOption`.  

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

 Definiuje operacje w kolejności, w jakiej mają być przetwarzane:  
  
- Żądanie `Add` operacji musi zawierać transakcję przepływaną.  
  
- Żądanie `Subtract` operacji może obejmować przechodzącą transakcję.  
  
- Żądanie `Multiply` operacji nie może zawierać przepływającej transakcji za pomocą jawnego ustawienia nołojud.  
  
- Żądanie operacji nie może zawierać przepływającej transakcji przez pominięcie `TransactionFlow` atrybutu. `Divide`  
  
 Aby włączyć przepływ transakcji, oprócz odpowiednich atrybutów [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) operacji należy użyć powiązań z włączoną właściwością TransactionFlow >. W tym przykładzie konfiguracja usługi uwidacznia punkt końcowy protokołu TCP i punkt końcowy HTTP oprócz punktu końcowego wymiany metadanych. Punkt końcowy TCP i punkt końcowy HTTP używają następujących powiązań, z których oba mają [ \<włączoną właściwość TransactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) .  
  
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
> NetTcpBinding udostępnione przez system umożliwia specyfikację element TransactionProtocol, podczas gdy w przypadku systemu wsHttpBinding jest wykorzystywany tylko bardziej międzyoperacyjny protokół WSAtomicTransactionOctober2004. Protokół OleTransactions jest dostępny tylko dla klientów Windows Communication Foundation (WCF).  
  
 Dla klasy implementującej `ICalculator` interfejs wszystkie metody są przypisane <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> do właściwości ustawionej na `true`. To ustawienie deklaruje, że wszystkie akcje podjęte w ramach metody są wykonywane w zakresie transakcji. W takim przypadku wykonane działania obejmują rejestrowanie do bazy danych dziennika. Jeśli żądanie operacji obejmuje przetworzoną transakcję, akcje są wykonywane w ramach zakresu transakcji przychodzącej lub automatycznie generowane są nowe zakresy transakcji.  
  
> [!NOTE]
> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> Właściwość definiuje zachowanie lokalne dla implementacji metod usługi i nie definiuje możliwości lub wymagania dotyczącego przepływania transakcji przez klienta.  

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

 W przypadku klienta `TransactionFlowOption` ustawienia usługi dla operacji są odzwierciedlone w wygenerowanej definicji `ICalculator` interfejsu klienta. Ponadto ustawienia `transactionFlow` właściwości usługi są odzwierciedlone w konfiguracji aplikacji klienta. Klient może wybrać transport i protokół, wybierając odpowiednie `endpointConfigurationName`.  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> Obserwowane zachowanie tego przykładu jest takie samo, niezależnie od tego, który protokół lub transport jest wybierany.  
  
 Po zainicjowaniu połączenia z usługą Klient tworzy nowy `TransactionScope` wokół wywołań operacji usługi.  

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
  
- `Add` Żądanie przeprowadzi transakcję wymaganą przez usługę, a akcje usługi są wykonywane w zakresie transakcji klienta.  
  
- Pierwsze `Subtract` żądanie również przepływie dozwolonej transakcji do usługi, a następnie akcje usługi są wykonywane w zakresie transakcji klienta.  
  
- Drugie `Subtract` żądanie jest wykonywane w ramach nowego zakresu transakcji zadeklarowanego `TransactionScopeOption.Suppress` za pomocą opcji. Pomija to początkową transakcję klienta i żądanie nie powoduje przepływania transakcji do usługi. Takie podejście pozwala klientowi jawnie zrezygnować z usługi i chronić ją przed przepływaniem transakcji w usłudze, gdy nie jest to wymagane. Akcje usługi są wykonywane w zakresie nowej i niepołączonej transakcji.  
  
- <xref:System.ServiceModel.TransactionFlowAttribute> `ICalculator` `NotAllowed` <xref:System.ServiceModel.TransactionFlowOption>Żądanie nie przepływ transakcji do usługi, ponieważ wygenerowana definicja interfejsu klienta zawiera zestaw do. `Multiply`  
  
- Żądanie nie przepływ transakcji do usługi, ponieważ wywygenerowana definicja `ICalculator` `TransactionFlowAttribute`interfejsu klienta nie zawiera. `Divide` Akcje usługi są ponownie wykonywane w zakresie innej nowej i niepołączonej transakcji.  
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
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
  
 Rejestrowanie żądań operacji usługi jest wyświetlane w oknie konsoli usługi. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 Po pomyślnym wykonaniu zakres transakcji klienta zostaje zakończony i wszystkie akcje podjęte w ramach tego zakresu zostaną zatwierdzone. W odróżnieniu od 5 rekordów w bazie danych usługi są utrwalane. Pierwsze 2 z nich wystąpiło w zakresie transakcji klienta.  
  
 Jeśli wystąpi wyjątek w dowolnym miejscu w ramach klienta `TransactionScope` , nie można ukończyć transakcji. Powoduje to, że rekordy zarejestrowane w tym zakresie nie są zatwierdzone do bazy danych. Ten efekt można zaobserwować przez powtórzenie przykładowego przebiegu po komentowaniu wywołania w celu ukończenia zewnętrznego `TransactionScope`. W takim przebiegu są rejestrowane tylko ostatnie 3 akcje (od drugiej `Subtract` `Multiply` , a i `Divide` żądania), ponieważ transakcja klienta nie przepływa do tych.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Aby skompilować wersję C# rozwiązania lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)  
  
2. Upewnij się, że masz zainstalowaną wersję SQL Server Express lub SQL Server i że parametry połączenia zostały prawidłowo ustawione w pliku konfiguracyjnym aplikacji usługi. Aby uruchomić przykład bez korzystania z bazy danych, ustaw `usingSql` wartość w pliku konfiguracyjnym aplikacji usługi na`false`  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  W przypadku konfiguracji między maszynami Włącz Distributed Transaction Coordinator przy użyciu poniższych instrukcji i użyj narzędzia WsatConfig. exe z Windows SDK, aby włączyć obsługę transakcji WCF w sieci. Zobacz [Konfigurowanie obsługi transakcji WS-AT](https://go.microsoft.com/fwlink/?LinkId=190370) , aby uzyskać informacje na temat konfigurowania programu wsatConfig. exe.  
  
 Bez względu na to, czy uruchamiasz przykład na tym samym komputerze, czy na różnych komputerach, należy skonfigurować usługę Microsoft Distributed Transaction Coordinator (MSDTC) w celu włączenia przepływu transakcji sieci i użyć narzędzia WsatConfig. exe, aby włączyć obsługę sieci transakcji WCF.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a>Aby skonfigurować Distributed Transaction Coordinator firmy Microsoft (MSDTC) do obsługi uruchamiania przykładu  
  
1. Na maszynie usługi z systemem Windows Server 2003 lub Windows XP Skonfiguruj usługę MSDTC tak, aby zezwalała na przychodzące transakcje sieciowe, wykonując te instrukcje.  
  
    1. W menu **Start** przejdź do **Panelu sterowania**, a następnie **Narzędzia administracyjne**, a następnie **usługi składowe**.  
  
    2. Rozwiń węzeł **usługi składowe**. Otwórz folder **komputery** .  
  
    3. Kliknij prawym przyciskiem myszy pozycję **mój komputer** , a następnie wybierz pozycję **Właściwości**.  
  
    4. Na karcie **MSDTC** kliknij pozycję **Konfiguracja zabezpieczeń**.  
  
    5. Sprawdź **dostęp do usługi Network DTC** i **Zezwalaj na ruch**przychodzący.  
  
    6. Kliknij przycisk **OK**, a następnie kliknij przycisk **tak** , aby ponownie uruchomić usługę MSDTC.  
  
    7. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
2. Na maszynie usługi z systemem Windows Server 2008 lub Windows Vista Skonfiguruj usługę MSDTC tak, aby zezwalała na przychodzące transakcje sieciowe, wykonując te instrukcje.  
  
    1. W menu **Start** przejdź do **Panelu sterowania**, a następnie **Narzędzia administracyjne**, a następnie **usługi składowe**.  
  
    2. Rozwiń węzeł **usługi składowe**. Otwórz folder **komputery** . Wybierz **Distributed Transaction Coordinator**.  
  
    3. Kliknij prawym przyciskiem myszy pozycję **koordynator usługi DTC** i wybierz pozycję **Właściwości**.  
  
    4. Na karcie **zabezpieczenia** Sprawdź **dostęp do usługi Network DTC** i **Zezwalaj na ruch**przychodzący.  
  
    5. Kliknij przycisk **OK**, a następnie kliknij przycisk **tak** , aby ponownie uruchomić usługę MSDTC.  
  
    6. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
3. Na komputerze klienckim Skonfiguruj usługę MSDTC tak, aby zezwalała na wychodzące transakcje sieciowe:  
  
    1. W menu **Start** przejdź do `Control Panel`, a następnie **Narzędzia administracyjne**, a następnie **usługi składowe**.  
  
    2. Kliknij prawym przyciskiem myszy pozycję **mój komputer** , a następnie wybierz pozycję **Właściwości**.  
  
    3. Na karcie **MSDTC** kliknij pozycję **Konfiguracja zabezpieczeń**.  
  
    4. Sprawdź **dostęp do usługi Network DTC** i **Zezwalaj na**ruch wychodzący.  
  
    5. Kliknij przycisk **OK**, a następnie kliknij przycisk **tak** , aby ponownie uruchomić usługę MSDTC.  
  
    6. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
> [!IMPORTANT]
>  Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
