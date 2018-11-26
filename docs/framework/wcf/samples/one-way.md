---
title: Komunikacja jednokierunkowa
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 9a8af4bcdc76afd96ada595a7234cbc5e0250dfc
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52296701"
---
# <a name="one-way"></a>Komunikacja jednokierunkowa
Niniejszy przykład pokazuje usługi skontaktuj się z operacji usługi jednokierunkowej. Klient nie czeka na zakończenie, jak w przypadku operacji dwukierunkowe usługi przy użyciu operacji usługi. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i używa `wsHttpBinding` powiązania. Usługi w tym przykładzie to aplikacja konsoli Self-Hosted umożliwia obserwowanie usługa, która odbiera i przetwarza żądania. Klient jest również Aplikacja konsoli.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Aby utworzyć kontrakt usługi jednokierunkowej, definiowanie kontraktu usługi, usługi, zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej operacji, a następnie ustaw <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> do `true` jak pokazano w poniższym przykładowym kodzie:  
  
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
  
 Aby zademonstrować, że klient nie czeka na zakończenie operacji usługi, kod usługi, w tym przykładzie implementuje pięciu sekund opóźnienia, jak pokazano w poniższym przykładowym kodzie:  
  
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
  
 Po uruchomieniu przykładu, działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta. Możesz zobaczyć komunikaty odbierania usługi z klienta. Naciśnij klawisz ENTER w każdego okna konsoli, aby zamknąć usługę i klienta.  
  
 Klient zakończy się wcześniej usługi, prezentacja, że klient nie czeka na zakończenie operacji usługi jednokierunkowej. Dane wyjściowe klienta jest następujący:  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 Następujące dane wyjściowe usługi jest wyświetlany:  
  
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
>  Zgodnie z definicją, HTTP jest protokół żądanie/odpowiedź; Po wysłaniu żądania, odpowiedź jest zwracana. Ta zasada obowiązuje nawet w przypadku operacji usługi jednokierunkowej, który jest dostępny za pośrednictwem protokołu HTTP. Po wywołaniu operacji usługa zwraca kod stanu HTTP 202, zanim została wykonana operacja usługi. Ten kod stanu oznacza, że żądanie zostało zaakceptowane do przetwarzania, ale przetwarzanie nie zostało jeszcze zakończone. Klient, który wywołał operację blokuje, dopóki nie odbierze odpowiedzi 202 z usługi. Może to spowodować niektóre nieoczekiwane zachowanie, gdy wiele jednokierunkowe komunikaty są wysyłane przy użyciu powiązania, który jest skonfigurowany do używania sesji. `wsHttpBinding` Powiązania używanego w tym przykładzie jest skonfigurowany do używania sesji, aby domyślnie ustanawiania kontekstu zabezpieczeń. Domyślnie komunikaty w sesji dotrą do celu w kolejności, w której są wysyłane. W związku z tym gdy drugi komunikat w sesji są wysyłane, nie został przetworzony aż pierwszy komunikat został przetworzony. Z tego powodu jest, że klient nie otrzyma odpowiedzi 202 wiadomości do momentu zakończenia przetwarzania poprzedni komunikat. Klient w związku z tym wydaje się blok przy każdym wywołaniu kolejna operacja. Aby uniknąć tego zachowania, ten przykład umożliwia skonfigurowanie środowiska uruchomieniowego do wysyłania komunikatów jednocześnie w celu odrębnych wystąpień do przetworzenia. Przykładowe zestawy <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> do `PerCall` tak, aby każdy komunikat mogą być przetwarzane przez inne wystąpienie. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ustawiono `Multiple` umożliwia więcej niż jeden wątek do wysyłania wiadomości w czasie.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Przed uruchomieniem klienta i zamknąć klienta przed zamknięciem usługi, należy uruchomić usługę. Umożliwia to uniknięcie wyjątek klienta, gdy klient nie można zamknąć sesji zabezpieczeń nie pozostawia żadnych śladów, ponieważ usługa został usunięty.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
  
## <a name="see-also"></a>Zobacz też
