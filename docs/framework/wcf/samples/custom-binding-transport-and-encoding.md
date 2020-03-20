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
# <a name="custom-binding-transport-and-encoding"></a><span data-ttu-id="d46b4-102">Transport i kodowanie powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="d46b4-102">Custom Binding Transport and Encoding</span></span>
<span data-ttu-id="d46b4-103">Powiązanie niestandardowe jest definiowane przez uporządkowaną listę dyskretnych elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="d46b4-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="d46b4-104">W tym przykładzie pokazano, jak skonfigurować niestandardowe powiązanie z różnych elementów kodowania transportu i wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d46b4-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d46b4-105">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d46b4-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d46b4-106">Ten przykład jest oparty na [hosta własnego](../../../../docs/framework/wcf/samples/self-host.md)i został zmodyfikowany w celu skonfigurowania trzech punktów końcowych do obsługi transportów HTTP, TCP i NamedPipe z niestandardowymi powiązaniami.</span><span class="sxs-lookup"><span data-stu-id="d46b4-106">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md), and has been modified to configure three endpoints to support HTTP, TCP, and NamedPipe transports with custom bindings.</span></span> <span data-ttu-id="d46b4-107">Konfiguracja klienta została podobnie zmodyfikowana, a kod klienta został zmieniony w celu komunikowania się z każdym z trzech punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="d46b4-107">The client configuration was similarly modified, and the client code changed to communicate with each of the three endpoints.</span></span>  
  
 <span data-ttu-id="d46b4-108">Przykład pokazuje, jak skonfigurować niestandardowe powiązanie, które obsługuje określonego transportu i kodowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d46b4-108">The sample demonstrates a how to configure a custom binding that supports a particular transport and message encoding.</span></span> <span data-ttu-id="d46b4-109">Jest to realizowane przez skonfigurowanie transportu i kodowania wiadomości dla `binding` elementu.</span><span class="sxs-lookup"><span data-stu-id="d46b4-109">This is accomplished by configuring a transport and a message encoding for the `binding` element.</span></span> <span data-ttu-id="d46b4-110">Kolejność elementów wiązania jest ważna przy definiowaniu niestandardowego powiązania, ponieważ każdy reprezentuje warstwę w stosie kanałów (zobacz [Powiązania niestandardowe).](../../../../docs/framework/wcf/extending/custom-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d46b4-110">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="d46b4-111">W tym przykładzie konfiguruje trzy powiązania niestandardowe: transport HTTP z kodowaniem tekstowym, transport TCP z kodowaniem tekstowym i transport NamedPipe z kodowaniem binarnym.</span><span class="sxs-lookup"><span data-stu-id="d46b4-111">This sample configures three custom bindings: an HTTP transport with text encoding, a TCP transport with text encoding, and a NamedPipe transport with a binary encoding.</span></span>  
  
 <span data-ttu-id="d46b4-112">Konfiguracja usługi definiuje niestandardowe powiązania w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d46b4-112">The service configuration defines the custom bindings as follows:</span></span>  
  
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
  
 <span data-ttu-id="d46b4-113">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane zarówno w oknie usługi, jak i konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="d46b4-113">When you run the sample, the operation requests and responses are displayed in both the service and client console window.</span></span> <span data-ttu-id="d46b4-114">Klient komunikuje się z każdym z trzech punktów końcowych, uzyskując dostęp najpierw HTTP, następnie TCP i na koniec NamedPipe.</span><span class="sxs-lookup"><span data-stu-id="d46b4-114">The client communicates with each of the three endpoints, accessing first HTTP, then TCP, and finally NamedPipe.</span></span> <span data-ttu-id="d46b4-115">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="d46b4-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="d46b4-116">Powiązanie `namedPipeTransport` nie obsługuje operacji między maszynami.</span><span class="sxs-lookup"><span data-stu-id="d46b4-116">The `namedPipeTransport` binding does not support machine-to-machine operations.</span></span> <span data-ttu-id="d46b4-117">Jest on używany tylko do komunikacji na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d46b4-117">It is used only for communication on the same machine.</span></span> <span data-ttu-id="d46b4-118">W związku z tym podczas uruchamiania próbki w scenariuszu między komputerami, skomentować następujące wiersze w pliku kodu klienta:</span><span class="sxs-lookup"><span data-stu-id="d46b4-118">Therefore, when running the sample in a cross-machine scenario, comment out the following lines in the client code file:</span></span>  
  
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
> <span data-ttu-id="d46b4-119">Jeśli używasz Svcutil.exe do ponownego wygenerowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.</span><span class="sxs-lookup"><span data-stu-id="d46b4-119">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d46b4-120">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="d46b4-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d46b4-121">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d46b4-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d46b4-122">Aby utworzyć wersję C#, C++ lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d46b4-122">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d46b4-123">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d46b4-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d46b4-124">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d46b4-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d46b4-125">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="d46b4-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d46b4-126">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="d46b4-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d46b4-127">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d46b4-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
