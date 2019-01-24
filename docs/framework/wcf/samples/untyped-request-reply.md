---
title: Nietypizowane żądanie odpowiedź.
ms.date: 03/30/2017
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
ms.openlocfilehash: 2eb6a46d339c9277c1622c0cc16d057b186f1d79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612752"
---
# <a name="untyped-requestreply"></a>Nietypizowane żądanie/nietypizowana odpowiedź
Niniejszy przykład pokazuje jak zdefiniować kontrakty operacji, korzystających z klasy wiadomości.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Kontrakt usługi definiuje jedna operacja, która przyjmuje typ komunikatu jako argument i zwraca komunikat. Operacja zbiera wszystkie dane wymagane do obliczenia sum z treści wiadomości, a następnie wysyła Suma jako treść w komunikacie zwrotu.  
  
```csharp
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 W usłudze operacja pobiera tablicę liczb całkowitych przekazanej do komunikatu wejściowego, a następnie oblicza sumę. Aby wysłać komunikat odpowiedzi, próbka tworzy nowy komunikat z wersją odpowiedni komunikat i akcji i dodaje obliczona suma jako jej treści. Następujący przykładowy kod pokazuje to.  
  
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
  
 Klient korzysta z kodu, który jest generowany przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do utworzenia serwera proxy do zdalnej usługi. Aby wysłać komunikat żądania, klient musi mieć wersji wiadomości, która jest zależna od kanału źródłowego. W związku z tym, tworzy nową <xref:System.ServiceModel.OperationContextScope> ograniczone do serwera proxy kanału on utworzony, co powoduje utworzenie <xref:System.ServiceModel.OperationContext> wersją komunikatów wypełnionych w jego `OutgoingMessageHeaders.MessageVersion` właściwości. Klient przekazuje tablicy wejściowej jako treść komunikatu żądania, a następnie wywołuje `ComputeSum` na serwerze proxy. Klient pobiera następnie sumę przeszła, uzyskując dostęp do danych wejściowych `GetBody<T>` metody na komunikat odpowiedzi. Następujący przykładowy kod pokazuje to.  
  
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
  
 W tym przykładzie przedstawiono przykładowe hostowanych w sieci Web i musi być uruchamiany tylko plik wykonywalny klienta. Poniżej przedstawiono przykładowe dane wyjściowe na komputerze klienckim.  
  
```console  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 W tym przykładzie to przykładowy hostowanych w sieci Web i wyboru tak, podane łącze w kroku 3, aby zobaczyć, jak tworzenie i uruchamianie aplikacji przykładowej.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
  
## <a name="see-also"></a>Zobacz także
