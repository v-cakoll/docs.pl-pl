---
title: Komunikacja jednokierunkowa
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a781963205f260c82d3db316680c9e8c33045434
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="one-way"></a>Komunikacja jednokierunkowa
W przykładzie pokazano kontaktu usługi z usługi jednokierunkowej operacji. Klient czeka na zakończenie jak w przypadku operacji usługi dwukierunkowe operacji usługi. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i używa `wsHttpBinding` powiązania. Usługa w tym przykładzie jest aplikacji konsoli siebie umożliwia obserwowanie usługa, która odbiera i przetwarza żądania. Klient jest również aplikacji konsoli.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Aby utworzyć kontrakt usługi jednokierunkowe, zdefiniuj dany kontrakt usługi, zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej operacji i ustaw <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> do `true` jak pokazano w poniższym kodzie próbki:  
  
```  
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
  
 Aby zademonstrować, że klient nie czeka na zakończenie operacji usługi, kodu usługi, w tym przykładzie implementuje pięciu sekund opóźnienia, jak pokazano w poniższym kodzie próbki:  
  
```  
/ This service class implements the service contract.  
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
  
 Kiedy klient wywołuje usługę, wywołanie zwraca bez oczekiwania na zakończenie operacji usługi.  
  
 Po uruchomieniu próbki działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta. Można wyświetlić wiadomości receive usługi z klienta. Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć zarówno usługę i klienta.  
  
 Klient kończy wcześniejsze usługi, z którego wynika, że klient nie czeka na zakończenie operacji jednokierunkowych usługi. Dane wyjściowe klienta jest następujący:  
  
```  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 Przedstawiono to następujące dane wyjściowe usługi:  
  
```  
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
>  HTTP jest zgodnie z definicją protokołu żądań i odpowiedzi; Po wysłaniu żądania odpowiedź jest zwracana. Dotyczy to nawet w przypadku operacji jednokierunkowych usługi uwidocznionego za pośrednictwem protokołu HTTP. Po wywołaniu operacji usługi zwraca kod stanu HTTP 202 przed wykonał operacji usługi. Ten kod stanu oznacza, że żądanie zostało zaakceptowane do przetwarzania, ale przetwarzanie nie zostało jeszcze zakończone. Klient, który wywołał operację bloków, dopóki nie odbierze 202 odpowiedzi z usługi. To może spowodować niektórych nieoczekiwanego zachowania, gdy wiele jednokierunkowe komunikaty są wysyłane przy użyciu powiązania, który jest skonfigurowany do używania sesji. `wsHttpBinding` Powiązania używanego w tym przykładzie jest skonfigurowany do używania sesji, aby domyślnie ustanowić kontekst zabezpieczeń. Domyślnie wiadomości w sesji dotrą do celu w kolejności, w jakiej są wysyłane. W związku z tym gdy drugi komunikat w sesji jest wysyłany, nie został przetworzony dopóki pierwszy komunikat został przetworzony. Wynik jest, że klient odbiera 202 odpowiedzi na wiadomość dopiero po ukończeniu przetwarzania poprzedniej wiadomości. Klient jest wyświetlany w związku z tym do bloku przy każdym wywołaniu kolejnych operacji. Aby uniknąć tego zachowania, ten przykład konfiguruje środowiska uruchomieniowego do wysyłania wiadomości do jednocześnie odrębnych wystąpień do przetwarzania. Ustawia próbki <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> do `PerCall` tak, aby każdy komunikat mogą być przetwarzane przez inne wystąpienie. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>ustawiono `Multiple` zezwalająca na więcej niż jeden wątek na wysyłanie wiadomości w czasie.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Przed uruchomieniem klienta i zamknąć klienta przed zamknięciem usługi, należy uruchomić usługę. Pozwala to uniknąć wyjątek klienta, gdy klient nie można zamknąć sesji zabezpieczeń prawidłowo, ponieważ usługa został usunięty.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
  
## <a name="see-also"></a>Zobacz też
