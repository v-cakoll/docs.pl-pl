---
title: Konfigurowanie usług WCF w kodzie
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 96bd9af7fcf22789b95b2efabbed6a19401b2d97
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242415"
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="a9184-102">Konfigurowanie usług WCF w kodzie</span><span class="sxs-lookup"><span data-stu-id="a9184-102">Configuring WCF Services in Code</span></span>
<span data-ttu-id="a9184-103">Windows Communication Foundation (WCF) umożliwia deweloperom konfigurowanie usług za pomocą plików konfiguracji lub kodu.</span><span class="sxs-lookup"><span data-stu-id="a9184-103">Windows Communication Foundation (WCF) allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="a9184-104">Pliki konfiguracyjne są przydatne, gdy usługa musi zostać skonfigurowane po wdrożeniu.</span><span class="sxs-lookup"><span data-stu-id="a9184-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="a9184-105">Korzystając z plików konfiguracji, specjalistów IT wystarczy zaktualizować plik konfiguracji, nie ponownej kompilacji jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="a9184-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="a9184-106">Pliki konfiguracyjne, może jednak być złożone i trudne w utrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="a9184-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="a9184-107">Brak obsługi debugowania plików konfiguracji i elementy konfiguracji odwołują się nazwy, co sprawia, że pliki konfiguracji tworzenia podatne na błędy i trudne.</span><span class="sxs-lookup"><span data-stu-id="a9184-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> <span data-ttu-id="a9184-108">WCF umożliwia również skonfigurowanie usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a9184-108">WCF also allows you to configure services in code.</span></span> <span data-ttu-id="a9184-109">We wcześniejszych wersjach, konfigurowanie usług WCF (4.0 i starszych) w kodzie jest łatwe w scenariuszach Self-Hosted <xref:System.ServiceModel.ServiceHost> klasa dozwolona można skonfigurować punkty końcowe i zachowania przed wywołaniem ServiceHost.Open.</span><span class="sxs-lookup"><span data-stu-id="a9184-109">In earlier versions of WCF (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="a9184-110">W scenariuszach hostowanych w sieci web, ale nie masz bezpośredni dostęp do <xref:System.ServiceModel.ServiceHost> klasy.</span><span class="sxs-lookup"><span data-stu-id="a9184-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="a9184-111">Aby skonfigurować sieci web hostowanych usług, które są wymagane do utworzenia `System.ServiceModel.ServiceHostFactory` utworzonego <xref:System.ServiceModel.Activation.ServiceHostFactory> i wykonać wszelkie wymagane konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a9184-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="a9184-112">Począwszy od .NET 4.5 programu WCF zapewnia łatwiejszy sposób skonfigurować zarówno może być samodzielnie hostowane i sieci web hostowanej usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a9184-112">Starting with .NET 4.5, WCF provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="a9184-113">Metoda Konfiguruj</span><span class="sxs-lookup"><span data-stu-id="a9184-113">The Configure method</span></span>  
 <span data-ttu-id="a9184-114">Wystarczy zdefiniować publicznej statycznej metody o nazwie `Configure` z następującą sygnaturą w klasie implementacji usługi:</span><span class="sxs-lookup"><span data-stu-id="a9184-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="a9184-115">Metoda Konfiguruj przyjmuje <xref:System.ServiceModel.ServiceConfiguration> wystąpienie, które umożliwia dla deweloperów dodać punkty końcowe i zachowania.</span><span class="sxs-lookup"><span data-stu-id="a9184-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="a9184-116">Ta metoda jest wywoływana przez architekturę WCF, przed otwarciem hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="a9184-116">This method is called by WCF before the service host is opened.</span></span> <span data-ttu-id="a9184-117">Po zdefiniowaniu wszystkie ustawienia konfiguracji usługi w pliku app.config lub web.config zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="a9184-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="a9184-118">Poniższy fragment kodu ilustruje sposób definiowania `Configure` metody i Dodaj punkt końcowy usługi, zachowanie punktu końcowego i zachowania usługi:</span><span class="sxs-lookup"><span data-stu-id="a9184-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
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
            return $"You entered: {value}";
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
  
 <span data-ttu-id="a9184-119">Aby włączyć protokół, taki jak https dla usługi, można jawnie dodać punkt końcowy, który korzysta z protokołu lub można automatycznie dodać punkty końcowe, wywołując ServiceConfiguration.EnableProtocol(Binding), który dodaje punkt końcowy dla każdego adresu podstawowego zgodny z protokołem i każdej umowy serwisowej zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="a9184-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="a9184-120">Poniższy kod ilustruje sposób użycia metody ServiceConfiguration.EnableProtocol:</span><span class="sxs-lookup"><span data-stu-id="a9184-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
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
  
 <span data-ttu-id="a9184-121">Ustawienia w <`protocolMappings`> sekcji są używane tylko w przypadku punktów końcowych aplikacji są dodawane do <xref:System.ServiceModel.ServiceConfiguration> programowo. Możesz opcjonalnie załadować konfiguracji usługi z domyślny plik konfiguracji aplikacji, wywołując <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> , a następnie zmień ustawienia.</span><span class="sxs-lookup"><span data-stu-id="a9184-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="a9184-122"><xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> Klasy umożliwia także załadować konfiguracji ze scentralizowanego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a9184-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="a9184-123">Poniższy kod ilustruje sposób implementacji:</span><span class="sxs-lookup"><span data-stu-id="a9184-123">The following code illustrates how to implement this:</span></span>  
  
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
>  <span data-ttu-id="a9184-124">Należy pamiętać, że <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignoruje <`host`> Ustawienia w <`service`> tag <`system.serviceModel`>.</span><span class="sxs-lookup"><span data-stu-id="a9184-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="a9184-125">Model <`host`> dotyczy konfiguracji hosta, nie konfiguracji usługi i pobiera załadowane przed wykonaniem metody konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a9184-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9184-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9184-126">See Also</span></span>  
 [<span data-ttu-id="a9184-127">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a9184-127">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [<span data-ttu-id="a9184-128">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="a9184-128">Configuring Client Behaviors</span></span>](../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [<span data-ttu-id="a9184-129">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a9184-129">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="a9184-130">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a9184-130">Configuration</span></span>](../../../docs/framework/wcf/samples/configuration-sample.md)  
 [<span data-ttu-id="a9184-131">Aktywacja oparta na konfiguracji w usługach IIS i WAS</span><span class="sxs-lookup"><span data-stu-id="a9184-131">Configuration-Based Activation in IIS and WAS</span></span>](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 [<span data-ttu-id="a9184-132">Konfiguracja i obsługa metadanych</span><span class="sxs-lookup"><span data-stu-id="a9184-132">Configuration and Metadata Support</span></span>](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)  
 [<span data-ttu-id="a9184-133">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a9184-133">Configuration</span></span>](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)  
 [<span data-ttu-id="a9184-134">Instrukcje: Określanie wiązań usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a9184-134">How to: Specify a Service Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [<span data-ttu-id="a9184-135">Instrukcje: Tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a9184-135">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [<span data-ttu-id="a9184-136">Instrukcje: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a9184-136">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="a9184-137">Instrukcje: Określanie wiązania klienta w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a9184-137">How to: Specify a Client Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
