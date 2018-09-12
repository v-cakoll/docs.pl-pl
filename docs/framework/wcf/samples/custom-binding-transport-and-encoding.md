---
title: Transport i kodowanie powiązań niestandardowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: ee15fd37390f8bf4ca3bc287f9a3dbd5f8ebd935
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44508639"
---
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="f42ab-102">Transport i kodowanie powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="f42ab-102">Custom Binding Transport and Encoding</span></span>
<span data-ttu-id="f42ab-103">Powiązanie niestandardowe jest definiowany przez uporządkowaną listą elementy powiązania dyskretnych.</span><span class="sxs-lookup"><span data-stu-id="f42ab-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="f42ab-104">Niniejszy przykład pokazuje, jak skonfigurować powiązania niestandardowego z różnymi transport i kodowanie elementów wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f42ab-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f42ab-105">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="f42ab-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f42ab-106">Ten przykład jest oparty na [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md)i została zmodyfikowana, aby skonfigurować trzy punkty końcowe do obsługi protokołu HTTP, TCP i nazwany potok transportów powiązań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="f42ab-106">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="f42ab-107">Podobnie modyfikacji konfiguracji klienta, a następnie zmienić kodu klienta do komunikowania się z każdym z trzech punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="f42ab-107">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="f42ab-108">W przykładzie pokazano, jak skonfigurować niestandardowe powiązanie, które obsługuje danego transportu i kodowanie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f42ab-108">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="f42ab-109">Jest to realizowane przez skonfigurowanie transport i kodowanie komunikatu `binding` elementu.</span><span class="sxs-lookup"><span data-stu-id="f42ab-109">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="f42ab-110">Określanie kolejności elementów wiązania jest ważny w celu definiowania niestandardowego powiązania, ponieważ każdy z nich reprezentuje warstwę w stosie kanału (zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="f42ab-110">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="f42ab-111">Ten przykład umożliwia skonfigurowanie trzy powiązań niestandardowych: protokół transportu HTTP przy użyciu kodowania tekstu, warstwy transportowej TCP za pomocą kodowania tekstu i transport nazwany potok przy użyciu kodowania binarnego.</span><span class="sxs-lookup"><span data-stu-id="f42ab-111">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="f42ab-112">Konfiguracja usługi definiuje powiązań niestandardowych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f42ab-112">The service configuration defines the custom bindings as follows:</span></span>  
  
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
  
 <span data-ttu-id="f42ab-113">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="f42ab-113">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="f42ab-114">Klient komunikuje się z każdym z trzech punktów końcowych, uzyskiwanie dostępu do pierwszego HTTP, a następnie TCP, a na końcu nazwany potok.</span><span class="sxs-lookup"><span data-stu-id="f42ab-114">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="f42ab-115">Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="f42ab-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="f42ab-116">`namedPipeTransport` Powiązanie nie obsługuje operacji od maszyny.</span><span class="sxs-lookup"><span data-stu-id="f42ab-116">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="f42ab-117">Jest on używany tylko do komunikacji na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f42ab-117">It is used only for communication on the same machine.</span></span> <span data-ttu-id="f42ab-118">W związku z tym gdy działa aplikacja przykładowa w scenariuszu między komputerami, jako komentarz następujące wiersze w pliku kodu klienta:</span><span class="sxs-lookup"><span data-stu-id="f42ab-118">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
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
>  <span data-ttu-id="f42ab-119">Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.</span><span class="sxs-lookup"><span data-stu-id="f42ab-119">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f42ab-120">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="f42ab-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f42ab-121">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f42ab-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f42ab-122">Aby kompilować rozwiązania w wersji języka C#, C++ lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f42ab-122">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="f42ab-123">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f42ab-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f42ab-124">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f42ab-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f42ab-125">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="f42ab-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f42ab-126">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="f42ab-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f42ab-127">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f42ab-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## <a name="see-also"></a><span data-ttu-id="f42ab-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f42ab-128">See Also</span></span>
