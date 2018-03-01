---
title: "Zachowanie transakcji usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a4c7c9c78b821f7457f193d24bae031d49b301ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="service-transaction-behavior"></a>Zachowanie transakcji usługi
W przykładzie pokazano użycie transakcji koordynowane przez klienta i ustawienia atrybutu ServiceBehaviorAttribute i OperationBehaviorAttribute można kontrolować zachowanie transakcji usługi. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementuje usługi Kalkulator, ale jest rozszerzony do obsługi serwera dziennik działań wykonywanych w tabeli bazy danych i stanowego Suma operacji Kalkulator bieżąca. Utrwalonych zapisuje dane w tabeli dziennika serwera są zależne od wyniku transakcji klienta koordynowane — Jeśli transakcja klienta nie zostanie ukończone, transakcja usługi sieci Web zapewnia aktualizacji do bazy danych nie są przekazywane.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Kontrakt usługi określa, że wszystkie operacje wymaga przepływu z żądaniami transakcji:  
  
```  
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
  
 Aby umożliwić ruch przychodzący transakcji, usługa jest skonfigurowana z wsHttpBinding dostarczane przez system z atrybutem transactionFlow ustawioną `true`. Współdziałanie protokołu WSAtomicTransactionOctober2004 używa tego powiązania:  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="transactionalBinding" transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
 Po zainicjowaniu zarówno połączenia usługi i transakcji, klient uzyskuje dostęp do wielu operacji usługi w zakresie transakcji wykonuje transakcję i zamyka połączenie:  
  
```  
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
  
 W usłudze istnieją trzy atrybuty, które mają wpływ na zachowanie transakcji usługi, a w tym celu w następujący sposób:  
  
-   Na `ServiceBehaviorAttribute`:  
  
    -   `TransactionTimeout` Właściwość określa okres czasu, w ramach którego transakcja musi zostać zakończona. W tym przykładzie jest ustawiona na 30 sekund.  
  
    -   `TransactionIsolationLevel` Właściwość określa poziom izolacji, który obsługuje usługę. Jest to wymagane, aby dopasować poziom izolacji klienta.  
  
    -   `ReleaseServiceInstanceOnTransactionComplete` Właściwość określa, czy wystąpienie usługi jest ponownie przetwarzany po zakończeniu transakcji. Przez ustawienie jej na `false`, usługa utrzymuje tego samego wystąpienia usługi między żądania operacji. Jest to wymagane, aby kontynuować obliczanie całkowitej. Jeśli ustawiono `true`, nowe wystąpienie jest generowany po zakończeniu każdej akcji.  
  
    -   `TransactionAutoCompleteOnSessionClose` Właściwość określa, czy transakcje oczekujące są wykonywane po zamknięciu sesji. Przez ustawienie jej na `false`, poszczególnych operacji są wymagane do obu zestawów `OperationBehaviorAttribute``TransactionAutoComplete` właściwości `true` lub aby jawnie wymaga wywołania `SetTransactionComplete` sposób realizacji transakcji. W tym przykładzie przedstawiono obu podejść.  
  
-   Na `ServiceContractAttribute`:  
  
    -   `SessionMode` Właściwość określa, czy usługi są powiązane z odpowiednich żądań do logicznego sesji. Ponieważ ta usługa obejmuje operacje, których właściwość OperationBehaviorAttribute Wartość TransactionAutoComplete jest wartość `false` (mnożenia i dzielenia) `SessionMode.Required` musi być określona. Na przykład wielokrotnie operacja nie zostanie zakończone transakcję i zamiast tego, opiera się na nowsze wywołanie do dzielenia wykonania za pomocą `SetTransactionComplete` metody; usługi musi być możliwe ustalenie, czy te operacje są wykonywane w ramach tej samej sesji.  
  
-   Na `OperationBehaviorAttribute`:  
  
    -   `TransactionScopeRequired` Właściwość określa, czy mają zostać wykonane akcje wykonać operację w zakresie transakcji. Ta wartość jest równa `true` dla wszystkich operacji w tym przykładowe i, ponieważ klient przepływy transakcji do wszystkich operacji, wykonywane akcje w zakresie transakcji klienta.  
  
    -   `TransactionAutoComplete` Właściwość określa, czy transakcja, w której wykonuje metodę jest wprowadzana automatycznie, jeśli wystąpi żaden nieobsługiwany wyjątek. Jak opisano wcześniej, to ma ustawioną wartość `true` operacji Dodawanie i odejmowanie, ale `false` Multiply i operacji dzielenia. Dodawanie i odejmowanie operacji wykonania swoich akcji automatycznie, dzielenia zakończeniem za pomocą jawnego wywołania do `SetTransactionComplete` — metoda i Multiply nie zakończy działania, ale zamiast tego opiera się i wymaga nowszej wywołanie, takich jak Dzielenie, aby wykonać akcje.  
  
 Implementacja usługi oparte na atrybutach wygląda następująco:  
  
