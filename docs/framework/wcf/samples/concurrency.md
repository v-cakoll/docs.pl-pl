---
title: "Współbieżność"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c63882055718bd54d1983ea0aa10d208bd70793f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="concurrency"></a>Współbieżność
Przykład współbieżności demonstruje użycie <xref:System.ServiceModel.ServiceBehaviorAttribute> z <xref:System.ServiceModel.ConcurrencyMode> wyliczenia, która kontroluje, czy wystąpienie usługi przetwarza wiadomości sekwencyjnie lub jednocześnie. Próbki jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi. W tym przykładzie definiuje kontrakt nowe `ICalculatorConcurrency`, który dziedziczy z `ICalculator`, zapewniając dwa dodatkowe operacje dla sprawdzenie stanu usługi współbieżności. Zmieniając ustawienie współbieżności, można obserwować zmiany w zachowaniu przez uruchomienie klienta.  
  
 W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Dostępne są trzy tryby współbieżności:  
  
-   `Single`: Każde wystąpienie usługi przetwarza jeden komunikat naraz. Jest to domyślny tryb współbieżności.  
  
-   `Multiple`: Każde wystąpienie usługi jednocześnie przetwarza wiele komunikatów. Implementacja usługi musi być wielowątkowość ten tryb współbieżności.  
  
-   `Reentrant`: Każde wystąpienie usługi przetwarza jeden komunikat w czasie, ale akceptuje wywołania współużytkowane. Usługa akceptuje tylko tych wywołań, wywołując. Procedura wielobieżna jest przedstawiona w [pomocą właściwości ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) próbki.  
  
 Użycie współbieżności jest powiązany z trybu tworzenia. W <xref:System.ServiceModel.InstanceContextMode.PerCall> wystąpień, współbieżności nie jest ważna, ponieważ każdy komunikat jest przetwarzany przez nowego wystąpienia usługi. W <xref:System.ServiceModel.InstanceContextMode.Single> wystąpień, albo <xref:System.ServiceModel.ConcurrencyMode.Single> lub <xref:System.ServiceModel.ConcurrencyMode.Multiple> współbieżności jest istotne, w zależności od tego, czy pojedyncze wystąpienie przetwarza wiadomości sekwencyjnie lub jednocześnie. W <xref:System.ServiceModel.InstanceContextMode.PerSession> wystąpień, dowolnym trybie współbieżności mogą być istotne.  
  
 Klasa usługi określa zachowanie współbieżności `[ServiceBehavior(ConcurrencyMode=<setting>)]` atrybutu, jak pokazano w poniższym przykładzie kodu. Zmieniając wierszy, które są oznaczone jako komentarz, możesz eksperymentować z `Single` i `Multiple` tryby współbieżności. Pamiętaj, aby odbudować usługę po zmianie trybu współbieżności.  
  
```  
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
  
 W przykładzie użyto <xref:System.ServiceModel.ConcurrencyMode.Multiple> współbieżności z <xref:System.ServiceModel.InstanceContextMode.Single> wystąpień domyślnie. Kod klienta został zmodyfikowany w celu użycia asynchronicznego serwera proxy. Dzięki temu klient może wykonywać wiele wywołania do usługi bez oczekiwania na odpowiedź między każdym wywołaniu. Można obserwować różnice w zachowaniu tryb współbieżności usługi.  
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Tryb współbieżności, w którym jest uruchomiona w ramach jest wyświetlany, nosi nazwę każdej operacji, a następnie wyświetlana jest liczba operacji. Zwróć uwagę, że gdy tryb współbieżności jest `Multiple`, wyniki są zwracane w innym porządku niż jak były nazywane, ponieważ usługa przetwarza wiele komunikatów jednocześnie. Zmieniając tryb współbieżności na `Single`, wyniki są zwracane w kolejności ich były nazywane, ponieważ usługa przetwarza każdy komunikat po kolei. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Jeśli używasz Svcutil.exe do generowania klienta serwera proxy, upewnij się, że obejmuje `/async` opcji.  
  
3.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
  
## <a name="see-also"></a>Zobacz też
