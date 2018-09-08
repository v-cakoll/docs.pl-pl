---
title: Powiązanie niestandardowe imperatywne
ms.date: 03/30/2017
ms.assetid: 6e13bf96-5de0-4476-b646-5f150774418d
ms.openlocfilehash: dac98d2c08a207019b9ec5b18340afc02e62f836
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44196468"
---
# <a name="custom-binding-imperative"></a><span data-ttu-id="47dcf-102">Powiązanie niestandardowe imperatywne</span><span class="sxs-lookup"><span data-stu-id="47dcf-102">Custom Binding Imperative</span></span>
<span data-ttu-id="47dcf-103">W przykładzie pokazano sposób pisania kodu imperatywnego do definiowania i używania powiązań niestandardowych bez przy użyciu pliku konfiguracji lub klienta generowany Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="47dcf-103">The sample demonstrates how to write imperative code to define and use custom bindings without using a configuration file or a Windows Communication Foundation (WCF) generated client.</span></span> <span data-ttu-id="47dcf-104">W tym przykładzie to połączenie funkcji oferowanych przez transportu HTTP i kanał niezawodnej sesji, aby utworzyć niezawodne powiązania oparty na protokole HTTP.</span><span class="sxs-lookup"><span data-stu-id="47dcf-104">This sample combines the features provided by the HTTP transport and the reliable session channel to create a reliable HTTP-based binding.</span></span> <span data-ttu-id="47dcf-105">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="47dcf-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47dcf-106">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="47dcf-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="47dcf-107">Na kliencie oraz usługi utworzono niestandardowego powiązania, która zawiera dwa elementy wiązania (niezawodnej sesji i HTTP):</span><span class="sxs-lookup"><span data-stu-id="47dcf-107">On both the client and the service, a custom binding is created that contains two binding elements (Reliable Session and HTTP):</span></span>  

```csharp
ReliableSessionBindingElement reliableSession = new ReliableSessionBindingElement();  
reliableSession.Ordered = true;  
  
HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();  
httpTransport.AuthenticationScheme = System.Net.AuthenticationSchemes.Anonymous;  
httpTransport.HostNameComparisonMode = HostNameComparisonMode.StrongWildcard;  
  
CustomBinding binding = new CustomBinding(reliableSession, httpTransport);  
```
  
 <span data-ttu-id="47dcf-108">W usłudze powiązania jest używany przez dodanie punktu końcowego do elementu ServiceHost:</span><span class="sxs-lookup"><span data-stu-id="47dcf-108">On the service, the binding is used by adding an endpoint to the ServiceHost:</span></span>  

```csharp
serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, "");  
```

 <span data-ttu-id="47dcf-109">Na komputerze klienckim, powiązania jest używany przez <xref:System.ServiceModel.ChannelFactory> próba utworzenia kanału do usługi:</span><span class="sxs-lookup"><span data-stu-id="47dcf-109">On the client, the binding is used by a <xref:System.ServiceModel.ChannelFactory> to create a channel to the service:</span></span>  

```csharp
EndpointAddress address = new EndpointAddress("http://localhost:8000/servicemodelsamples/service");  
ChannelFactory<ICalculator> channelFactory = new ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = channelFactory.CreateChannel();  
```

 <span data-ttu-id="47dcf-110">Ten kanał jest następnie używany do interakcji z usługą:</span><span class="sxs-lookup"><span data-stu-id="47dcf-110">This channel is then used to interact with the service:</span></span>  

```csharp
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```

 <span data-ttu-id="47dcf-111">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="47dcf-111">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="47dcf-112">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="47dcf-112">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="47dcf-113">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="47dcf-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="47dcf-114">Pamiętaj, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="47dcf-114">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="47dcf-115">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="47dcf-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="47dcf-116">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="47dcf-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="47dcf-117">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="47dcf-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="47dcf-118">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="47dcf-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="47dcf-119">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="47dcf-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="47dcf-120">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="47dcf-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Custom\Imperative`  
  
## <a name="see-also"></a><span data-ttu-id="47dcf-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47dcf-121">See Also</span></span>  
 [<span data-ttu-id="47dcf-122">Powiązanie niestandardowe</span><span class="sxs-lookup"><span data-stu-id="47dcf-122">Custom Binding</span></span>](https://msdn.microsoft.com/library/657e8143-beb0-472d-9cfe-ed1a19c2ab08)
