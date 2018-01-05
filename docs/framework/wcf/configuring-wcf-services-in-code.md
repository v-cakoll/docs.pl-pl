---
title: "Konfigurowanie usług WCF w kodzie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 202214a6c9279eb61db560321a8f36943ce5d635
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="e49ed-102">Konfigurowanie usług WCF w kodzie</span><span class="sxs-lookup"><span data-stu-id="e49ed-102">Configuring WCF Services in Code</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="e49ed-103">Umożliwia deweloperom konfigurowanie usług przy użyciu plików konfiguracyjnych lub kodu.</span><span class="sxs-lookup"><span data-stu-id="e49ed-103"> allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="e49ed-104">Pliki konfiguracji są przydatne, gdy usługa musi być skonfigurowana po wdrożeniu.</span><span class="sxs-lookup"><span data-stu-id="e49ed-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="e49ed-105">Podczas korzystania z plików konfiguracyjnych, specjalistów IT wystarczy tylko zaktualizować pliku konfiguracji, kompilacji nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="e49ed-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="e49ed-106">Pliki konfiguracji, jednak można złożone i trudne w utrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="e49ed-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="e49ed-107">Nie jest obsługiwane dla debugowania plików konfiguracji i elementy konfiguracji odwołują się nazwy, dzięki czemu tworzenia plików konfiguracyjnych podatne na błędy i trudne.</span><span class="sxs-lookup"><span data-stu-id="e49ed-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="e49ed-108">Umożliwia również skonfigurować usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e49ed-108"> also allows you to configure services in code.</span></span> <span data-ttu-id="e49ed-109">W starszych wersjach [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (4.0 i starszych) Konfigurowanie usług w kodzie było łatwe w scenariuszach siebie <xref:System.ServiceModel.ServiceHost> klasa dozwolona konfigurowania punktów końcowych i zachowania przed wywołaniem ServiceHost.Open.</span><span class="sxs-lookup"><span data-stu-id="e49ed-109">In earlier versions of [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="e49ed-110">W scenariuszach hostowana w sieci web, możesz nie mają jednak bezpośredni dostęp do <xref:System.ServiceModel.ServiceHost> klasy.</span><span class="sxs-lookup"><span data-stu-id="e49ed-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="e49ed-111">Aby skonfigurować sieci web hostowanej usługi są wymagane do utworzenia `System.ServiceModel.ServiceHostFactory` utworzony <xref:System.ServiceModel.Activation.ServiceHostFactory> i wykonać wszelkie wymagane konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e49ed-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="e49ed-112">W programie .NET 4.5, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] umożliwia łatwiejsze sposobem skonfigurowania obu hosta samodzielnego i sieci web hostowanych usług w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e49ed-112">Starting with .NET 4.5, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="e49ed-113">Konfiguruj — metoda</span><span class="sxs-lookup"><span data-stu-id="e49ed-113">The Configure method</span></span>  
 <span data-ttu-id="e49ed-114">Wystarczy zdefiniować publicznej metody statycznej o nazwie `Configure` z następującą sygnaturą w klasie implementacji usługi:</span><span class="sxs-lookup"><span data-stu-id="e49ed-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="e49ed-115">Metoda Konfiguruj przyjmuje <xref:System.ServiceModel.ServiceConfiguration> wystąpienie, które umożliwia deweloperowi dodać punkty końcowe i zachowania.</span><span class="sxs-lookup"><span data-stu-id="e49ed-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="e49ed-116">Ta metoda jest wywoływana przez [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] przed otwarciem hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="e49ed-116">This method is called by [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] before the service host is opened.</span></span> <span data-ttu-id="e49ed-117">Po zdefiniowaniu wszystkich ustawień konfiguracji usługi określone w pliku app.config lub web.config zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="e49ed-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="e49ed-118">Poniższy fragment kodu przedstawia sposób definiowania `Configure` — metoda i Dodaj punkt końcowy usługi, zachowanie punktu końcowego i zachowania usługi:</span><span class="sxs-lookup"><span data-stu-id="e49ed-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return string.Format("You entered: {0}", value);  
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 <span data-ttu-id="e49ed-119">Aby włączyć protokół, taki jak https dla usługi, można jawnie dodać punktu końcowego, który korzysta z protokołu lub może automatycznie dodać punkty końcowe, wywołując ServiceConfiguration.EnableProtocol(Binding), który dodaje punkt końcowy dla każdego adresu podstawowego zgodny z protokołem i każdej umowy serwisowej zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="e49ed-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="e49ed-120">Poniższy kod przedstawia sposób użycia metody ServiceConfiguration.EnableProtocol:</span><span class="sxs-lookup"><span data-stu-id="e49ed-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
```csharp  
public class Service1 : IService1   
{   
    public string GetData(int value);   
    public static void Configure(ServiceConfiguration config)   
    {   
        // Enable "Add Service Reference" support   
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });   
       // set up support for http, https, net.tcp, net.pipe   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new NetTcpBinding());   
       config.EnableProtocol(new NetNamedPipeBinding());   
       // add an extra BasicHttpBinding endpoint at http:///basic   
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");   
    }   
}   
```  
  
 <span data-ttu-id="e49ed-121">Ustawienia w <`protocolMappings`> sekcji są używane tylko w przypadku punktów końcowych aplikacji są dodawane do <xref:System.ServiceModel.ServiceConfiguration> programowo. Można opcjonalnie załadować konfiguracji usługi z domyślny plik konfiguracji aplikacji, wywołując <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> , a następnie zmień ustawienia.</span><span class="sxs-lookup"><span data-stu-id="e49ed-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="e49ed-122"><xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> Klasa umożliwia także załadować konfiguracji z scentralizowane konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e49ed-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="e49ed-123">Poniższy kod ilustruje sposób implementowania to:</span><span class="sxs-lookup"><span data-stu-id="e49ed-123">The following code illustrates how to implement this:</span></span>  
  
