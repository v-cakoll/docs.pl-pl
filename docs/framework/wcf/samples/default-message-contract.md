---
title: Domyślny kontrakt komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 29bfb88d638f68b2f9a3ba983a5c38fe49edb9a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="default-message-contract"></a>Domyślny kontrakt komunikatów
Domyślny kontrakt komunikatów w przykładzie pokazano usługi, gdy wiadomość niestandardowe zdefiniowane przez użytkownika jest przekazywany do i z operacji usługi. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej interfejs Kalkulator jako typu usługi. Zamiast poszczególnych usług operacji dodawania, odejmowania mnożenia i dzielenia używane w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), w tym przykładzie przekazuje niestandardowy komunikat, który zawiera argumenty operacji i operatora i zwraca wynik operacji arytmetycznych.  
  
 Klient znajduje się program konsoli (.exe) i usługi biblioteki (.dll) jest obsługiwana przez Internet Information Services (IIS). Aktywność klienta jest widoczna w oknie konsoli.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W usłudze operacji usługi pojedynczej zdefiniowano akceptuje i zwraca komunikaty niestandardowe typu `MyMessage`. Mimo że w tym przykładzie komunikatów żądań i odpowiedzi są tego samego typu, oczywiście może być inny komunikat kontraktów w razie potrzeby.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 Niestandardowy komunikat `MyMessage` jest zdefiniowany w klasie opatrzoną <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> i <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybutów. Trzeci Konstruktor jest używany w tym przykładzie. Używanie kontraktów komunikatu umożliwia wykonywanie pełnej kontroli nad komunikatu protokołu SOAP. W tym przykładzie <xref:System.ServiceModel.MessageHeaderAttribute> atrybut służy do put `Operation` w nagłówku protokołu SOAP. Argumenty operacji `N1`, `N2` i `Result` wystąpić w treści protokołu SOAP, ponieważ mają one <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybut zastosowany.  
  
```  
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
  
 Klasa implementacji zawiera kod `Calculate` operacji usługi. `CalculateService` Klas uzyskuje argumenty i operatora z komunikatu żądania i tworzy komunikat odpowiedzi, zawierający wynik żądanej operacji, jak pokazano w poniższym kodzie próbki.  
  
```  
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
  
 Wygenerowanego kodu klienta dla klienta został utworzony z [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia. Narzędzie automatycznie tworzy typy kontraktu komunikatu w kodzie wygenerowanego klienta, jeśli to konieczne. `/messageContract` Można określić opcji polecenia, aby wymuszenie kontraktów komunikatu.  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Następujący przykładowy kod przedstawia klienta przy użyciu `MyMessage` wiadomości.  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage();  
request.N1 = 100D;  
request.N2 = 15.99D;  
request.Operation = "+";  
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 Po uruchomieniu próbki obliczenia są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 W tym momencie przekazanego niestandardowe zdefiniowane przez użytkownika wiadomości między klientem a operacji usługi. Kontrakt komunikatu zdefiniowane, że argumenty i wyniki były w treści wiadomości i że operator w nagłówku wiadomości. Rejestrowanie komunikatów można skonfigurować do stosowania tej struktury wiadomości.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
  
## <a name="see-also"></a>Zobacz też
