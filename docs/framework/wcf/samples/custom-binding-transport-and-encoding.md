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
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="997da-102">Transport i kodowanie powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="997da-102">Custom Binding Transport and Encoding</span></span>
<span data-ttu-id="997da-103">Wiązanie niestandardowe jest zdefiniowana przez uporządkowaną listę elementów wiązania odrębny.</span><span class="sxs-lookup"><span data-stu-id="997da-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="997da-104">W tym przykładzie pokazano, jak skonfigurować niestandardowego powiązania z różnymi transport i kodowanie elementów komunikatu.</span><span class="sxs-lookup"><span data-stu-id="997da-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="997da-105">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="997da-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="997da-106">Ten przykład jest oparty na [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md)i został zmodyfikowany w celu konfigurowania trzech punktów końcowych do obsługi protokołu HTTP, TCP i nazwany potok transportów wiązań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="997da-106">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="997da-107">Podobnie modyfikacji konfiguracji klienta i zmienić kod klienta do komunikowania się z wszystkich trzech punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="997da-107">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="997da-108">Przykład pokazuje, jak skonfigurować niestandardowego powiązania, który obsługuje danego transportu i kodowanie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="997da-108">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="997da-109">Jest to osiągane przez konfigurowanie transport i kodowanie komunikatu `binding` elementu.</span><span class="sxs-lookup"><span data-stu-id="997da-109">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="997da-110">Kolejność elementów wiązania jest ważne podczas definiowania niestandardowego powiązania, ponieważ każdy reprezentuje warstwę stosu kanał (zobacz [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="997da-110">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="997da-111">Ten przykład konfiguruje trzy powiązania niestandardowe: protokół transportu HTTP z kodowaniem tekstu, transportu TCP za pomocą kodowania tekstu i transportu nazwany potok kodowania binarnego.</span><span class="sxs-lookup"><span data-stu-id="997da-111">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="997da-112">Konfiguracja usługi definiuje niestandardowego powiązania w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="997da-112">The service configuration defines the custom bindings as follows:</span></span>  
  
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
  
 <span data-ttu-id="997da-113">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="997da-113">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="997da-114">Klient komunikuje się z wszystkich trzech punktów końcowych, uzyskiwanie dostępu do pierwszego protokołu HTTP, a następnie TCP, a na końcu nazwany potok.</span><span class="sxs-lookup"><span data-stu-id="997da-114">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="997da-115">Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="997da-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="997da-116">`namedPipeTransport` Powiązania nie obsługuje operacji maszyny do komputera.</span><span class="sxs-lookup"><span data-stu-id="997da-116">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="997da-117">Jest on używany tylko do komunikacji na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="997da-117">It is used only for communication on the same machine.</span></span> <span data-ttu-id="997da-118">W związku z tym kiedy uruchomiona próbki w scenariuszu między komputerami, komentarz następujące wiersze w pliku kodu klienta:</span><span class="sxs-lookup"><span data-stu-id="997da-118">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
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
>  <span data-ttu-id="997da-119">Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="997da-119">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="997da-120">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="997da-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="997da-121">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="997da-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="997da-122">Tworzenie wersji języka C#, C++ lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="997da-122">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="997da-123">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="997da-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="997da-124">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="997da-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="997da-125">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="997da-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="997da-126">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="997da-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="997da-127">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="997da-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## <a name="see-also"></a><span data-ttu-id="997da-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="997da-128">See Also</span></span>
