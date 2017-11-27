---
title: "Fabryka kanałów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6962cbbdd632ac9fa15253939ba2dad09eaf00de
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="channel-factory"></a><span data-ttu-id="94616-102">Fabryka kanałów</span><span class="sxs-lookup"><span data-stu-id="94616-102">Channel Factory</span></span>
<span data-ttu-id="94616-103">W tym przykładzie pokazano, jak utworzyć aplikację kliencką kanału o <xref:System.ServiceModel.ChannelFactory> klasy zamiast wygenerowanego klienta.</span><span class="sxs-lookup"><span data-stu-id="94616-103">This sample demonstrates how a client application can create a channel with the <xref:System.ServiceModel.ChannelFactory> class instead of a generated client.</span></span> <span data-ttu-id="94616-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="94616-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94616-105">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="94616-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="94616-106">W przykładzie użyto <xref:System.ServiceModel.ChannelFactory%601> klasy w celu utworzenia kanału dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="94616-106">This sample uses the <xref:System.ServiceModel.ChannelFactory%601> class to create a channel to a service endpoint.</span></span> <span data-ttu-id="94616-107">Zazwyczaj próba utworzenia kanału dla punktu końcowego generowania typ klienta z [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) i utworzyć wystąpienia typu wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="94616-107">Typically, to create a channel to a service endpoint you generate a client type with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) and create an instance of the generated type.</span></span> <span data-ttu-id="94616-108">Można również utworzyć kanał za pomocą <xref:System.ServiceModel.ChannelFactory%601> klasy, jak pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="94616-108">You can also create a channel by using the <xref:System.ServiceModel.ChannelFactory%601> class, as demonstrated in this sample.</span></span> <span data-ttu-id="94616-109">Usługa utworzony przez następujący przykładowy kod jest taki sam jak usługi w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="94616-109">The service created by the following sample code is identical to the service in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
```  
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
WSHttpBinding binding = new WSHttpBinding();  
ChannelFactory<ICalculator> factory = new   
                    ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = factory.CreateChannel();  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="94616-110">Jeśli korzystasz z tego przykładu w scenariuszu między komputerami, musisz zastąpić "localhost" w poprzednim kodzie pełną nazwę komputera, na którym jest uruchomiona usługa.</span><span class="sxs-lookup"><span data-stu-id="94616-110">If you are running this sample in a cross-machine scenario, you must replace "localhost" in the preceding code with the fully-qualified name of the machine that is running the service.</span></span> <span data-ttu-id="94616-111">W tym przykładzie nie korzysta z konfiguracji, aby ustawić adres punktu końcowego, tak aby to zrobić w kodzie.</span><span class="sxs-lookup"><span data-stu-id="94616-111">This sample does not use configuration to set the endpoint address, so this must be done in code.</span></span>  
  
 <span data-ttu-id="94616-112">Po utworzeniu kanału można wywołać operacji usługi, tak jak w przypadku wygenerowanego klienta.</span><span class="sxs-lookup"><span data-stu-id="94616-112">Once the channel is created, service operations can be invoked just as with a generated client.</span></span>  
  
```  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
 <span data-ttu-id="94616-113">Aby zamknąć kanał, jego musi najpierw można rzutować na <xref:System.ServiceModel.IClientChannel> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="94616-113">To close the channel, it must first be cast to an <xref:System.ServiceModel.IClientChannel> interface.</span></span> <span data-ttu-id="94616-114">Jest to spowodowane zadeklarowano kanału wygenerowane w aplikacji klienta przy użyciu `ICalculator` interfejs, który ma metody takie jak `Add` i `Subtract` , ale nie `Close`.</span><span class="sxs-lookup"><span data-stu-id="94616-114">This is because the channel as generated is declared in the client application using the `ICalculator` interface, which has methods like `Add` and `Subtract` but not `Close`.</span></span> <span data-ttu-id="94616-115">`Close` Metody pochodzi z <xref:System.ServiceModel.ICommunicationObject> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="94616-115">The `Close` method originates on the <xref:System.ServiceModel.ICommunicationObject> interface.</span></span>  
  
```  
// Close the channel.  
 ((IClientChannel)client).Close();  
```  
  
 <span data-ttu-id="94616-116">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="94616-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="94616-117">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="94616-117">Press ENTER in the client window to shut down the client application.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="94616-118">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="94616-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="94616-119">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="94616-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="94616-120">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="94616-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="94616-121">Należy pamiętać, że w tym przykładzie umożliwiają publikowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="94616-121">Note that this sample does not enable metadata publishing.</span></span> <span data-ttu-id="94616-122">Należy najpierw włączyć publikowanie metadanych dla tego przykładu, można ponownie wygenerować typu klienta.</span><span class="sxs-lookup"><span data-stu-id="94616-122">You must first enable metadata publishing for this sample to regenerate the client type.</span></span>  
  
3.  <span data-ttu-id="94616-123">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="94616-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-cross-machine"></a><span data-ttu-id="94616-124">Aby uruchomić przykład cross maszyny</span><span class="sxs-lookup"><span data-stu-id="94616-124">To run the sample cross machine</span></span>  
  
1.  <span data-ttu-id="94616-125">Zastąp wartość "localhost" w poniższym kodzie pełną nazwę komputera, na którym jest uruchomiona usługa.</span><span class="sxs-lookup"><span data-stu-id="94616-125">Replace "localhost" in the following code with the fully-qualified name of the machine that is running the service.</span></span>  
  
    ```  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="94616-126">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="94616-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="94616-127">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="94616-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="94616-128">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="94616-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="94616-129">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="94616-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  
  
## <a name="see-also"></a><span data-ttu-id="94616-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94616-130">See Also</span></span>
