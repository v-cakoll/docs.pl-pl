---
title: Tworzenie wystąpienia
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: 1e755a28ff4ce6450db4189783fa688002ebe8eb
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045557"
---
# <a name="instancing"></a>Tworzenie wystąpienia
Przykładowa funkcja tworzenia wystąpień pokazuje ustawienie zachowania tworzenia wystąpienia, które określa sposób, w jaki wystąpienie klasy usługi jest tworzone w odpowiedzi na żądania klientów. Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontrakt usługi. Ten przykład definiuje nowy kontrakt `ICalculatorInstance`, który dziedziczy z. `ICalculator` Kontrakt określony przez `ICalculatorInstance` zawiera trzy dodatkowe operacje umożliwiające sprawdzenie stanu wystąpienia usługi. Zmieniając ustawienie tworzenia wystąpienia, można obserwować zmianę zachowania przez uruchomienie klienta.  
  
 W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Dostępne są następujące tryby wystąpienia:  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: Nowe wystąpienie usługi jest tworzone dla każdego żądania klienta.  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: Nowe wystąpienie jest tworzone dla każdej nowej sesji klienta i utrzymywane przez okres istnienia tej sesji (wymaga powiązania, które obsługuje sesję).  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: Pojedyncze wystąpienie klasy usługi obsługuje wszystkie żądania klientów w okresie istnienia aplikacji.  
  
 Klasa usługi określa zachowanie podczas wystąpienia z `[ServiceBehavior(InstanceContextMode=<setting>)]` atrybutem, jak pokazano w poniższym przykładzie kodu. Zmieniając wiersze, które są oznaczone jako komentarze, można obserwować zachowanie każdego z trybów wystąpienia. Pamiętaj, aby ponownie skompilować usługę po zmianie trybu tworzenia wystąpienia. Brak ustawień związanych z tworzeniem wystąpień do określenia na kliencie.  
  
```csharp
// Enable one of the following instance modes to compare instancing behaviors.  
 [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
  
// PerCall creates a new instance for each operation.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]  
  
// Singleton creates a single instance for application lifetime.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class CalculatorService : ICalculatorInstance  
{  
    static Object syncObject = new object();  
    static int instanceCount;  
    int instanceId;  
    int operationCount;  
  
    public CalculatorService()  
    {  
        lock (syncObject)  
        {  
            instanceCount++;  
            instanceId = instanceCount;  
        }  
    }  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 / n2;  
    }  
  
    public string GetInstanceContextMode()  
    {   // Return the InstanceContextMode of the service  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.InstanceContextMode.ToString();  
    }  
  
    public int GetInstanceId()  
    {   // Return the id for this instance  
        return instanceId;  
    }  
  
    public int GetOperationCount()  
    {   // Return the number of ICalculator operations performed   
        // on this instance  
        lock (syncObject)  
        {  
            return operationCount;  
        }  
    }  
}  
  
static void Main()  
{  
    // Create a client.  
    CalculatorInstanceClient client = new CalculatorInstanceClient();  
    string instanceMode = client.GetInstanceContextMode();  
    Console.WriteLine("InstanceContextMode: {0}", instanceMode);  
    DoCalculations(client);  
  
    // Create a second client.  
    CalculatorInstanceClient client2 = new CalculatorInstanceClient();  
  
    DoCalculations(client2);  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Zostanie wyświetlona opcja tryb wystąpienia, w którym działa usługa. Po każdej operacji zostanie wyświetlony komunikat o IDENTYFIKATORze i liczbie operacji odzwierciedlający zachowanie trybu Tworzenie wystąpienia. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
