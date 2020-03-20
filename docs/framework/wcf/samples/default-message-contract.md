---
title: Domyślny kontrakt komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 46b69697616ad7983daed16f8a180a4da7f61a16
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183769"
---
# <a name="default-message-contract"></a>Domyślny kontrakt komunikatów
Przykład domyślnej umowy wiadomości pokazuje usługę, w której niestandardowa wiadomość zdefiniowana przez użytkownika jest przekazywana do i z operacji usługi. Ten przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje interfejs kalkulatora jako wpisaną usługę. Zamiast poszczególnych operacji usługi dodawania, odejmowania, mnożenia i dzielenia używanego w [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md)w tym przykładzie przekazuje niestandardowy komunikat zawierający zarówno argumenty, jak i operator i zwraca wynik obliczeń arytmetycznych.  
  
 Klient jest programem konsoli (exe), a biblioteka usług (dll) jest obsługiwana przez internetowe usługi informacyjne (IIS). Aktywność klienta jest widoczna w oknie konsoli.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W usłudze zdefiniowano pojedynczą operację usługi, która akceptuje `MyMessage`i zwraca niestandardowe wiadomości typu . Chociaż w tym przykładzie wiadomości żądania i odpowiedzi są tego samego typu, mogą one oczywiście być różne kontrakty wiadomości, jeśli to konieczne.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 Wiadomość `MyMessage` niestandardowa jest zdefiniowana w <xref:System.ServiceModel.MessageContractAttribute>klasie <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> z adnotacjami i atrybutami. Tylko trzeci konstruktor jest używany w tym przykładzie. Za pomocą kontraktów wiadomości pozwala na wykonywanie pełnej kontroli nad komunikatem SOAP. W tym przykładzie <xref:System.ServiceModel.MessageHeaderAttribute> atrybut jest `Operation` używany do umieszczenia w nagłówku SOAP. `N1`Argumenty `N2` i pojawiają się `Result` w treści SOAP, ponieważ <xref:System.ServiceModel.MessageBodyMemberAttribute> mają zastosowany atrybut.  
  
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
  
 Klasa implementacji zawiera kod `Calculate` dla operacji usługi. Klasa `CalculateService` uzyskuje operands i operator z komunikatu żądania i tworzy komunikat odpowiedzi, który zawiera wynik żądanego obliczenia, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Wygenerowany kod klienta dla klienta został utworzony za pomocą narzędzia [ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) Narzędzie automatycznie tworzy typy kontraktów wiadomości w wygenerowanym kodzie klienta, jeśli to konieczne. Opcja `/messageContract` polecenia może być określona, aby wymusić generowanie kontraktów wiadomości.  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Poniższy przykładowy kod pokazuje `MyMessage` klienta przy użyciu wiadomości.  
  
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
  
 Po uruchomieniu próbki obliczenia są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 W tym momencie niestandardowe komunikaty zdefiniowane przez użytkownika zostały przekazane między klientem a operacją usługi. Kontrakt wiadomości zdefiniowane, że argumenty i wyniki były w treści wiadomości i że operator był w nagłówku wiadomości. Rejestrowanie wiadomości można skonfigurować tak, aby obserwować tę strukturę komunikatów.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
