---
title: Współbieżność
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: eb6140895bb922bd159f1abf536a0d0b12d4f96c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183934"
---
# <a name="concurrency"></a>Współbieżność
Przykład współbieżności pokazuje przy <xref:System.ServiceModel.ServiceBehaviorAttribute> użyciu <xref:System.ServiceModel.ConcurrencyMode> z wyliczenia, który kontroluje, czy wystąpienie usługi przetwarza wiadomości sekwencyjnie lub jednocześnie. Próbka jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), `ICalculator` który implementuje umowy serwisowej. W tym przykładzie definiuje `ICalculatorConcurrency`nowy kontrakt, `ICalculator`który dziedziczy po , zapewniając dwie dodatkowe operacje do sprawdzania stanu współbieżności usługi. Zmieniając ustawienie współbieżności, można zaobserwować zmiany w zachowaniu, uruchamiając klienta.  
  
 W tym przykładzie klient jest aplikacją konsoli (.exe), a usługa jest obsługiwana przez internetowe usługi informacyjne (IIS).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Dostępne są trzy tryby współbieżności:  
  
- `Single`: Każde wystąpienie usługi przetwarza po jednym komunikacie naraz. Jest to domyślny tryb współbieżności.  
  
- `Multiple`: Każde wystąpienie usługi przetwarza wiele komunikatów jednocześnie. Implementacja usługi musi być bezpieczna dla wątków, aby używać tego trybu współbieżności.  
  
- `Reentrant`: Każde wystąpienie usługi przetwarza jedną wiadomość naraz, ale akceptuje wywołania wielokrotnego. Usługa akceptuje te wywołania tylko wtedy, gdy wywołuje. Reentrant jest wykazane w [concurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) próbki.  
  
 Użycie współbieżności jest związane z trybem instancing. W <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing współbieżność nie jest istotne, ponieważ każda wiadomość jest przetwarzana przez nowe wystąpienie usługi. W <xref:System.ServiceModel.InstanceContextMode.Single> instancing albo <xref:System.ServiceModel.ConcurrencyMode.Single> <xref:System.ServiceModel.ConcurrencyMode.Multiple> współbieżności jest istotne, w zależności od tego, czy pojedyncze wystąpienie przetwarza wiadomości sekwencyjnie lub jednocześnie. W <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, każdy z trybów współbieżności może być istotne.  
  
 Klasa usługi określa zachowanie współbieżności `[ServiceBehavior(ConcurrencyMode=<setting>)]` z atrybutem, jak pokazano w przykładzie kodu, który następuje. Zmieniając wiersze, które są komentowane, `Single` `Multiple` można eksperymentować z trybów współbieżności. Pamiętaj, aby odbudować usługę po zmianie trybu współbieżności.  
  
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
  
 W przykładzie <xref:System.ServiceModel.ConcurrencyMode.Multiple> używa współbieżności z <xref:System.ServiceModel.InstanceContextMode.Single> instancing domyślnie. Kod klienta został zmodyfikowany w celu użycia asynchronickiego serwera proxy. Dzięki temu klient może wykonywać wiele wywołań do usługi bez oczekiwania na odpowiedź między każdym wywołaniem. Można zaobserwować różnicę w zachowaniu trybu współbieżności usługi.  
  
 Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Tryb współbieżności, w obszarze usługi jest wyświetlany, każda operacja jest wywoływana, a następnie wyświetlana jest liczba operacji. Należy zauważyć, że gdy tryb `Multiple`współbieżności jest , wyniki są zwracane w innej kolejności niż jak zostały wywołane, ponieważ usługa przetwarza wiele komunikatów jednocześnie. Zmieniając tryb współbieżności na `Single`, wyniki są zwracane w kolejności, w jakiej zostały wywołane, ponieważ usługa przetwarza każdą wiadomość sekwencyjnie. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Jeśli używasz Svcutil.exe do generowania klienta serwera `/async` proxy, upewnij się, że należy dołączyć tę opcję.  
  
3. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
