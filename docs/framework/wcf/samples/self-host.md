---
title: Host samodzielny
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
caps.latest.revision: "38"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dc1a25bcf6f840f2ad5939d812b23c56c7966d93
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="self-host"></a><span data-ttu-id="302e6-102">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="302e6-102">Self-Host</span></span>
<span data-ttu-id="302e6-103">W tym przykładzie pokazano, jak wdrożyć własny hostowanej usługi w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="302e6-103">This sample demonstrates how to implement a self-hosted service in a console application.</span></span> <span data-ttu-id="302e6-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="302e6-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="302e6-105">Pliku konfiguracji usługi zostało zmienione z pliku Web.config do pliku App.config i zmodyfikować, aby skonfigurować adres podstawowy, który korzysta z hosta.</span><span class="sxs-lookup"><span data-stu-id="302e6-105">The service configuration file has been renamed from Web.config to App.config and modified to configure a base address, which the host uses.</span></span> <span data-ttu-id="302e6-106">Kod źródłowy usługi został zmodyfikowany w celu wykonania statycznego `Main` funkcji, które tworzy i otwiera hosta usługi, która udostępnia skonfigurowany adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="302e6-106">The service source code has been modified to implement a static `Main` function that creates and opens a service host that provides the configured base address.</span></span> <span data-ttu-id="302e6-107">Implementacji usługi został zmodyfikowany w celu zapisywania danych wyjściowych do konsoli dla każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="302e6-107">The service implementation has been modified to write output to the console for each operation.</span></span> <span data-ttu-id="302e6-108">Klient został zostały zmodyfikowane, z wyjątkiem konfigurowania adresu właściwego punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="302e6-108">The client has been unmodified, except for configuring the correct endpoint address of the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="302e6-109">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="302e6-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="302e6-110">Próbki implementuje statycznej funkcji main utworzyć <xref:System.ServiceModel.ServiceHost> dla danego `CalculatorService` typ, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="302e6-110">The sample implements a static main function to create a <xref:System.ServiceModel.ServiceHost> for the given `CalculatorService` type, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="302e6-111">Gdy usługa jest obsługiwana w Internet Information Services (IIS) lub usługi aktywacji procesów systemu Windows (WAS), adres podstawowy usługi są udostępniane przez środowisko macierzyste.</span><span class="sxs-lookup"><span data-stu-id="302e6-111">When a service is hosted in Internet Information Services (IIS) or Windows Process Activation Service (WAS), the base address of the service is provided by the hosting environment.</span></span> <span data-ttu-id="302e6-112">W przypadku hostowania samoobsługowego należy określić adres podstawowy samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="302e6-112">In the self-hosted case, you must specify the base address yourself.</span></span> <span data-ttu-id="302e6-113">Odbywa się przy użyciu `add` element, podrzędny [ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), podrzędny [ \<hosta >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), podrzędny [ \<usługi > ](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) jak przedstawiono w następujących Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="302e6-113">This is done using the `add` element, child of [\<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), child of [\<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), child of [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) as demonstrated in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="302e6-114">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="302e6-114">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="302e6-115">Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="302e6-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="302e6-116">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="302e6-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="302e6-117">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="302e6-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="302e6-118">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="302e6-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="302e6-119">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="302e6-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="302e6-120">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="302e6-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="302e6-121">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="302e6-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="302e6-122">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="302e6-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="302e6-123">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="302e6-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a><span data-ttu-id="302e6-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="302e6-124">See Also</span></span>  
 [<span data-ttu-id="302e6-125">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="302e6-125">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
