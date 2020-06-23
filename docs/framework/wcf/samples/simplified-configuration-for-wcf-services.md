---
title: Uproszczona konfiguracja usług WCF
description: Dowiedz się, jak zaimplementować i skonfigurować typową usługę i klienta przy użyciu programu WCF. Usługa komunikuje się za pomocą punktu końcowego określonego w pliku konfiguracji.
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 46a0c878b29de34219413a508799ddaddf507dd8
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246223"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="dad4e-104">Uproszczona konfiguracja usług WCF</span><span class="sxs-lookup"><span data-stu-id="dad4e-104">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="dad4e-105">Ten przykład pokazuje, jak zaimplementować i skonfigurować typową usługę i klienta przy użyciu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="dad4e-105">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="dad4e-106">Ten przykład jest podstawą dla wszystkich innych podstawowych przykładów technologii.</span><span class="sxs-lookup"><span data-stu-id="dad4e-106">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="dad4e-107">Ta usługa, która udostępnia punkt końcowy do komunikacji z usługą, używa uproszczonej konfiguracji w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="dad4e-107">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in .NET Framework 4.</span></span> <span data-ttu-id="dad4e-108">Przed .NET Framework 4 punkt końcowy jest zwykle definiowany w pliku konfiguracji (Web.config), jak pokazano w poniższym przykładowym kodzie konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="dad4e-108">Prior to .NET Framework 4, the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="dad4e-109">W .NET Framework 4 `<service>` element jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="dad4e-109">In .NET Framework 4, the `<service>` element is optional.</span></span> <span data-ttu-id="dad4e-110">Gdy usługa nie definiuje żadnych punktów końcowych, do usługi są dodawane punkty końcowe dla każdego adresu podstawowego i zaimplementowanego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="dad4e-110">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="dad4e-111">Adres podstawowy jest dołączany do nazwy kontraktu w celu określenia punktu końcowego i powiązania jest określany przez schemat adresu.</span><span class="sxs-lookup"><span data-stu-id="dad4e-111">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="dad4e-112">Poniższy przykład kodu demonstruje uproszczony plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="dad4e-112">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="dad4e-113">Zgodnie z konfiguracją usługa może być dostępna `http://localhost/servicemodelsamples/service.svc` przez klienta programu na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="dad4e-113">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="dad4e-114">Aby klienci na komputerach zdalnych mogli uzyskać dostęp do usługi, należy określić w pełni kwalifikowaną nazwę domeny zamiast hosta lokalnego.</span><span class="sxs-lookup"><span data-stu-id="dad4e-114">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="dad4e-115">Usługa domyślnie nie uwidacznia metadanych.</span><span class="sxs-lookup"><span data-stu-id="dad4e-115">The service does not expose metadata by default.</span></span> <span data-ttu-id="dad4e-116">W związku z tym usługa włącza <xref:System.ServiceModel.Description.ServiceMetadataBehavior> zachowanie.</span><span class="sxs-lookup"><span data-stu-id="dad4e-116">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="dad4e-117">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="dad4e-117">To use this sample</span></span>  
  
1. <span data-ttu-id="dad4e-118">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dad4e-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="dad4e-119">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dad4e-119">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="dad4e-120">Uruchom przykład, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="dad4e-120">Run the sample by following these steps:</span></span>  
  
    1. <span data-ttu-id="dad4e-121">Kliknij prawym przyciskiem myszy projekt **usługi** i wybierz pozycję **Ustaw jako projekt startowy**, a następnie naciśnij **klawisze CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="dad4e-121">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2. <span data-ttu-id="dad4e-122">Poczekaj, aż dane wyjściowe konsoli potwierdzają, że usługa jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="dad4e-122">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3. <span data-ttu-id="dad4e-123">Kliknij prawym przyciskiem myszy projekt **klienta** i wybierz pozycję **Ustaw jako projekt startowy**, a następnie naciśnij **klawisze CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="dad4e-123">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dad4e-124">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="dad4e-124">The samples may already be installed on your computer.</span></span> <span data-ttu-id="dad4e-125">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="dad4e-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="dad4e-126">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="dad4e-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dad4e-127">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="dad4e-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="dad4e-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dad4e-128">See also</span></span>

- <span data-ttu-id="dad4e-129">[Przykłady zarządzania dla oprogramowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="dad4e-129">[AppFabric Management Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span></span>
- [<span data-ttu-id="dad4e-130">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="dad4e-130">Simplified Configuration</span></span>](../simplified-configuration.md)
