---
title: Komunikacja jednokierunkowa
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 3203762e05c794ed28b65d8fded6972fac1f5820
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183441"
---
# <a name="one-way"></a>Komunikacja jednokierunkowa
W tym przykładzie pokazano kontakt usługi z jednokierunkowych operacji usługi. Klient nie czeka na zakończenie operacji usługi, jak ma to miejsce w przypadku operacji usługi dwukierunkowej. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) `wsHttpBinding` i używa powiązania. Usługa w tym przykładzie jest samodzielną aplikacją konsoli, aby umożliwić obserwowanie usługi, która odbiera i przetwarza żądania. Klient jest również aplikacją konsoli.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Aby utworzyć jednokierunkową umowę serwisową, zdefiniuj umowę serwisową, zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasę do każdej operacji i <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `true` ustaw, jak pokazano w poniższym przykładowym kodzie:  
  
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
  
 Aby wykazać, że klient nie czeka na zakończenie operacji usługi, kod usługi w tym przykładzie implementuje opóźnienie pięciu sekund, jak pokazano w poniższym przykładowym kodzie:  
  
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
  
 Po uruchomieniu przykładu działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta. Możesz zobaczyć, że usługa odbiera wiadomości od klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć zarówno usługę, jak i klienta.  
  
 Klient kończy przed usługą, wykazując, że klient nie czeka na zakończenie operacji usługi jednokierunkowej. Dane wyjściowe klienta są następujące:  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 Następujące dane wyjściowe usługi są wyświetlane:  
  
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
> PROTOKÓŁ HTTP jest z definicji protokołem żądania/odpowiedzi; po złożeniu żądania zwracana jest odpowiedź. Dotyczy to nawet operacji usługi jednokierunkowej, która jest widoczna za pośrednictwem protokołu HTTP. Gdy operacja jest wywoływana, usługa zwraca kod stanu HTTP 202 przed wykonaniem operacji usługi. Ten kod stanu oznacza, że żądanie zostało zaakceptowane do przetworzenia, ale przetwarzanie nie zostało jeszcze zakończone. Klient, który wezwał bloki operacji, dopóki nie otrzyma odpowiedzi 202 z usługi. Może to spowodować pewne nieoczekiwane zachowanie, gdy wiele komunikatów jednokierunkowych są wysyłane przy użyciu powiązania, które jest skonfigurowane do korzystania z sesji. Powiązanie `wsHttpBinding` używane w tym przykładzie jest skonfigurowane do domyślnego używania sesji w celu ustanowienia kontekstu zabezpieczeń. Domyślnie wiadomości w sesji są gwarantowane do jść w kolejności, w jakiej są wysyłane. Z tego powodu po wysłaniu drugiej wiadomości w sesji nie jest przetwarzana, dopóki nie zostanie przetworzona pierwsza wiadomość. Wynik jest to, że klient nie otrzyma odpowiedzi 202 dla wiadomości, dopóki przetwarzanie poprzedniej wiadomości zostało zakończone. W związku z tym klient wydaje się blokować przy każdym kolejnym wywołaniu operacji. Aby uniknąć tego zachowania, w tym przykładzie konfiguruje środowisko uruchomieniowe do wysyłania komunikatów jednocześnie do różnych wystąpień do przetwarzania. Przykładowy <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> zestaw, tak aby `PerCall` każda wiadomość może być przetwarzane przez inne wystąpienie. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>jest ustawiona, aby `Multiple` zezwolić na więcej niż jeden wątek do wysyłania wiadomości w czasie.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
> Uruchom usługę przed uruchomieniem klienta i zamknąć klienta przed zamknięciem usługi. Pozwala to uniknąć wyjątku klienta, gdy klient nie może zamknąć sesji zabezpieczeń czysto, ponieważ usługa zniknęła.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
