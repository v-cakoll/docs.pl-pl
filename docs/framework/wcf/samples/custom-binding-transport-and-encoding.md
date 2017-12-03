---
title: "Transport i kodowanie powiązań niestandardowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e4e26e332cc67fc462c703c502594a8a36758501
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="custom-binding-transport-and-encoding"></a>Transport i kodowanie powiązań niestandardowych
Wiązanie niestandardowe jest zdefiniowana przez uporządkowaną listę elementów wiązania odrębny. W tym przykładzie pokazano, jak skonfigurować niestandardowego powiązania z różnymi transport i kodowanie elementów komunikatu.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład jest oparty na [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md)i został zmodyfikowany w celu konfigurowania trzech punktów końcowych do obsługi protokołu HTTP, TCP i nazwany potok transportów wiązań niestandardowych. Podobnie modyfikacji konfiguracji klienta i zmienić kod klienta do komunikowania się z wszystkich trzech punktów końcowych.  
  
 Przykład pokazuje, jak skonfigurować niestandardowego powiązania, który obsługuje danego transportu i kodowanie komunikatu. Jest to osiągane przez konfigurowanie transport i kodowanie komunikatu `binding` elementu. Kolejność elementów wiązania jest ważne podczas definiowania niestandardowego powiązania, ponieważ każdy reprezentuje warstwę stosu kanał (zobacz [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md)). Ten przykład konfiguruje trzy powiązania niestandardowe: protokół transportu HTTP z kodowaniem tekstu, transportu TCP za pomocą kodowania tekstu i transportu nazwany potok kodowania binarnego.  
  
 Konfiguracja usługi definiuje niestandardowego powiązania w następujący sposób:  
  
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
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli usługi i klienta. Klient komunikuje się z wszystkich trzech punktów końcowych, uzyskiwanie dostępu do pierwszego protokołu HTTP, a następnie TCP, a na końcu nazwany potok. Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.  
  
 `namedPipeTransport` Powiązania nie obsługuje operacji maszyny do komputera. Jest on używany tylko do komunikacji na tym samym komputerze. W związku z tym kiedy uruchomiona próbki w scenariuszu między komputerami, komentarz następujące wiersze w pliku kodu klienta:  
  
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
>  Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kodu klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C#, C++ lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## <a name="see-also"></a>Zobacz też
