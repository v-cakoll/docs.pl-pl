---
title: Domyślny kontrakt komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 2115ac88c52efca09d32a870fc52905f80f6f746
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045053"
---
# <a name="default-message-contract"></a>Domyślny kontrakt komunikatów
Domyślny przykład kontraktu komunikatu pokazuje usługę, w której do i z operacji usługi jest przesyłany niestandardowy komunikat zdefiniowany przez użytkownika. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje interfejs kalkulatora jako usługę o określonym typie. Zamiast poszczególnych operacji usługi do dodawania, odejmowania, mnożenia i dzielenia używanych w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), ten przykład przekazuje komunikat niestandardowy, który zawiera operandy i operator, i zwraca wynik Obliczanie arytmetyczne.  
  
 Klient jest programem konsolowym (. exe), a Biblioteka usług (. dll) jest hostowana przez Internet Information Services (IIS). Aktywność klienta jest widoczna w oknie konsoli.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W usłudze jest zdefiniowana jedna operacja usługi, która akceptuje i zwraca niestandardową wiadomość typu `MyMessage`. Mimo że w tym przykładzie komunikaty żądania i odpowiedzi są tego samego typu, w razie potrzeby mogą oczywiście być różne umowy dotyczące komunikatów.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 Wiadomość `MyMessage` niestandardowa jest definiowana w klasie <xref:System.ServiceModel.MessageHeaderAttribute> z <xref:System.ServiceModel.MessageContractAttribute>adnotacjami i <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybutami. Tylko trzeci Konstruktor jest używany w tym przykładzie. Używanie kontraktów komunikatów umożliwia pełną kontrolę nad komunikatem protokołu SOAP. W tym przykładzie <xref:System.ServiceModel.MessageHeaderAttribute> atrybut jest używany do umieszczania `Operation` w nagłówku protokołu SOAP. Operandy `N1`i <xref:System.ServiceModel.MessageBodyMemberAttribute> `N2` pojawiająsięwtreściprotokołuSOAP,ponieważmajązastosowaneatrybuty.`Result`  
  
```csharp
[MessageContract]  
public class MyMessage  
{  
    private string operation;  
    private double n1;  
    private double n2;  
    private double result;  
  
    //Constructor - create an empty message.  
  
    public MyMessage() {}  
  
    //Constructor - create a message and populate its members.  
  
    public MyMessage(double n1, double n2, string operation,   
                     double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    //Constructor - create a message from another message.  
  
    public MyMessage(MyMessage message)  
    {  
        this.n1 = message.n1;  
        this.n2 = message.n2;  
        this.operation = message.operation;  
        this.result = message.result;  
    }  
  
    [MessageHeader]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [MessageBodyMember]  
    public double N1  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [MessageBodyMember]  
    public double N2  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [MessageBodyMember]  
    public double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
}  
```  
  
 Klasa implementacji zawiera kod dla `Calculate` operacji usługi. `CalculateService` Klasa uzyskuje operandy i operator z komunikatu żądania i tworzy komunikat odpowiedzi, który zawiera wynik żądanego obliczenia, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
// Service class which implements the service contract.  
public class CalculatorService : ICalculator  
{  
    // Perform a calculation.  
  
    public MyMessage Calculate(MyMessage request)  
    {  
        MyMessage response = new MyMessage(request);  
        switch (request.Operation)  
        {  
            case "+":  
                response.Result = request.N1 + request.N2;  
                break;  
            case "-":  
                response.Result = request.N1 - request.N2;  
                break;  
            case "*":  
                response.Result = request.N1 * request.N2;  
                break;  
            case "/":  
                response.Result = request.N1 / request.N2;  
                break;  
            default:  
                response.Result = 0.0D;  
                break;  
        }  
        return response;  
    }  
}  
```  
  
 Wygenerowany kod klienta dla klienta został utworzony za pomocą narzędzia [Svcutil. exe (narzędzie do przesyłania metadanych)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) . W razie potrzeby narzędzie automatycznie tworzy w kodzie wygenerowanym klienta typy kontraktów komunikatów. Opcja `/messageContract` polecenia może być określona, aby wymusić generowanie kontraktów komunikatów.  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Następujący przykładowy kod demonstruje klienta korzystającego z `MyMessage` wiadomości.  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage() 
                    {  
                        N1 = 100D,  
                        N2 = 15.99D,  
                        Operation = "+"  
                    };
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 Po uruchomieniu przykładu obliczenia są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 W tym momencie niestandardowe komunikaty zdefiniowane przez użytkownika przechodzą między klientem a operacją usługi. Kontrakt komunikatu określił, że operandy i wyniki znajdowały się w treści wiadomości i że operator znajdował się w nagłówku komunikatu. Rejestrowanie komunikatów można skonfigurować tak, aby obserwować tę strukturę komunikatów.  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
