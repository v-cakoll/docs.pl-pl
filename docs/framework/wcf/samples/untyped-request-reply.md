---
title: Bez typu żądanie odpowiedź.
ms.date: 03/30/2017
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
ms.openlocfilehash: ef1e20bbeaf5f7a0d9eae4b921628482714c6163
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505345"
---
# <a name="untyped-requestreply"></a>Nietypizowane żądanie/nietypizowana odpowiedź
W tym przykładzie pokazano sposób definiowania kontrakty operacji, które używają klasy wiadomości.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Kontrakt usługi definiuje jedną operację, który przyjmuje typ komunikatu jako argument i zwraca komunikat. Operacja zbiera wszystkie dane wymagane do obliczenia sumie z treści wiadomości, a następnie wysyła Suma jako treść w zwróconego komunikatu.  
  
```  
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 W usłudze operacji pobiera tablicę liczb całkowitych przekazano komunikat wejściowy, a następnie oblicza sumę. Aby wysłać komunikat odpowiedzi, próbka tworzy nowy komunikat z wersją odpowiedni komunikat i akcji i dodaje obliczona suma jako jego treści. Następujący przykładowy kod przedstawia to.  
  
```  
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
  
 Klient korzysta z kodu, który jest generowany przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do utworzenia obiektu pośredniczącego dla usługi zdalnej. Aby wysłać komunikat żądania, klient musi mieć wersji wiadomości, która jest zależna od kanału źródłowego. W związku z tym tworzy nowy <xref:System.ServiceModel.OperationContextScope> ograniczone do kanału proxy go utworzyć, który tworzy <xref:System.ServiceModel.OperationContext> z wersją komunikatów wypełnionych w jego `OutgoingMessageHeaders.MessageVersion` właściwości. Klient przekazuje tablicy wejściowej jako treść komunikatu żądania, a następnie wywołuje `ComputeSum` na serwerze proxy. Klient następnie pobiera Suma przeszła uzyskując dostęp do danych wejściowych `GetBody<T>` metody dla komunikatu odpowiedzi. Następujący przykładowy kod przedstawia to.  
  
```  
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
  
 W tym przykładzie przedstawiono przykładowe hostowanych w sieci Web i musi być uruchomiony tylko plik wykonywalny klienta. Oto przykładowe dane wyjściowe na kliencie.  
  
```  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 Ten przykład jest przykładowe hostowanych w sieci Web i wyboru tak, podane łącze w kroku nr 3, aby zobaczyć, jak skompilować i uruchomić próbki.  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
  
## <a name="see-also"></a>Zobacz też
