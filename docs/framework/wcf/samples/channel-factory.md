---
title: Fabryka kanałów
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: cd56c47223f0c98e48bd92376c9bbe9db6d2202e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045734"
---
# <a name="channel-factory"></a><span data-ttu-id="e6b97-102">Fabryka kanałów</span><span class="sxs-lookup"><span data-stu-id="e6b97-102">Channel Factory</span></span>

<span data-ttu-id="e6b97-103">Ten przykład pokazuje, <xref:System.ServiceModel.ChannelFactory> jak aplikacja kliencka może utworzyć kanał z klasą zamiast wygenerowanego klienta.</span><span class="sxs-lookup"><span data-stu-id="e6b97-103">This sample demonstrates how a client application can create a channel with the <xref:System.ServiceModel.ChannelFactory> class instead of a generated client.</span></span> <span data-ttu-id="e6b97-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="e6b97-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>

> [!NOTE]
> <span data-ttu-id="e6b97-105">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e6b97-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="e6b97-106">Ten przykład używa <xref:System.ServiceModel.ChannelFactory%601> klasy w celu utworzenia kanału do punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="e6b97-106">This sample uses the <xref:System.ServiceModel.ChannelFactory%601> class to create a channel to a service endpoint.</span></span> <span data-ttu-id="e6b97-107">Zazwyczaj w celu utworzenia kanału w punkcie końcowym usługi wygenerowany typ klienta za pomocą narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) i Utwórz wystąpienie wygenerowanego typu.</span><span class="sxs-lookup"><span data-stu-id="e6b97-107">Typically, to create a channel to a service endpoint you generate a client type with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) and create an instance of the generated type.</span></span> <span data-ttu-id="e6b97-108">Kanał można również utworzyć za pomocą <xref:System.ServiceModel.ChannelFactory%601> klasy, jak pokazano w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e6b97-108">You can also create a channel by using the <xref:System.ServiceModel.ChannelFactory%601> class, as demonstrated in this sample.</span></span> <span data-ttu-id="e6b97-109">Usługa utworzona przez następujący przykładowy kod jest taka sama jak usługa w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e6b97-109">The service created by the following sample code is identical to the service in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>

```csharp
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
WSHttpBinding binding = new WSHttpBinding();
ChannelFactory<ICalculator> factory = new
                    ChannelFactory<ICalculator>(binding, address);
ICalculator channel = factory.CreateChannel();
```

> [!IMPORTANT]
> <span data-ttu-id="e6b97-110">Jeśli używasz tego przykładu w scenariuszu między maszynami, musisz zastąpić "localhost" w powyższym kodzie za pomocą w pełni kwalifikowanej nazwy komputera, na którym działa usługa.</span><span class="sxs-lookup"><span data-stu-id="e6b97-110">If you are running this sample in a cross-machine scenario, you must replace "localhost" in the preceding code with the fully-qualified name of the machine that is running the service.</span></span> <span data-ttu-id="e6b97-111">Ten przykład nie używa konfiguracji do ustawienia adresu punktu końcowego, dlatego należy to zrobić w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e6b97-111">This sample does not use configuration to set the endpoint address, so this must be done in code.</span></span>

<span data-ttu-id="e6b97-112">Po utworzeniu kanału operacje usługi mogą być wywoływane tak samo jak z wygenerowanym klientem.</span><span class="sxs-lookup"><span data-stu-id="e6b97-112">Once the channel is created, service operations can be invoked just as with a generated client.</span></span>

```csharp
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = channel.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

<span data-ttu-id="e6b97-113">Aby zamknąć kanał, najpierw należy go rzutować do <xref:System.ServiceModel.IClientChannel> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e6b97-113">To close the channel, it must first be cast to an <xref:System.ServiceModel.IClientChannel> interface.</span></span> <span data-ttu-id="e6b97-114">Wynika to z faktu, że kanał jako wygenerowany jest zadeklarowany w aplikacji `ICalculator` klienckiej przy użyciu interfejsu, `Add` który ma metody `Close`takie jak i, `Subtract` ale nie.</span><span class="sxs-lookup"><span data-stu-id="e6b97-114">This is because the channel as generated is declared in the client application using the `ICalculator` interface, which has methods like `Add` and `Subtract` but not `Close`.</span></span> <span data-ttu-id="e6b97-115">`Close` Metoda pochodzi<xref:System.ServiceModel.ICommunicationObject> z interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e6b97-115">The `Close` method originates on the <xref:System.ServiceModel.ICommunicationObject> interface.</span></span>

```csharp
// Close the channel.
 ((IClientChannel)client).Close();
```

<span data-ttu-id="e6b97-116">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="e6b97-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e6b97-117">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć aplikację kliencką.</span><span class="sxs-lookup"><span data-stu-id="e6b97-117">Press ENTER in the client window to shut down the client application.</span></span>

```
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e6b97-118">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="e6b97-118">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="e6b97-119">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e6b97-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="e6b97-120">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e6b97-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="e6b97-121">Należy zauważyć, że ten przykład nie umożliwia publikowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="e6b97-121">Note that this sample does not enable metadata publishing.</span></span> <span data-ttu-id="e6b97-122">Najpierw należy włączyć Publikowanie metadanych dla tego przykładu w celu ponownego wygenerowania typu klienta.</span><span class="sxs-lookup"><span data-stu-id="e6b97-122">You must first enable metadata publishing for this sample to regenerate the client type.</span></span>

3. <span data-ttu-id="e6b97-123">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e6b97-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-cross-machine"></a><span data-ttu-id="e6b97-124">Aby uruchomić przykładową maszynę</span><span class="sxs-lookup"><span data-stu-id="e6b97-124">To run the sample cross machine</span></span>

1. <span data-ttu-id="e6b97-125">Zastąp wartość "localhost" w następującym kodzie z w pełni kwalifikowaną nazwą komputera, na którym działa usługa.</span><span class="sxs-lookup"><span data-stu-id="e6b97-125">Replace "localhost" in the following code with the fully-qualified name of the machine that is running the service.</span></span>

    ```csharp
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
    ```

> [!IMPORTANT]
> <span data-ttu-id="e6b97-126">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e6b97-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e6b97-127">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="e6b97-127">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e6b97-128">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="e6b97-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e6b97-129">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e6b97-129">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`