```  
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
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
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
  
 Rejestrowanie żądań operacji usługi są wyświetlane w oknie konsoli usługi. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Press <ENTER> to terminate service.  
Creating new service instance...  
  Writing row 1 to database: Adding 100 to 0  
  Writing row 2 to database: Subtracting 45 from 100  
  Writing row 3 to database: Multiplying 55 by 9  
  Writing row 4 to database: Dividing 495 by 15  
```  
  
 Należy pamiętać, że oprócz zachowaniu całkowitej działanie obliczeń, usługa raporty tworzenia wystąpień (jedno wystąpienie dla tego przykładu) i rejestruje żądania operacji do bazy danych. Ponieważ wszystkie żądania przepływu transakcji klienta, jakiekolwiek niepowodzenie do ukończenia tej transakcji powoduje wszystkie operacje bazy danych Trwa wycofywanie. Mogą to być przedstawiane na kilka różnych sposobów:  
  
-   Komentarz wywołania klienta `tx.Complete`() i uruchom ponownie — spowoduje to klienta Kończenie zakresu transakcji bez ukończenia transakcji.  
  
-   Komentarz dotyczący out wywołania operacji usługi dzielenia — powoduje to zapobiec zainicjowane przez akcję mnożenia ukończenie operacji i w związku z tym transakcji klienta ostatecznie również nie powiedzie się.  
  
-   Throw Wystąpił nieobsługiwany wyjątek w dowolnym miejscu w zakresie transakcji klienta — podobnie zapobiega to klient wykonanie jego transakcji.  
  
 Wynikiem tych jest żadna z operacji wykonywanych w tym zakresie nie jest zatwierdzona, a liczba wierszy utrwalone w bazie danych zwiększa się.  
  
> [!NOTE]
>  W ramach procesu tworzenia pliku bazy danych jest kopiowany do folderu bin. Należy przyjrzeć się tej kopii pliku bazy danych do przestrzegania tych wierszy, które są zachowywane w dzienniku, a nie w pliku, który jest dołączony do projektu programu Visual Studio.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że zainstalowano program SQL Server 2005 Express Edition lub SQL Server 2005. W pliku App.config usługi bazy danych `connectionString` może być zestawu lub baza danych interakcje mogą być wyłączone przez ustawienia appSettings `usingSql` do wartości `false`.  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Po uruchomieniu próbki na komputerach, należy skonfigurować MSDTC Microsoft Distributed Transaction Coordinator () do włączenia przepływu transakcji sieci i włączyć za pomocą narzędzia WsatConfig.exe [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transakcji sieci pomocy technicznej.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a>Aby skonfigurować MSDTC Microsoft Distributed Transaction Coordinator () do obsługi systemem próbki na komputerach  
  
1.  Na komputerze usługi należy skonfigurować usługi MSDTC, aby umożliwić przychodzących transakcji sieci.  
  
    1.  Z **Start** menu, przejdź do **Panelu sterowania**, następnie **narzędzia administracyjne**, a następnie **usługi składowe**.  
  
    2.  Kliknij prawym przyciskiem myszy **Mój komputer** i wybierz **właściwości**.  
  
    3.  Na **MSDTC** , kliknij pozycję **konfiguracji zabezpieczeń**.  
  
    4.  Sprawdź **sieci dostęp do usługi DTC** i **Zezwalaj na przychodzące**.  
  
    5.  Kliknij przycisk **tak** Uruchom ponownie usługę MS DTC, a następnie kliknij przycisk **OK**.  
  
    6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
2.  Na komputerze usługi i na komputerze klienta należy skonfigurować zapory systemu Windows, aby uwzględnić MSDTC Microsoft Distributed Transaction Coordinator () do listy aplikacji wyjątku:  
  
    1.  Uruchom aplikację Zapora systemu Windows w Panelu sterowania.  
  
    2.  Z **wyjątki** , kliknij pozycję **Dodaj Program**.  
  
    3.  Przejdź do folderu C:\WINDOWS\System32.  
  
    4.  Wybierz Msdtc.exe i kliknij przycisk **Otwórz**.  
  
    5.  Kliknij przycisk **OK** zamknąć **Dodaj Program** okno dialogowe, a następnie kliknij przycisk **OK** ponownie, aby zamknąć aplet Zapora systemu Windows.  
  
3.  Na komputerze klienckim należy skonfigurować usługi MSDTC, aby umożliwić wychodzących transakcji sieci:  
  
    1.  Z **Start** menu, przejdź do **Panelu sterowania**, następnie **narzędzia administracyjne**, a następnie **usługi składowe**.  
  
    2.  Kliknij prawym przyciskiem myszy **Mój komputer** i wybierz **właściwości**.  
  
    3.  Na **MSDTC** , kliknij pozycję **konfiguracji zabezpieczeń**.  
  
    4.  Sprawdź **sieci dostęp do usługi DTC** i **Zezwalaj na wychodzące**.  
  
    5.  Kliknij przycisk **tak** Uruchom ponownie usługę MS DTC, a następnie kliknij przycisk **OK**.  
  
    6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`  
  
## <a name="see-also"></a>Zobacz też
