---
title: Domyślny kontrakt komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 267cdffdc532aaa2b31de835c31d23e93aca8c54
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315520"
---
# <a name="default-message-contract"></a>Domyślny kontrakt komunikatów
Domyślny kontrakt komunikatów w przykładzie pokazano, usługi, w której niestandardowy komunikat zdefiniowany przez użytkownika jest przekazywany do i z operacji usługi. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej interfejs Kalkulator, co usługa wpisane. Zamiast poszczególnych usług operacjami dotyczącymi dodawania, odejmowania, mnożenia i dzielenia używane w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), w tym przykładzie przekazuje niestandardowy komunikat, która zawiera argumenty operacji i operatora i zwraca wynik obliczeń arytmetycznych.  
  
 Klient znajduje się program konsoli (.exe), a Usługa biblioteki (.dll) jest obsługiwana przez Internetowe usługi informacyjne (IIS). Aktywność klienta jest widoczna w oknie konsoli.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 W usłudze operacji usługi pojedynczej jest zdefiniowany, która przyjmuje i zwraca niestandardowe komunikaty o typie `MyMessage`. Mimo że w tym przykładzie komunikatów żądań i odpowiedzi są tego samego typu, można oczywiście one kontraktów inny komunikat w razie potrzeby.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 Niestandardowy komunikat `MyMessage` zdefiniowanej w klasie, oznaczony za pomocą <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> i <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybutów. Trzeci Konstruktor jest używany w tym przykładzie. Używanie kontraktów komunikatu można wykonywać pełną kontrolę nad komunikatu protokołu SOAP. W tym przykładzie <xref:System.ServiceModel.MessageHeaderAttribute> atrybut jest używany do umieszczenia `Operation` w nagłówku protokołu SOAP. Argumenty operacji `N1`, `N2` i `Result` są wyświetlane w treści protokołu SOAP, ponieważ mają one <xref:System.ServiceModel.MessageBodyMemberAttribute> zastosowany.  
  
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
  
 Klasa implementacji zawiera kod `Calculate` operacji usługi. `CalculateService` Klasy uzyskuje operandy i operator poza komunikatem żądania i tworzy komunikat odpowiedzi, zawierający wynik żądanego obliczenia, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Wygenerowanego kodu klienta dla klienta został utworzony za pomocą [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia. Narzędzie automatycznie tworzy typy kontraktu komunikatu, w kodzie wygenerowanego klienta, jeśli to konieczne. `/messageContract` Można określić opcji polecenia, aby wymusić generowania kontrakty komunikatów.  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Następujący przykładowy kod przedstawia klienta przy użyciu `MyMessage` wiadomości.  
  
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
  
 Po uruchomieniu przykładu, obliczenia są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 W tym momencie komunikaty niestandardowe zdefiniowane przez użytkownika są spełnione między klientem a operacji usługi. Kontraktu komunikatu zdefiniowana, że argumenty operacji i wyniki były w treści komunikatu i że operatora w nagłówku komunikatu. Rejestrowanie komunikatów można skonfigurować do obserwowania strukturą wiadomości.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
