---
title: Żądanie nietypu-odpowiedź
ms.date: 03/30/2017
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
ms.openlocfilehash: 132ae05236b23ff5bb0cce67d66d26d308cce305
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038685"
---
# <a name="untyped-requestreply"></a>Nietypizowane żądanie/nietypizowana odpowiedź
Ten przykład ilustruje sposób definiowania kontraktów operacji, które używają klasy Message.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Kontrakt usługi definiuje jedną operację, która przyjmuje typ komunikatu jako argument i zwraca komunikat. Operacja zbiera wszystkie wymagane dane w celu obliczenia sumy z treści wiadomości, a następnie wysyła sumę jako treść w komunikacie zwrotnym.  
  
```csharp
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 W usłudze operacja pobiera tablicę liczb całkowitych przekazaną w komunikacie wejściowym, a następnie oblicza sumę. Aby wysłać komunikat odpowiedzi, przykład tworzy nową wiadomość z odpowiednią wersją i akcją wiadomości i dodaje obliczoną sumę jako treść. Poniższy przykładowy kod demonstruje ten sposób.  
  
```csharp
public Message ComputeSum(Message request)  
{  
    //The body of the message contains a list of numbers which will be   
    //read as a int[] using GetBody<T>  
    int result = 0;  
  
    int[] inputs = request.GetBody<int[]>();  
    foreach (int i in inputs)  
    {  
        result += i;  
    }  
  
    Message response = Message.CreateMessage(request.Version,   
                                      ReplyAction, result);  
    return response;  
}  
```  
  
 Klient korzysta z kodu wygenerowanego przez [Narzędzie do obsługi metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) , aby utworzyć serwer proxy w usłudze zdalnej. Aby wysłać komunikat żądania, klient musi mieć wersję wiadomości, która zależy od kanału bazowego. W tym celu tworzy nowy <xref:System.ServiceModel.OperationContextScope> zakres w utworzonym przez siebie kanale serwera proxy, który <xref:System.ServiceModel.OperationContext> tworzy z prawidłową wersją wiadomości wypełnioną w jej `OutgoingMessageHeaders.MessageVersion` właściwości. Klient przekaże tablicę wejściową jako treść komunikatu żądania, a następnie wywoła `ComputeSum` na serwerze proxy. Następnie klient pobiera sumę danych wejściowych, które przekazuje, uzyskując dostęp `GetBody<T>` do metody w komunikacie odpowiedzi. Poniższy przykładowy kod demonstruje ten sposób.  
  
```csharp
using (new OperationContextScope(client.InnerChannel))  
{  
    // Call the Sum service operation.  
    int[] values = { 1, 2, 3, 4, 5 };  
    Message request = Message.CreateMessage(  
        OperationContext.Current.OutgoingMessageHeaders.MessageVersion,   
        RequestAction, values);  
    Message reply = client.ComputeSum(request);  
    int response = reply.GetBody<int>();  
  
    Console.WriteLine("Sum of numbers passed (1,2,3,4,5) = {0}",   
                                                       response);  
}  
```  
  
 Ten przykład jest przykładem hostowanym w sieci Web i dlatego musi być uruchomiony tylko plik wykonywalny klienta. Poniżej przedstawiono przykładowe dane wyjściowe na komputerze klienckim.  
  
```console  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 Ten przykład jest przykładem hostowanym w sieci Web, więc sprawdź link podany w kroku 3, aby zobaczyć, jak skompilować i uruchomić przykład.  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
