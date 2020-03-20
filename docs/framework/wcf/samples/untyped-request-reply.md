---
title: Bez typu żądanie-odpowiedź
ms.date: 03/30/2017
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
ms.openlocfilehash: a526837b9bccf7a6287972e482a189a53ecadaf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183286"
---
# <a name="untyped-requestreply"></a>Nietypizowane żądanie/nietypizowana odpowiedź
W tym przykładzie pokazano, jak zdefiniować kontrakty operacji, które używają Message klasy.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Umowa serwisowa definiuje jedną operację, która przyjmuje typ wiadomości jako argument i zwraca komunikat. Operacja zbiera wszystkie wymagane dane do obliczenia sumy z treści wiadomości, a następnie wysyła sumę jako treść w komunikacie zwrotnym.  
  
```csharp
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 W usłudze operacja pobiera tablicę liczby całkowitych przekazanych w komunikacie wejściowym, a następnie oblicza sumę. Aby wysłać wiadomość odpowiedzi, przykład tworzy nową wiadomość z odpowiednią wersją wiadomości i Action i dodaje obliczoną sumę jako swoją treść. Poniższy przykładowy kod pokazuje to.  
  
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
  
 Klient używa kodu generowanego przez [narzędzie narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do utworzenia serwera proxy usługi zdalnej. Aby wysłać wiadomość żądania, klient musi mieć wersję wiadomości, która zależy od kanału źródłowego. W związku z <xref:System.ServiceModel.OperationContextScope> tym tworzy nowy zakres do kanału <xref:System.ServiceModel.OperationContext> proxy, który został utworzony, który tworzy z poprawną wersją wiadomości wypełnione w jego `OutgoingMessageHeaders.MessageVersion` właściwości. Klient przekazuje tablicę danych wejściowych jako treść do `ComputeSum` komunikatu żądania, a następnie wywołuje na serwerze proxy. Następnie klient pobiera sumę danych wejściowych, które `GetBody<T>` przeszedł, uzyskując dostęp do metody w wiadomości odpowiedzi. Poniższy przykładowy kod pokazuje to.  
  
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
  
 Ten przykład jest próbką hostowane w sieci Web i dlatego należy uruchomić tylko plik wykonywalny klienta. Poniżej przedstawiono przykładowe dane wyjściowe na kliencie.  
  
```console  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 Ten przykład jest próbką hostowane w sieci Web i tak sprawdź łącze podane w kroku 3, aby zobaczyć, jak skompilować i uruchomić przykład.  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
