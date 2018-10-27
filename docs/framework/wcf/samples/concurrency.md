---
title: Współbieżność
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: f8925157714621f8b97893bc25e41685778416f5
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50186008"
---
# <a name="concurrency"></a>Współbieżność
Przykład współbieżności, który demonstruje sposób użycia <xref:System.ServiceModel.ServiceBehaviorAttribute> z <xref:System.ServiceModel.ConcurrencyMode> wyliczenia, które kontrolują, czy wystąpienie usługi przetwarza komunikaty kolejno lub równolegle. Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi. Ta przykładowa aplikacja definiuje kontrakt nowe `ICalculatorConcurrency`, który dziedziczy z `ICalculator`, zapewniając dwóch dodatkowych operacji sprawdzania stanu współbieżności usługi. Zmieniając ustawienie współbieżności, można obserwować zmiany w zachowaniu przez uruchomienie klienta.  
  
 W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Dostępne są trzy tryby współbieżności:  
  
-   `Single`: Każde wystąpienie usługi przetwarza jeden komunikat w danym momencie. Jest to domyślny tryb współbieżności.  
  
-   `Multiple`: Każde wystąpienie usługi przetwarza wiele wiadomości jednocześnie. Implementacja usługi musi być wątków, aby użyć tego trybu współbieżności.  
  
-   `Reentrant`: Każde wystąpienie usługi przetwarza jeden komunikat w danym momencie, ale akceptuje wywołania współużytkowane. Usługa akceptuje tylko te wywołania kontaktujący. Wielobieżna ConcurrencyMode została przedstawiona w [pomocą właściwości ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) próbki.  
  
 Użycie współbieżności jest powiązana z trybu wystąpień. W <xref:System.ServiceModel.InstanceContextMode.PerCall> wystąpień, współbieżności nie jest ważna, ponieważ każdy komunikat jest przetwarzany przez nowe wystąpienie usługi. W <xref:System.ServiceModel.InstanceContextMode.Single> wystąpień, albo <xref:System.ServiceModel.ConcurrencyMode.Single> lub <xref:System.ServiceModel.ConcurrencyMode.Multiple> współbieżność jest istotne, w zależności od tego, czy pojedyncze wystąpienie przetwarza komunikaty kolejno lub równolegle. W <xref:System.ServiceModel.InstanceContextMode.PerSession> wystąpień, jednym z trybów współbieżności mogą być istotne.  
  
 Klasa usługi określa zachowanie współbieżności przy użyciu `[ServiceBehavior(ConcurrencyMode=<setting>)]` atrybutu, jak pokazano w poniższym przykładzie kodu. Zmieniając wierszy, które są oznaczone jako komentarz, możesz eksperymentować z `Single` i `Multiple` tryby współbieżności. Pamiętaj, aby odbudować usługi po zmianie trybu współbieżności.  
  
```csharp
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {     
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {     
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 W przykładzie użyto <xref:System.ServiceModel.ConcurrencyMode.Multiple> współbieżności przy użyciu <xref:System.ServiceModel.InstanceContextMode.Single> wystąpień domyślnie. Kod klienta została zmodyfikowana, aby używać asynchronicznych serwera proxy. Dzięki temu klientowi skierowanie wielu wywołań do usługi bez oczekiwania na odpowiedź między każdym wywołaniem. Możesz obserwować różnicy w zachowaniu trybu współbieżności usługi.  
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Tryb współbieżności, w którym działa usługa jest wyświetlana, nosi nazwę każdej operacji i następnie jest wyświetlana liczba operacji. Należy zauważyć, że przy włączonym trybie współbieżności `Multiple`, wyniki są zwracane w kolejności innej niż jak zostały wywołane, ponieważ usługa przetwarza wiele wiadomości jednocześnie. Zmieniając tryb współbieżności `Single`, wyniki są zwracane w kolejności ich wywołane, ponieważ usługa przetwarza każdy komunikat sekwencyjnie. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Korzystając z programu Svcutil.exe do generowania klienta serwera proxy, upewnij się, że zawrzesz `/async` opcji.  
  
3.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
  
## <a name="see-also"></a>Zobacz też
