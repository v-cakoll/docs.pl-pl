---
title: Host samodzielny
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: a38738c369db3d3f8242bd71ee04a19a669b2cf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144152"
---
# <a name="self-host"></a><span data-ttu-id="42608-102">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="42608-102">Self-Host</span></span>
<span data-ttu-id="42608-103">W tym przykładzie pokazano, jak zaimplementować usługę hostowane samodzielnie w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="42608-103">This sample demonstrates how to implement a self-hosted service in a console application.</span></span> <span data-ttu-id="42608-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="42608-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="42608-105">Nazwa pliku konfiguracji usługi została zmieniona z witryny Web.config na App.config i zmodyfikowana w celu skonfigurowania adresu podstawowego, którego używa host.</span><span class="sxs-lookup"><span data-stu-id="42608-105">The service configuration file has been renamed from Web.config to App.config and modified to configure a base address, which the host uses.</span></span> <span data-ttu-id="42608-106">Kod źródłowy usługi został zmodyfikowany w `Main` celu zaimplementowania funkcji statycznej, która tworzy i otwiera hosta usługi, który udostępnia skonfigurowany adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="42608-106">The service source code has been modified to implement a static `Main` function that creates and opens a service host that provides the configured base address.</span></span> <span data-ttu-id="42608-107">Implementacja usługi została zmodyfikowana w celu zapisania danych wyjściowych w konsoli dla każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="42608-107">The service implementation has been modified to write output to the console for each operation.</span></span> <span data-ttu-id="42608-108">Klient został niezmodyfikowany, z wyjątkiem konfigurowania poprawnego adresu punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="42608-108">The client has been unmodified, except for configuring the correct endpoint address of the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42608-109">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="42608-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="42608-110">Przykład implementuje statyczną funkcję główną, aby utworzyć <xref:System.ServiceModel.ServiceHost> dla danego `CalculatorService` typu, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="42608-110">The sample implements a static main function to create a <xref:System.ServiceModel.ServiceHost> for the given `CalculatorService` type, as shown in the following sample code.</span></span>  
  
```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost =
           new ServiceHost(typeof(CalculatorService)))  
    {  
        // Open the ServiceHost to create listeners
        // and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```  
  
 <span data-ttu-id="42608-111">Gdy usługa jest hostowana w internetowych usługach informacyjnych (IIS) lub usłudze aktywacji procesów systemu Windows (WAS), adres podstawowy usługi jest dostarczany przez środowisko hostingowe.</span><span class="sxs-lookup"><span data-stu-id="42608-111">When a service is hosted in Internet Information Services (IIS) or Windows Process Activation Service (WAS), the base address of the service is provided by the hosting environment.</span></span> <span data-ttu-id="42608-112">W przypadku hostowane samodzielnie należy określić adres podstawowy samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="42608-112">In the self-hosted case, you must specify the base address yourself.</span></span> <span data-ttu-id="42608-113">Odbywa się to `add` przy użyciu elementu, podrzędny [ \<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), podrzędny [ \<>hosta ](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), element podrzędny [ \<usługi>,](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="42608-113">This is done using the `add` element, child of [\<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), child of [\<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), child of [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
  ...  
</service>  
```  
  
 <span data-ttu-id="42608-114">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="42608-114">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="42608-115">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="42608-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="42608-116">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="42608-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="42608-117">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="42608-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="42608-118">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="42608-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="42608-119">Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="42608-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="42608-120">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="42608-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="42608-121">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="42608-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="42608-122">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="42608-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="42608-123">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="42608-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a><span data-ttu-id="42608-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42608-124">See also</span></span>

- <span data-ttu-id="42608-125">[AppFabric Hosting i trwałość przykłady](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="42608-125">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
