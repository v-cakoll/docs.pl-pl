---
title: Współbieżność
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 393c8a79cb60a33203b41a0778176a4d78a9b6ee
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585314"
---
# <a name="concurrency"></a>Współbieżność
Przykład współbieżności ilustruje użycie <xref:System.ServiceModel.ServiceBehaviorAttribute> z <xref:System.ServiceModel.ConcurrencyMode> wyliczeniem, które określa, czy wystąpienie usługi przetwarza komunikaty sekwencyjnie czy współbieżnie. Przykład jest oparty na [wprowadzenie](getting-started-sample.md), który implementuje `ICalculator` kontrakt usługi. Ten przykład definiuje nowy kontrakt, `ICalculatorConcurrency` który dziedziczy z `ICalculator` , dostarczając dwie dodatkowe operacje do sprawdzania stanu współbieżności usługi. Zmieniając ustawienie współbieżności, można obserwować zmianę zachowania przez uruchomienie klienta.  
  
 W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Dostępne są trzy tryby współbieżności:  
  
- `Single`: Każde wystąpienie usługi przetwarza jeden komunikat w danym momencie. Jest to domyślny tryb współbieżności.  
  
- `Multiple`: Każde wystąpienie usługi przetwarza wiele komunikatów jednocześnie. Implementacja usługi musi być bezpieczna wątkowo, aby można było używać tego trybu współbieżności.  
  
- `Reentrant`: Każde wystąpienie usługi przetwarza jeden komunikat w danym momencie, ale akceptuje wywołania współużytkowane. Usługa akceptuje te wywołania tylko wtedy, gdy jest wywoływany. Reprezentacja jest przedstawiona w przykładzie [concurrency.](concurrencymode-reentrant.md) Retail.  
  
 Użycie współbieżności jest związane z trybem wystąpienia. W <xref:System.ServiceModel.InstanceContextMode.PerCall> przypadku tworzenia wystąpień współbieżność nie jest istotna, ponieważ każdy komunikat jest przetwarzany przez nowe wystąpienie usługi. W <xref:System.ServiceModel.InstanceContextMode.Single> przypadku wystąpienia, <xref:System.ServiceModel.ConcurrencyMode.Single> w <xref:System.ServiceModel.ConcurrencyMode.Multiple> zależności od tego, czy pojedyncze wystąpienie przetwarza komunikaty sekwencyjnie, czy współbieżnie. W <xref:System.ServiceModel.InstanceContextMode.PerSession> przypadku wystąpienia może być istotny dowolny z trybów współbieżności.  
  
 Klasa usługi określa zachowanie współbieżności z `[ServiceBehavior(ConcurrencyMode=<setting>)]` atrybutem, jak pokazano w poniższym przykładzie kodu. Poprzez zmianę wierszy, które są oznaczone jako komentarze, można eksperymentować `Single` z `Multiple` trybami współbieżności i. Pamiętaj, aby ponownie skompilować usługę po zmianie trybu współbieżności.  
  
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
  
 Przykład domyślnie używa <xref:System.ServiceModel.ConcurrencyMode.Multiple> współbieżności z wystąpieniami <xref:System.ServiceModel.InstanceContextMode.Single> . Kod klienta został zmodyfikowany w celu korzystania z asynchronicznego serwera proxy. Dzięki temu Klient może wykonywać wiele wywołań do usługi bez oczekiwania na odpowiedź między każdym wywołaniem. Można obserwować różnicę w działaniu trybu współbieżności usługi.  
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Zostanie wyświetlona opcja tryb współbieżności, w którym jest uruchomiona usługa, każda operacja jest wywoływana, a następnie wyświetlana jest liczba operacji. Należy zauważyć, że gdy tryb współbieżności to `Multiple` , wyniki są zwracane w innej kolejności niż w sposobie ich wywołania, ponieważ usługa przetwarza wiele komunikatów współbieżnie. Zmieniając tryb współbieżności na `Single` , wyniki są zwracane w kolejności, w jakiej zostały wywołane, ponieważ usługa przetwarza każdy komunikat sekwencyjnie. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Jeśli używasz programu Svcutil. exe do generowania klienta proxy, upewnij się, że dołączysz `/async` opcję.  
  
3. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
