---
title: NetNamedPipeBinding
ms.date: 03/30/2017
helpviewer_keywords:
- Net Profile Named Pipe
ms.assetid: e78e845f-c325-46e2-927d-81616f97f7d5
ms.openlocfilehash: da54a835fd32efe4f53a80701465d2d7d8adba7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183462"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="c262f-102">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="c262f-102">NetNamedPipeBinding</span></span>
<span data-ttu-id="c262f-103">W tym przykładzie pokazano `netNamedPipeBinding` powiązania, który zapewnia komunikację między procesami na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c262f-103">This sample demonstrates the `netNamedPipeBinding` binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="c262f-104">Nazwane potoki nie działają na różnych komputerach.</span><span class="sxs-lookup"><span data-stu-id="c262f-104">Named pipes do not work across machines.</span></span> <span data-ttu-id="c262f-105">Ten przykład jest oparty na usłudze kalkulatora [wprowadzenie.](../../../../docs/framework/wcf/samples/getting-started-sample.md)</span><span class="sxs-lookup"><span data-stu-id="c262f-105">This sample is based on The [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) calculator service.</span></span>  
  
 <span data-ttu-id="c262f-106">W tym przykładzie usługa jest hostowana samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="c262f-106">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="c262f-107">Zarówno klient, jak i usługa są aplikacjami konsoli.</span><span class="sxs-lookup"><span data-stu-id="c262f-107">Both the client and the service are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c262f-108">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c262f-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c262f-109">Powiązanie jest określone w plikach konfiguracyjnych dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="c262f-109">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="c262f-110">Typ powiązania jest określony `binding` w atrybucie [ \<>punktu końcowego](../../configure-apps/file-schema/wcf/endpoint-element.md) lub [ \< \<> punktu końcowego](../../configure-apps/file-schema/wcf/endpoint-of-client.md) elementu>klienta, jak pokazano w następującej konfiguracji przykładowej:</span><span class="sxs-lookup"><span data-stu-id="c262f-110">The binding type is specified in the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) or [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element, as shown in the following sample configuration:</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="c262f-111">W poprzednim przykładzie pokazano, jak skonfigurować `netNamedPipeBinding` punkt końcowy do używania powiązania z ustawieniami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="c262f-111">The previous sample shows how to configure an endpoint to use the `netNamedPipeBinding` binding with the default settings.</span></span> <span data-ttu-id="c262f-112">Jeśli chcesz skonfigurować `netNamedPipeBinding` powiązanie i zmienić niektóre jego ustawienia, należy zdefiniować konfigurację powiązania.</span><span class="sxs-lookup"><span data-stu-id="c262f-112">If you want to configure the `netNamedPipeBinding` binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="c262f-113">Punkt końcowy musi odwoływać się do `bindingConfiguration` konfiguracji powiązania za pomocą nazwy z atrybutem.</span><span class="sxs-lookup"><span data-stu-id="c262f-113">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="c262f-114">W tym przykładzie konfiguracja `Binding1` wiązania ma nazwę i ma następującą definicję:</span><span class="sxs-lookup"><span data-stu-id="c262f-114">In this sample, the binding configuration is named `Binding1` and has the following definition:</span></span>  
  
```xml  
<bindings>  
  <!--   
        Following is the expanded configuration section for a NetNamedPipeBinding.  
        Each property is configured with the default value.  
     -->  
  <netNamedPipeBinding>  
    <binding name="Binding1"
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"  
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"
             maxBufferPoolSize="524288"  
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">  
      <security mode="Transport">  
        <transport protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netNamedPipeBinding>  
</bindings>  
```  
  
 <span data-ttu-id="c262f-115">Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="c262f-115">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c262f-116">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="c262f-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c262f-117">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="c262f-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c262f-118">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c262f-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c262f-119">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c262f-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c262f-120">Aby uruchomić przykład w konfiguracji pojedynczego komputera, postępuj zgodnie z instrukcjami w [uruchamianiu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c262f-120">To run the sample in a single machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c262f-121">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c262f-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c262f-122">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="c262f-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c262f-123">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="c262f-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c262f-124">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c262f-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\NamedPipe`  
