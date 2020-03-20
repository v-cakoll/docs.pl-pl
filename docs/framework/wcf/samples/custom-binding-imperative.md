---
title: Powiązanie niestandardowe imperatywne
ms.date: 03/30/2017
ms.assetid: 6e13bf96-5de0-4476-b646-5f150774418d
ms.openlocfilehash: 90126720beea2cf9742724b24f5889dd6d554200
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145322"
---
# <a name="custom-binding-imperative"></a><span data-ttu-id="752c2-102">Powiązanie niestandardowe imperatywne</span><span class="sxs-lookup"><span data-stu-id="752c2-102">Custom Binding Imperative</span></span>
<span data-ttu-id="752c2-103">Przykład pokazuje, jak napisać kod imperatywny do definiowania i używania niestandardowych powiązań bez użycia pliku konfiguracji lub klienta generowanego przez Program Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="752c2-103">The sample demonstrates how to write imperative code to define and use custom bindings without using a configuration file or a Windows Communication Foundation (WCF) generated client.</span></span> <span data-ttu-id="752c2-104">Ten przykład łączy funkcje dostarczane przez transport HTTP i niezawodny kanał sesji, aby utworzyć niezawodne powiązanie oparte na protoko.</span><span class="sxs-lookup"><span data-stu-id="752c2-104">This sample combines the features provided by the HTTP transport and the reliable session channel to create a reliable HTTP-based binding.</span></span> <span data-ttu-id="752c2-105">Ten przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="752c2-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="752c2-106">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="752c2-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="752c2-107">Zarówno na kliencie, jak i w usłudze tworzone jest niestandardowe powiązanie, które zawiera dwa elementy wiązania (niezawodna sesja i HTTP):</span><span class="sxs-lookup"><span data-stu-id="752c2-107">On both the client and the service, a custom binding is created that contains two binding elements (Reliable Session and HTTP):</span></span>  

```csharp
ReliableSessionBindingElement reliableSession = new ReliableSessionBindingElement();  
reliableSession.Ordered = true;  
  
HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();  
httpTransport.AuthenticationScheme = System.Net.AuthenticationSchemes.Anonymous;  
httpTransport.HostNameComparisonMode = HostNameComparisonMode.StrongWildcard;  
  
CustomBinding binding = new CustomBinding(reliableSession, httpTransport);  
```
  
 <span data-ttu-id="752c2-108">W usłudze powiązanie jest używane przez dodanie punktu końcowego do ServiceHost:</span><span class="sxs-lookup"><span data-stu-id="752c2-108">On the service, the binding is used by adding an endpoint to the ServiceHost:</span></span>  

```csharp
serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, "");  
```

 <span data-ttu-id="752c2-109">Na kliencie powiązanie jest <xref:System.ServiceModel.ChannelFactory> używane przez a do utworzenia kanału do usługi:</span><span class="sxs-lookup"><span data-stu-id="752c2-109">On the client, the binding is used by a <xref:System.ServiceModel.ChannelFactory> to create a channel to the service:</span></span>  

```csharp
EndpointAddress address = new EndpointAddress("http://localhost:8000/servicemodelsamples/service");  
ChannelFactory<ICalculator> channelFactory = new ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = channelFactory.CreateChannel();  
```

 <span data-ttu-id="752c2-110">Ten kanał jest następnie używany do interakcji z usługą:</span><span class="sxs-lookup"><span data-stu-id="752c2-110">This channel is then used to interact with the service:</span></span>  

```csharp
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```

 <span data-ttu-id="752c2-111">Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="752c2-111">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="752c2-112">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="752c2-112">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="752c2-113">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="752c2-113">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="752c2-114">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="752c2-114">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="752c2-115">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="752c2-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="752c2-116">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="752c2-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="752c2-117">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="752c2-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="752c2-118">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="752c2-118">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="752c2-119">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="752c2-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="752c2-120">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="752c2-120">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Custom\Imperative`  
  
## <a name="see-also"></a><span data-ttu-id="752c2-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="752c2-121">See also</span></span>

- [<span data-ttu-id="752c2-122">Niestandardowe przykłady powiązania</span><span class="sxs-lookup"><span data-stu-id="752c2-122">Custom Binding Samples</span></span>](custom-binding.md)
