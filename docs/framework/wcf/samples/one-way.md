---
title: Komunikacja jednokierunkowa
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 0035b64b14b0d32f39974e8eaa28242290d665c0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957244"
---
# <a name="one-way"></a>Komunikacja jednokierunkowa
Ten przykład pokazuje kontakt z usługą z jednokierunkowymi operacjami usługi. Klient nie czeka na zakończenie operacji usługi, podobnie jak w przypadku operacji dwukierunkowych usługi. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i używa `wsHttpBinding` powiązania. Usługa w tym przykładzie to samodzielna aplikacja konsolowa, która umożliwia obserwowanie usługi, która odbiera i przetwarza żądania. Klient jest również aplikacją konsolową.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Aby utworzyć kontrakt usługi jednokierunkowej, zdefiniuj kontrakt usługi, Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasę do każdej operacji i `true` ustaw wartość <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> tak, jak pokazano w poniższym przykładowym kodzie:  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 Aby zademonstrować, że klient nie czeka na zakończenie operacji usługi, kod usługi w tym przykładzie implementuje pięć-sekundowe opóźnienie, jak pokazano w poniższym przykładowym kodzie:  
  
```csharp
// This service class implements the service contract.  
// This code writes output to the console window.  
 [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple,  
    InstanceContextMode = InstanceContextMode.PerCall)]  
public class CalculatorService : IOneWayCalculator  
{  
    public void Add(double n1, double n2)  
    {  
        Console.WriteLine("Received Add({0},{1}) - sleeping", n1, n2);  
        System.Threading.Thread.Sleep(1000 * 5);  
        double result = n1 + n2;  
        Console.WriteLine("Processing Add({0},{1}) - result: {2}", n1, n2, result);  
    }  
    ...  
}  
```  
  
 Gdy klient wywołuje usługę, wywołanie zwraca bez oczekiwania na zakończenie operacji usługi.  
  
 Po uruchomieniu przykładu działania klienta i usługi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta. Możesz zobaczyć, że usługa odbiera komunikaty od klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.  
  
 Klient kończy pracę przed usługą, pokazując, że klient nie czeka na zakończenie operacji jednokierunkowej usługi. Dane wyjściowe klienta są następujące:  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 Wyświetlane są następujące dane wyjściowe usługi:  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Received Add(100,15.99) - sleeping  
Received Subtract(145,76.54) - sleeping  
Received Multiply(9,81.25) - sleeping  
Received Divide(22,7) - sleeping  
Processing Add(100,15.99) - result: 115.99  
Processing Subtract(145,76.54) - result: 68.46  
Processing Multiply(9,81.25) - result: 731.25  
Processing Divide(22,7) - result: 3.14285714285714  
```  
  
> [!NOTE]
> HTTP to, według definicji, protokołu żądania/odpowiedzi; Po wykonaniu żądania zwracana jest odpowiedź. Jest to prawdziwe nawet dla jednokierunkowej operacji usługi, która jest udostępniona za pośrednictwem protokołu HTTP. Po wywołaniu operacji usługa zwraca kod stanu HTTP 202 przed wykonaniem operacji usługi. Ten kod stanu oznacza, że żądanie zostało zaakceptowane do przetworzenia, ale przetwarzanie nie zostało jeszcze zakończone. Klient, który wywołał bloki operacji, dopóki nie odbierze odpowiedzi 202 od usługi. Może to spowodować pewne nieoczekiwane zachowanie, gdy wiele komunikatów jednokierunkowych jest wysyłanych przy użyciu powiązania, które jest skonfigurowane do korzystania z sesji. `wsHttpBinding` Powiązanie używane w tym przykładzie jest skonfigurowane tak, aby domyślnie używać sesji w celu ustanowienia kontekstu zabezpieczeń. Domyślnie komunikaty w sesji są gwarantowane w kolejności, w jakiej są wysyłane. W związku z tym, gdy wysyłany jest drugi komunikat w sesji, nie jest przetwarzany do momentu przetworzenia pierwszego komunikatu. Wynika to z tego, że klient nie otrzymuje odpowiedzi 202 na komunikat do momentu ukończenia przetwarzania poprzedniego komunikatu. W związku z tym klient jest blokowany dla każdego kolejnego wywołania operacji. Aby uniknąć tego zachowania, ten przykład umożliwia skonfigurowanie środowiska uruchomieniowego do wysyłania komunikatów współbieżnie do różnych wystąpień do przetworzenia. Przykład ustawia <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> się tak `PerCall` , aby każdy komunikat mógł być przetwarzany przez inne wystąpienie. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>jest ustawiona na `Multiple` tak, aby umożliwić wysyłanie komunikatów jednocześnie więcej niż jeden wątek.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
> Uruchom usługę przed uruchomieniem klienta i wyłącz klienta przed zamknięciem usługi. Pozwala to uniknąć wyjątku klienta, gdy klient nie może prawidłowo zamknąć sesji zabezpieczeń, ponieważ usługa zniknęła.  
  
> [!IMPORTANT]
>  Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
