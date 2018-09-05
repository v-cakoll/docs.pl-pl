---
title: Fabryka kanałów
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: 6bf0668c6b846671db12dc20465ee70137d70b35
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528875"
---
# <a name="channel-factory"></a><span data-ttu-id="9037a-102">Fabryka kanałów</span><span class="sxs-lookup"><span data-stu-id="9037a-102">Channel Factory</span></span>
<span data-ttu-id="9037a-103">Niniejszy przykład pokazuje, jak utworzyć aplikację kliencką kanału o <xref:System.ServiceModel.ChannelFactory> klasy zamiast wygenerowanego klienta.</span><span class="sxs-lookup"><span data-stu-id="9037a-103">This sample demonstrates how a client application can create a channel with the <xref:System.ServiceModel.ChannelFactory> class instead of a generated client.</span></span> <span data-ttu-id="9037a-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="9037a-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9037a-105">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="9037a-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9037a-106">W tym przykładzie użyto <xref:System.ServiceModel.ChannelFactory%601> klasy w celu utworzenia kanału do punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="9037a-106">This sample uses the <xref:System.ServiceModel.ChannelFactory%601> class to create a channel to a service endpoint.</span></span> <span data-ttu-id="9037a-107">Zazwyczaj próba utworzenia kanału do punktu końcowego usługi generowania typ klienta, za pomocą [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) i utworzyć wystąpienie typu wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="9037a-107">Typically, to create a channel to a service endpoint you generate a client type with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) and create an instance of the generated type.</span></span> <span data-ttu-id="9037a-108">Można również utworzyć kanał za pomocą <xref:System.ServiceModel.ChannelFactory%601> klasy, jak pokazano w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9037a-108">You can also create a channel by using the <xref:System.ServiceModel.ChannelFactory%601> class, as demonstrated in this sample.</span></span> <span data-ttu-id="9037a-109">Usługi utworzone przez następujący przykładowy kod jest identyczny z usługą w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="9037a-109">The service created by the following sample code is identical to the service in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
```csharp  
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
WSHttpBinding binding = new WSHttpBinding();  
ChannelFactory<ICalculator> factory = new   
                    ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = factory.CreateChannel();  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="9037a-110">Jeśli korzystasz z tego przykładu w scenariuszu między komputerami, musisz zastąpić "localhost" w poprzednim kodzie za pomocą w pełni kwalifikowana nazwa maszyny, na którym jest uruchomiona usługa.</span><span class="sxs-lookup"><span data-stu-id="9037a-110">If you are running this sample in a cross-machine scenario, you must replace "localhost" in the preceding code with the fully-qualified name of the machine that is running the service.</span></span> <span data-ttu-id="9037a-111">W tym przykładzie nie używa konfiguracji można ustawić adresu punktu końcowego, więc jest to niezbędne w kodzie.</span><span class="sxs-lookup"><span data-stu-id="9037a-111">This sample does not use configuration to set the endpoint address, so this must be done in code.</span></span>  
  
 <span data-ttu-id="9037a-112">Po utworzeniu kanału operacji usługi może być wywoływany podobnie jak w przypadku wygenerowanego klienta.</span><span class="sxs-lookup"><span data-stu-id="9037a-112">Once the channel is created, service operations can be invoked just as with a generated client.</span></span>  
  
```csharp  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
 <span data-ttu-id="9037a-113">Aby zamknąć okno kanał, jego musi najpierw można rzutować <xref:System.ServiceModel.IClientChannel> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9037a-113">To close the channel, it must first be cast to an <xref:System.ServiceModel.IClientChannel> interface.</span></span> <span data-ttu-id="9037a-114">Jest to spowodowane kanału, w miarę generowania jest zadeklarowana w aplikacji klienta przy użyciu `ICalculator` interfejs, który posiada metody takie jak `Add` i `Subtract` , ale nie `Close`.</span><span class="sxs-lookup"><span data-stu-id="9037a-114">This is because the channel as generated is declared in the client application using the `ICalculator` interface, which has methods like `Add` and `Subtract` but not `Close`.</span></span> <span data-ttu-id="9037a-115">`Close` Metody pochodzi z <xref:System.ServiceModel.ICommunicationObject> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9037a-115">The `Close` method originates on the <xref:System.ServiceModel.ICommunicationObject> interface.</span></span>  
  
```csharp  
// Close the channel.  
 ((IClientChannel)client).Close();  
```  
  
 <span data-ttu-id="9037a-116">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="9037a-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9037a-117">Naciśnij klawisz ENTER w oknie klienta do zamykania aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="9037a-117">Press ENTER in the client window to shut down the client application.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9037a-118">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="9037a-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9037a-119">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9037a-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9037a-120">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9037a-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="9037a-121">Należy pamiętać, że w tym przykładzie umożliwiają publikowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="9037a-121">Note that this sample does not enable metadata publishing.</span></span> <span data-ttu-id="9037a-122">Należy najpierw włączyć publikowanie metadanych dla tego przykładu ponownie wygenerować typu klienta.</span><span class="sxs-lookup"><span data-stu-id="9037a-122">You must first enable metadata publishing for this sample to regenerate the client type.</span></span>  
  
3.  <span data-ttu-id="9037a-123">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9037a-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-cross-machine"></a><span data-ttu-id="9037a-124">Aby uruchomić przykład krzyżowe maszyny</span><span class="sxs-lookup"><span data-stu-id="9037a-124">To run the sample cross machine</span></span>  
  
1.  <span data-ttu-id="9037a-125">Zastąp "localhost", w poniższym kodzie w pełni kwalifikowana nazwa maszyny, na którym jest uruchomiona usługa.</span><span class="sxs-lookup"><span data-stu-id="9037a-125">Replace "localhost" in the following code with the fully-qualified name of the machine that is running the service.</span></span>  
  
    ```csharp  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="9037a-126">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="9037a-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9037a-127">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="9037a-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9037a-128">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="9037a-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9037a-129">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="9037a-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  
  
## <a name="see-also"></a><span data-ttu-id="9037a-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9037a-130">See Also</span></span>
