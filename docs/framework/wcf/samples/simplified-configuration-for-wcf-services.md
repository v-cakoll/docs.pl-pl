---
title: Uproszczona konfiguracja usług WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 80e2ac83ec0e07176d6afe6d34c63fb4d8e836d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="8a07c-102">Uproszczona konfiguracja usług WCF</span><span class="sxs-lookup"><span data-stu-id="8a07c-102">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="8a07c-103">W tym przykładzie pokazano, jak wdrożyć i skonfigurować typowe usługi i klienta przy użyciu usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8a07c-103">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="8a07c-104">W tym przykładzie stanowi podstawę dla wszystkich innych przykładów podstawową technologię.</span><span class="sxs-lookup"><span data-stu-id="8a07c-104">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="8a07c-105">Uproszczona konfiguracja w korzysta z tej usługi, który udostępnia punktu końcowego w celu komunikowania się z usługą, [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8a07c-105">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span></span> <span data-ttu-id="8a07c-106">Przed [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], punkt końcowy jest zazwyczaj definiowane w pliku konfiguracyjnym (Web.config), jak pokazano w poniższym kodzie konfiguracji przykład.</span><span class="sxs-lookup"><span data-stu-id="8a07c-106">Prior to [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
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
  
 <span data-ttu-id="8a07c-107">W [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], `<service>` element jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8a07c-107">In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the `<service>` element is optional.</span></span> <span data-ttu-id="8a07c-108">Jeśli usługi nie definiuje żadnych punktów końcowych, dla każdego adresu podstawowego i zaimplementowana kontraktu punktu końcowego są dodawane do usługi.</span><span class="sxs-lookup"><span data-stu-id="8a07c-108">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="8a07c-109">Adres podstawowy jest dołączany do nazwy kontraktu, aby ustalić punktu końcowego i powiązania jest określany przez schemat adresów.</span><span class="sxs-lookup"><span data-stu-id="8a07c-109">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="8a07c-110">W poniższym przykładzie przedstawiono plik konfiguracji uproszczone.</span><span class="sxs-lookup"><span data-stu-id="8a07c-110">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="8a07c-111">Zgodnie z konfiguracją, usługi mogą być wyświetlane w http://localhost/servicemodelsamples/service.svc przez klienta na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="8a07c-111">As configured, the service can be accessed at http://localhost/servicemodelsamples/service.svc by a client on the same computer.</span></span> <span data-ttu-id="8a07c-112">Dla klientów na komputerach zdalnych do uzyskania dostępu do usługi należy określić w pełni kwalifikowanej nazwy domeny zamiast nazwy localhost.</span><span class="sxs-lookup"><span data-stu-id="8a07c-112">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="8a07c-113">Domyślnie usługa nie uwidacznia metadanych.</span><span class="sxs-lookup"><span data-stu-id="8a07c-113">The service does not expose metadata by default.</span></span> <span data-ttu-id="8a07c-114">W efekcie usługa włącza <xref:System.ServiceModel.Description.ServiceMetadataBehavior> zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8a07c-114">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
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
  
### <a name="to-use-this-sample"></a><span data-ttu-id="8a07c-115">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="8a07c-115">To use this sample</span></span>  
  
1.  <span data-ttu-id="8a07c-116">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8a07c-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="8a07c-117">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8a07c-117">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="8a07c-118">Uruchom próbkę, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="8a07c-118">Run the sample by following these steps:</span></span>  
  
    1.  <span data-ttu-id="8a07c-119">Kliknij prawym przyciskiem myszy **usługi** projekt i wybierz **Ustaw jako projekt startowy**, naciśnij klawisz **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="8a07c-119">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2.  <span data-ttu-id="8a07c-120">Poczekaj na dane wyjściowe konsoli potwierdzenie, że usługa działa i uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="8a07c-120">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3.  <span data-ttu-id="8a07c-121">Kliknij prawym przyciskiem myszy **klienta** projekt i wybierz **Ustaw jako projekt startowy**, naciśnij klawisz **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="8a07c-121">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8a07c-122">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="8a07c-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8a07c-123">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="8a07c-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8a07c-124">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="8a07c-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8a07c-125">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8a07c-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="8a07c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a07c-126">See Also</span></span>  
 [<span data-ttu-id="8a07c-127">Przykłady zarządzania AppFabric</span><span class="sxs-lookup"><span data-stu-id="8a07c-127">AppFabric Management Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193960)  
 [<span data-ttu-id="8a07c-128">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="8a07c-128">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
