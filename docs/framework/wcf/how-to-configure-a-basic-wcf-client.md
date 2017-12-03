---
title: 'Instrukcje: Konfigurowanie podstawowego klienta WCF (Windows Communication Foundation)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
caps.latest.revision: "47"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c9ee75734349210ac9379aaf30523a98c4a14f94
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a><span data-ttu-id="6cb9d-102">Instrukcje: Konfigurowanie podstawowego klienta WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="6cb9d-102">How to: Configure a Basic Windows Communication Foundation Client</span></span>
<span data-ttu-id="6cb9d-103">To jest piątym sześciu zadania wymagane do tworzenia prostej [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6cb9d-103">This is the fifth of six tasks required to create a basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="6cb9d-104">Omówienie sześciu wszystkich zadań, zobacz [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="6cb9d-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="6cb9d-105">Ten temat disuccess pliku konfiguracji klienta, który został wygenerowany za pomocą funkcji Dodaj odwołanie do usługi [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] lub [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6cb9d-105">This topic disuccess the client configuration file that was generated using the Add Service Reference functionality of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="6cb9d-106">Konfigurowanie klienta obejmuje określenie punktu końcowego, który klient używa do uzyskania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="6cb9d-106">Configuring the client consists of specifying the endpoint that the client uses to access the service.</span></span> <span data-ttu-id="6cb9d-107">Punkt końcowy ma adres, powiązania i kontrakt i każdego z nich musi być określona podczas konfigurowania klienta.</span><span class="sxs-lookup"><span data-stu-id="6cb9d-107">An endpoint has an address, a binding and a contract, and each of these must be specified in the process of configuring the client.</span></span>  
  
### <a name="to-configure-a-windows-communication-foundation-client"></a><span data-ttu-id="6cb9d-108">Aby skonfigurować klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="6cb9d-108">To configure a Windows Communication Foundation client</span></span>  
  
1.  <span data-ttu-id="6cb9d-109">Otwórz plik konfiguracji wygenerowanego (App.config) z projektu GettingStartedClient.</span><span class="sxs-lookup"><span data-stu-id="6cb9d-109">Open the generated configuration file (App.config) from the GettingStartedClient project.</span></span> <span data-ttu-id="6cb9d-110">Poniższy przykład jest to widok pliku konfiguracyjnego wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="6cb9d-110">The following example is a view of the generated configuration file.</span></span> <span data-ttu-id="6cb9d-111">W obszarze [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) sekcji, Znajdź [ \<punktu końcowego >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu.</span><span class="sxs-lookup"><span data-stu-id="6cb9d-111">Under the [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, find the [\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
        <startup>   
          <!-- specifies the version of WCF to use-->  
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />  
        </startup>  
        <system.serviceModel>  
            <bindings>  
                <!-- Uses wsHttpBinding-->  
                <wsHttpBinding>  
                    <binding name="WSHttpBinding_ICalculator" />  
                </wsHttpBinding>  
            </bindings>  
            <client>  
                <!-- specifies the endpoint to use when calling the service -->  
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"  
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"  
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">  
                    <identity>  
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />  
                    </identity>  
                </endpoint>  
            </client>  
        </system.serviceModel>  
    </configuration>   
    ```  
  
     <span data-ttu-id="6cb9d-112">Ten przykład konfiguruje punktu końcowego, który klient używa do uzyskania dostępu do usługi, która znajduje się pod następującym adresem: http://localhost: 8000/ServiceModelSamples/Service/CalculatorService</span><span class="sxs-lookup"><span data-stu-id="6cb9d-112">This example configures the endpoint that the client uses to access the service that is located at the following address: http://localhost:8000/ServiceModelSamples/Service/CalculatorService</span></span>  
  
     <span data-ttu-id="6cb9d-113">Określa element punktu końcowego, że `ServiceReference1.ICalculator` kontraktu usługi jest używany do komunikacji między klienta WCF i usługi.</span><span class="sxs-lookup"><span data-stu-id="6cb9d-113">The endpoint element specifies that the `ServiceReference1.ICalculator` service contract is used for communication between the WCF client and service.</span></span> <span data-ttu-id="6cb9d-114">Skonfigurowano kanał WCF dostarczane przez system <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>.</span><span class="sxs-lookup"><span data-stu-id="6cb9d-114">The WCF channel is configured with the system-provided <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>.</span></span> <span data-ttu-id="6cb9d-115">Ten kontrakt wygenerowanych przy użyciu Dodaj odwołanie do usługi w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6cb9d-115">This contract was generated by using Add Service Reference in Visual Studio.</span></span> <span data-ttu-id="6cb9d-116">Jest zasadniczo kopią kontraktu, który został zdefiniowany w projekcie GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="6cb9d-116">It is essentially a copy of the contract that was defined in the GettingStartedLib project.</span></span> <span data-ttu-id="6cb9d-117"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> Powiązanie określa HTTP jako transportu, interoperacyjne zabezpieczeń i inne szczegóły konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6cb9d-117">The <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>  
  
2.  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="6cb9d-118">wygenerowanego klienta za pomocą tej konfiguracji, zobacz [porady: używanie klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="6cb9d-118"> how to use the generated client with this configuration, see [How to: Use a Client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cb9d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6cb9d-119">See Also</span></span>  
 [<span data-ttu-id="6cb9d-120">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="6cb9d-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="6cb9d-121">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="6cb9d-121">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="6cb9d-122">Porady: Tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="6cb9d-122">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="6cb9d-123">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="6cb9d-123">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="6cb9d-124">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="6cb9d-124">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
