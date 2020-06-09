---
title: Fabryka kanałów
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: 2aa44c4ef274fa548d490b0d8a648457a7b1e03b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600662"
---
# <a name="channel-factory"></a><span data-ttu-id="58b6b-102">Fabryka kanałów</span><span class="sxs-lookup"><span data-stu-id="58b6b-102">Channel Factory</span></span>

<span data-ttu-id="58b6b-103">Ten przykład pokazuje, jak aplikacja kliencka może utworzyć kanał z <xref:System.ServiceModel.ChannelFactory> klasą zamiast wygenerowanego klienta.</span><span class="sxs-lookup"><span data-stu-id="58b6b-103">This sample demonstrates how a client application can create a channel with the <xref:System.ServiceModel.ChannelFactory> class instead of a generated client.</span></span> <span data-ttu-id="58b6b-104">Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md) , który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="58b6b-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>

> [!NOTE]
> <span data-ttu-id="58b6b-105">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="58b6b-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="58b6b-106">Ten przykład używa <xref:System.ServiceModel.ChannelFactory%601> klasy w celu utworzenia kanału do punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="58b6b-106">This sample uses the <xref:System.ServiceModel.ChannelFactory%601> class to create a channel to a service endpoint.</span></span> <span data-ttu-id="58b6b-107">Zazwyczaj w celu utworzenia kanału w punkcie końcowym usługi wygenerowany typ klienta za pomocą narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) i Utwórz wystąpienie wygenerowanego typu.</span><span class="sxs-lookup"><span data-stu-id="58b6b-107">Typically, to create a channel to a service endpoint you generate a client type with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) and create an instance of the generated type.</span></span> <span data-ttu-id="58b6b-108">Kanał można również utworzyć za pomocą <xref:System.ServiceModel.ChannelFactory%601> klasy, jak pokazano w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="58b6b-108">You can also create a channel by using the <xref:System.ServiceModel.ChannelFactory%601> class, as demonstrated in this sample.</span></span> <span data-ttu-id="58b6b-109">Usługa utworzona przez następujący przykładowy kod jest taka sama jak usługa w [wprowadzenie](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="58b6b-109">The service created by the following sample code is identical to the service in the [Getting Started](getting-started-sample.md).</span></span>

```csharp
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
WSHttpBinding binding = new WSHttpBinding();
ChannelFactory<ICalculator> factory = new
                    ChannelFactory<ICalculator>(binding, address);
ICalculator channel = factory.CreateChannel();
```

> [!IMPORTANT]
> <span data-ttu-id="58b6b-110">Jeśli używasz tego przykładu w scenariuszu między maszynami, musisz zastąpić "localhost" w powyższym kodzie za pomocą w pełni kwalifikowanej nazwy komputera, na którym działa usługa.</span><span class="sxs-lookup"><span data-stu-id="58b6b-110">If you are running this sample in a cross-machine scenario, you must replace "localhost" in the preceding code with the fully-qualified name of the machine that is running the service.</span></span> <span data-ttu-id="58b6b-111">Ten przykład nie używa konfiguracji do ustawienia adresu punktu końcowego, dlatego należy to zrobić w kodzie.</span><span class="sxs-lookup"><span data-stu-id="58b6b-111">This sample does not use configuration to set the endpoint address, so this must be done in code.</span></span>

<span data-ttu-id="58b6b-112">Po utworzeniu kanału operacje usługi mogą być wywoływane tak samo jak z wygenerowanym klientem.</span><span class="sxs-lookup"><span data-stu-id="58b6b-112">Once the channel is created, service operations can be invoked just as with a generated client.</span></span>

```csharp
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = channel.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

<span data-ttu-id="58b6b-113">Aby zamknąć kanał, najpierw należy go rzutować do <xref:System.ServiceModel.IClientChannel> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="58b6b-113">To close the channel, it must first be cast to an <xref:System.ServiceModel.IClientChannel> interface.</span></span> <span data-ttu-id="58b6b-114">Wynika to z faktu, że kanał jako wygenerowany jest zadeklarowany w aplikacji klienckiej przy użyciu `ICalculator` interfejsu, który ma metody takie jak `Add` i, `Subtract` ale nie `Close` .</span><span class="sxs-lookup"><span data-stu-id="58b6b-114">This is because the channel as generated is declared in the client application using the `ICalculator` interface, which has methods like `Add` and `Subtract` but not `Close`.</span></span> <span data-ttu-id="58b6b-115">`Close`Metoda pochodzi z <xref:System.ServiceModel.ICommunicationObject> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="58b6b-115">The `Close` method originates on the <xref:System.ServiceModel.ICommunicationObject> interface.</span></span>

```csharp
// Close the channel.
 ((IClientChannel)client).Close();
```

<span data-ttu-id="58b6b-116">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="58b6b-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="58b6b-117">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć aplikację kliencką.</span><span class="sxs-lookup"><span data-stu-id="58b6b-117">Press ENTER in the client window to shut down the client application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="58b6b-118">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="58b6b-118">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="58b6b-119">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="58b6b-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="58b6b-120">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="58b6b-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span> <span data-ttu-id="58b6b-121">Należy zauważyć, że ten przykład nie umożliwia publikowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="58b6b-121">Note that this sample does not enable metadata publishing.</span></span> <span data-ttu-id="58b6b-122">Najpierw należy włączyć Publikowanie metadanych dla tego przykładu w celu ponownego wygenerowania typu klienta.</span><span class="sxs-lookup"><span data-stu-id="58b6b-122">You must first enable metadata publishing for this sample to regenerate the client type.</span></span>

3. <span data-ttu-id="58b6b-123">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="58b6b-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

### <a name="to-run-the-sample-cross-machine"></a><span data-ttu-id="58b6b-124">Aby uruchomić przykładową maszynę</span><span class="sxs-lookup"><span data-stu-id="58b6b-124">To run the sample cross machine</span></span>

1. <span data-ttu-id="58b6b-125">Zastąp wartość "localhost" w następującym kodzie z w pełni kwalifikowaną nazwą komputera, na którym działa usługa.</span><span class="sxs-lookup"><span data-stu-id="58b6b-125">Replace "localhost" in the following code with the fully-qualified name of the machine that is running the service.</span></span>

    ```csharp
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
    ```

> [!IMPORTANT]
> <span data-ttu-id="58b6b-126">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="58b6b-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="58b6b-127">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="58b6b-127">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="58b6b-128">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="58b6b-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="58b6b-129">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="58b6b-129">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`
