---
title: Transport i kodowanie powiązań niestandardowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 47841b23dc3259aeb233192f396397745864d7ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145167"
---
# <a name="custom-binding-transport-and-encoding"></a>Transport i kodowanie powiązań niestandardowych
Powiązanie niestandardowe jest definiowane przez uporządkowaną listę dyskretnych elementów wiązania. W tym przykładzie pokazano, jak skonfigurować niestandardowe powiązanie z różnych elementów kodowania transportu i wiadomości.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład jest oparty na [hosta własnego](../../../../docs/framework/wcf/samples/self-host.md)i został zmodyfikowany w celu skonfigurowania trzech punktów końcowych do obsługi transportów HTTP, TCP i NamedPipe z niestandardowymi powiązaniami. Konfiguracja klienta została podobnie zmodyfikowana, a kod klienta został zmieniony w celu komunikowania się z każdym z trzech punktów końcowych.  
  
 Przykład pokazuje, jak skonfigurować niestandardowe powiązanie, które obsługuje określonego transportu i kodowania wiadomości. Jest to realizowane przez skonfigurowanie transportu i kodowania wiadomości dla `binding` elementu. Kolejność elementów wiązania jest ważna przy definiowaniu niestandardowego powiązania, ponieważ każdy reprezentuje warstwę w stosie kanałów (zobacz [Powiązania niestandardowe).](../../../../docs/framework/wcf/extending/custom-bindings.md) W tym przykładzie konfiguruje trzy powiązania niestandardowe: transport HTTP z kodowaniem tekstowym, transport TCP z kodowaniem tekstowym i transport NamedPipe z kodowaniem binarnym.  
  
 Konfiguracja usługi definiuje niestandardowe powiązania w następujący sposób:  
  
```xml  
<bindings>  
    <customBinding>  
        <binding name="HttpBinding" >  
            <textMessageEncoding
                messageVersion="Soap12Addressing10"/>  
            <httpTransport />  
        </binding>  
        <binding name="TcpBinding" >  
            <textMessageEncoding />  
            <tcpTransport />  
        </binding>  
        <binding name="NamedPipeBinding" >  
            <binaryMessageEncoding />  
            <namedPipeTransport />  
        </binding>  
    </customBinding>  
</bindings>  
```  
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane zarówno w oknie usługi, jak i konsoli klienta. Klient komunikuje się z każdym z trzech punktów końcowych, uzyskując dostęp najpierw HTTP, następnie TCP i na koniec NamedPipe. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.  
  
 Powiązanie `namedPipeTransport` nie obsługuje operacji między maszynami. Jest on używany tylko do komunikacji na tym samym komputerze. W związku z tym podczas uruchamiania próbki w scenariuszu między komputerami, skomentować następujące wiersze w pliku kodu klienta:  
  
```csharp  
CalculatorClient client = new CalculatorClient("default");  
Console.WriteLine("Communicate with named pipe endpoint.");  
// Call operations.  
DoCalculations(client);  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
```vb  
Dim client As New CalculatorClient("default")  
Console.WriteLine("Communicate with named pipe endpoint.")  
' call operations  
DoCalculations(client)  
'Closing the client gracefully closes the connection and cleans up resources  
client.Close()  
```  
  
> [!NOTE]
> Jeśli używasz Svcutil.exe do ponownego wygenerowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C#, C++ lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
