---
title: Uproszczona konfiguracja usług WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: c0d5f46e6ace71ad4732f8d387b3289b1d4105e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516372"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="1eb41-102">Uproszczona konfiguracja usług WCF</span><span class="sxs-lookup"><span data-stu-id="1eb41-102">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="1eb41-103">W tym przykładzie pokazano, jak zaimplementować i skonfigurować typowe usługi i klienta przy użyciu usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1eb41-103">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="1eb41-104">Te przykładowe dane stanowią podstawę dla wszystkich przykładów podstawową technologię.</span><span class="sxs-lookup"><span data-stu-id="1eb41-104">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="1eb41-105">Uproszczona konfiguracja w korzysta z tej usługi, który uwidacznia punkt końcowy w celu komunikowania się z usługą, [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1eb41-105">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span></span> <span data-ttu-id="1eb41-106">Przed [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], punkt końcowy jest zazwyczaj definiowane w pliku konfiguracji (Web.config), jak pokazano w poniższym kodzie przykładu w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1eb41-106">Prior to [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
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
  
 <span data-ttu-id="1eb41-107">W [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], `<service>` element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="1eb41-107">In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the `<service>` element is optional.</span></span> <span data-ttu-id="1eb41-108">Jeśli usługi nie definiuje żadnych punktów końcowych, punkt końcowy dla każdego adresu podstawowego i zaimplementować kontrakt są dodawane do usługi.</span><span class="sxs-lookup"><span data-stu-id="1eb41-108">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="1eb41-109">Adres podstawowy jest dołączany do nazwy kontraktu, aby ustalić punkt końcowy, a następnie powiązanie jest określana przez schemat adresów.</span><span class="sxs-lookup"><span data-stu-id="1eb41-109">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="1eb41-110">Poniższy przykład kodu demonstruje pliku uproszczona konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="1eb41-110">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="1eb41-111">Zgodnie z konfiguracją, usługi mogą być wyświetlane w `http://localhost/servicemodelsamples/service.svc` przez klienta na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="1eb41-111">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="1eb41-112">W przypadku klientów na komputerach zdalnych w celu uzyskania dostępu do usługi należy określić w pełni kwalifikowanej nazwy domeny zamiast nazwy localhost.</span><span class="sxs-lookup"><span data-stu-id="1eb41-112">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="1eb41-113">Domyślnie usługa nie ujawnia metadanych.</span><span class="sxs-lookup"><span data-stu-id="1eb41-113">The service does not expose metadata by default.</span></span> <span data-ttu-id="1eb41-114">W efekcie usługa włącza <xref:System.ServiceModel.Description.ServiceMetadataBehavior> zachowanie.</span><span class="sxs-lookup"><span data-stu-id="1eb41-114">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
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
  
### <a name="to-use-this-sample"></a><span data-ttu-id="1eb41-115">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="1eb41-115">To use this sample</span></span>  
  
1.  <span data-ttu-id="1eb41-116">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1eb41-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1eb41-117">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1eb41-117">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="1eb41-118">Uruchom aplikację przykładową, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="1eb41-118">Run the sample by following these steps:</span></span>  
  
    1.  <span data-ttu-id="1eb41-119">Kliknij prawym przyciskiem myszy **usługi** projektu, a następnie wybierz **Ustaw jako projekt startowy**, naciśnij klawisz **kombinację klawiszy Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="1eb41-119">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2.  <span data-ttu-id="1eb41-120">Poczekaj, aż dane wyjściowe konsoli z potwierdzenie, że usługa działa i uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="1eb41-120">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3.  <span data-ttu-id="1eb41-121">Kliknij prawym przyciskiem myszy **klienta** projektu, a następnie wybierz **Ustaw jako projekt startowy**, naciśnij klawisz **kombinację klawiszy Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="1eb41-121">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1eb41-122">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="1eb41-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1eb41-123">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="1eb41-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1eb41-124">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="1eb41-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1eb41-125">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="1eb41-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="1eb41-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1eb41-126">See also</span></span>
- [<span data-ttu-id="1eb41-127">Przykładami dotyczącymi zarządzania AppFabric</span><span class="sxs-lookup"><span data-stu-id="1eb41-127">AppFabric Management Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193960)
- [<span data-ttu-id="1eb41-128">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="1eb41-128">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
