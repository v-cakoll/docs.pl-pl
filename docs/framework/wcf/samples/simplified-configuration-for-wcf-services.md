---
title: "Uproszczona konfiguracja usług WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02611dc44b98c1b8b5ef5ae74559f9f370483792
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="ea144-102">Uproszczona konfiguracja usług WCF</span><span class="sxs-lookup"><span data-stu-id="ea144-102">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="ea144-103">W tym przykładzie pokazano, jak wdrożyć i skonfigurować typowe usługi i klienta przy użyciu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ea144-103">This sample demonstrates how to implement and configure a typical service and client using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="ea144-104">W tym przykładzie stanowi podstawę dla wszystkich innych przykładów podstawową technologię.</span><span class="sxs-lookup"><span data-stu-id="ea144-104">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="ea144-105">Uproszczona konfiguracja w korzysta z tej usługi, który udostępnia punktu końcowego w celu komunikowania się z usługą, [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ea144-105">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span></span> <span data-ttu-id="ea144-106">Przed [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], punkt końcowy jest zazwyczaj definiowane w pliku konfiguracyjnym (Web.config), jak pokazano w poniższym kodzie konfiguracji przykład.</span><span class="sxs-lookup"><span data-stu-id="ea144-106">Prior to [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
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
  
 <span data-ttu-id="ea144-107">W [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], `<service>` element jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ea144-107">In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the `<service>` element is optional.</span></span> <span data-ttu-id="ea144-108">Jeśli usługi nie definiuje żadnych punktów końcowych, dla każdego adresu podstawowego i zaimplementowana kontraktu punktu końcowego są dodawane do usługi.</span><span class="sxs-lookup"><span data-stu-id="ea144-108">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="ea144-109">Adres podstawowy jest dołączany do nazwy kontraktu, aby ustalić punktu końcowego i powiązania jest określany przez schemat adresów.</span><span class="sxs-lookup"><span data-stu-id="ea144-109">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="ea144-110">W poniższym przykładzie przedstawiono plik konfiguracji uproszczone.</span><span class="sxs-lookup"><span data-stu-id="ea144-110">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="ea144-111">Zgodnie z konfiguracją, usługi są dostępne w http://localhost/servicemodelsamples/service.svc przez klienta na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ea144-111">As configured, the service can be accessed at http://localhost/servicemodelsamples/service.svc by a client on the same computer.</span></span> <span data-ttu-id="ea144-112">Dla klientów na komputerach zdalnych do uzyskania dostępu do usługi należy określić w pełni kwalifikowanej nazwy domeny zamiast nazwy localhost.</span><span class="sxs-lookup"><span data-stu-id="ea144-112">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="ea144-113">Domyślnie usługa nie uwidacznia metadanych.</span><span class="sxs-lookup"><span data-stu-id="ea144-113">The service does not expose metadata by default.</span></span> <span data-ttu-id="ea144-114">W efekcie usługa włącza <xref:System.ServiceModel.Description.ServiceMetadataBehavior> zachowanie.</span><span class="sxs-lookup"><span data-stu-id="ea144-114">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
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
  
### <a name="to-use-this-sample"></a><span data-ttu-id="ea144-115">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="ea144-115">To use this sample</span></span>  
  
1.  <span data-ttu-id="ea144-116">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ea144-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ea144-117">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ea144-117">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ea144-118">Uruchom próbkę, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ea144-118">Run the sample by following these steps:</span></span>  
  
    1.  <span data-ttu-id="ea144-119">Kliknij prawym przyciskiem myszy **usługi** projekt i wybierz **Ustaw jako projekt startowy**, naciśnij klawisz **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="ea144-119">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2.  <span data-ttu-id="ea144-120">Poczekaj na dane wyjściowe konsoli potwierdzenie, że usługa działa i uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="ea144-120">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3.  <span data-ttu-id="ea144-121">Kliknij prawym przyciskiem myszy **klienta** projekt i wybierz **Ustaw jako projekt startowy**, naciśnij klawisz **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="ea144-121">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ea144-122">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ea144-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ea144-123">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="ea144-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ea144-124">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="ea144-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ea144-125">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ea144-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="ea144-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea144-126">See Also</span></span>  
 [<span data-ttu-id="ea144-127">Przykłady zarządzania AppFabric</span><span class="sxs-lookup"><span data-stu-id="ea144-127">AppFabric Management Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193960)  
 [<span data-ttu-id="ea144-128">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ea144-128">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
