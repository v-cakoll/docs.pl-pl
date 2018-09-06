---
title: 'Instrukcje: Konfigurowanie podstawowego klienta WCF (Windows Communication Foundation)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
ms.openlocfilehash: 2866cbd5862bf55286fc771823488cf913863de2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855858"
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a><span data-ttu-id="198fc-102">Instrukcje: Konfigurowanie podstawowego klienta WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="198fc-102">How to: Configure a Basic Windows Communication Foundation Client</span></span>
<span data-ttu-id="198fc-103">Jest to piąty sześciu zadań podrzędnych, wymagane do utworzenia podstawowej aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="198fc-103">This is the fifth of six tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="198fc-104">Omówienie wszystkich sześciu zadań, zobacz [Samouczek wprowadzający](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="198fc-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="198fc-105">W tym temacie omówiono pliku konfiguracji klienta, który został wygenerowany za pomocą funkcji Dodaj odwołanie do usługi [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] lub [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="198fc-105">This topic discusses the client configuration file that was generated using the Add Service Reference functionality of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="198fc-106">Konfigurowanie klienta składa się z określania punktu końcowego, który klient używa w celu uzyskania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="198fc-106">Configuring the client consists of specifying the endpoint that the client uses to access the service.</span></span> <span data-ttu-id="198fc-107">Punkt końcowy ma adres, powiązanie i kontrakt, a każdy z nich musi być określona w procesie konfigurowania klienta.</span><span class="sxs-lookup"><span data-stu-id="198fc-107">An endpoint has an address, a binding and a contract, and each of these must be specified in the process of configuring the client.</span></span>  
  
### <a name="to-configure-a-windows-communication-foundation-client"></a><span data-ttu-id="198fc-108">Aby skonfigurować klienta programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="198fc-108">To configure a Windows Communication Foundation client</span></span>  
  
1.  <span data-ttu-id="198fc-109">Otwórz plik wygenerowanego konfiguracji (App.config) z projektu GettingStartedClient.</span><span class="sxs-lookup"><span data-stu-id="198fc-109">Open the generated configuration file (App.config) from the GettingStartedClient project.</span></span> <span data-ttu-id="198fc-110">Poniższy przykład jest widok pliku wygenerowaną konfigurację.</span><span class="sxs-lookup"><span data-stu-id="198fc-110">The following example is a view of the generated configuration file.</span></span> <span data-ttu-id="198fc-111">W obszarze [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) sekcji, Znajdź [ \<punktu końcowego >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu.</span><span class="sxs-lookup"><span data-stu-id="198fc-111">Under the [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, find the [\<endpoint>](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.</span></span>  
  
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
  
     <span data-ttu-id="198fc-112">Ten przykład umożliwia skonfigurowanie punktu końcowego, który klient używa w celu uzyskania dostępu do usługi, która znajduje się pod następującym adresem: http://localhost:8000/ServiceModelSamples/Service/CalculatorService</span><span class="sxs-lookup"><span data-stu-id="198fc-112">This example configures the endpoint that the client uses to access the service that is located at the following address: http://localhost:8000/ServiceModelSamples/Service/CalculatorService</span></span>  
  
     <span data-ttu-id="198fc-113">Element końcowy określa, że `ServiceReference1.ICalculator` kontraktu usługi jest używany do komunikacji między klientem usługi WCF a usługą.</span><span class="sxs-lookup"><span data-stu-id="198fc-113">The endpoint element specifies that the `ServiceReference1.ICalculator` service contract is used for communication between the WCF client and service.</span></span> <span data-ttu-id="198fc-114">Kanał WCF jest skonfigurowany przy użyciu dostarczane przez system <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="198fc-114">The WCF channel is configured with the system-provided <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="198fc-115">Ten kontrakt został wygenerowany za pomocą Dodaj odwołanie do usługi w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="198fc-115">This contract was generated by using Add Service Reference in Visual Studio.</span></span> <span data-ttu-id="198fc-116">Jest zasadniczo kopię umowy, która została zdefiniowana w projekcie GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="198fc-116">It is essentially a copy of the contract that was defined in the GettingStartedLib project.</span></span> <span data-ttu-id="198fc-117"><xref:System.ServiceModel.WSHttpBinding> Powiązanie określa HTTP jako transportu, interoperacyjne zabezpieczeń i inne szczegóły konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="198fc-117">The <xref:System.ServiceModel.WSHttpBinding> binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>  
  
2.  <span data-ttu-id="198fc-118">Aby uzyskać więcej informacji o sposobie używania wygenerowanego klienta przy użyciu tej konfiguracji, zobacz [porady: używanie klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="198fc-118">For more information about how to use the generated client with this configuration, see [How to: Use a Client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="198fc-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="198fc-119">See Also</span></span>  
 [<span data-ttu-id="198fc-120">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="198fc-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="198fc-121">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="198fc-121">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="198fc-122">Instrukcje: tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="198fc-122">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="198fc-123">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="198fc-123">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="198fc-124">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="198fc-124">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