```  
public class Service1 : IService1   
{   
    public void DoWork();   
    public static void Configure(ServiceConfiguration config)   
    {   
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));   
    }   
}  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="e49ed-124">Należy pamiętać, że <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignoruje <`host`> Ustawienia w <`service`> tag <`system.serviceModel`>.</span><span class="sxs-lookup"><span data-stu-id="e49ed-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="e49ed-125">Koncepcyjnie <`host`> jest o konfiguracji hosta, nie konfigurację usługi i pobiera załadowane przed wykonaniem metody konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e49ed-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e49ed-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e49ed-126">See Also</span></span>  
 [<span data-ttu-id="e49ed-127">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e49ed-127">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [<span data-ttu-id="e49ed-128">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="e49ed-128">Configuring Client Behaviors</span></span>](../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [<span data-ttu-id="e49ed-129">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="e49ed-129">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="e49ed-130">Aktywacja oparta na konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e49ed-130">Configuration-Based Activation</span></span>](../../../docs/framework/wcf/samples/configuration-based-activation.md)  
 [<span data-ttu-id="e49ed-131">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="e49ed-131">Configuration</span></span>](../../../docs/framework/wcf/samples/configuration-sample.md)  
 [<span data-ttu-id="e49ed-132">Aktywacja oparta na konfiguracji w usługach IIS i WAS</span><span class="sxs-lookup"><span data-stu-id="e49ed-132">Configuration-Based Activation in IIS and WAS</span></span>](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 [<span data-ttu-id="e49ed-133">Konfiguracja i obsługa metadanych</span><span class="sxs-lookup"><span data-stu-id="e49ed-133">Configuration and Metadata Support</span></span>](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)  
 [<span data-ttu-id="e49ed-134">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="e49ed-134">Configuration</span></span>](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)  
 [<span data-ttu-id="e49ed-135">Instrukcje: określanie powiązania usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e49ed-135">How to: Specify a Service Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [<span data-ttu-id="e49ed-136">Instrukcje: tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e49ed-136">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [<span data-ttu-id="e49ed-137">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e49ed-137">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="e49ed-138">Instrukcje: określanie powiązań klienta w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e49ed-138">How to: Specify a Client Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
