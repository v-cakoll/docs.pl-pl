---
title: Konfigurowanie usług WCF w kodzie
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 5d05fe5f70f4e2b1490c728cc019430cd94ff925
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569503"
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="7c046-102">Konfigurowanie usług WCF w kodzie</span><span class="sxs-lookup"><span data-stu-id="7c046-102">Configuring WCF Services in Code</span></span>
<span data-ttu-id="7c046-103">Windows Communication Foundation (WCF) umożliwia deweloperom Konfigurowanie usług przy użyciu plików konfiguracyjnych lub kodu.</span><span class="sxs-lookup"><span data-stu-id="7c046-103">Windows Communication Foundation (WCF) allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="7c046-104">Pliki konfiguracji są przydatne, gdy usługa musi zostać skonfigurowana po wdrożeniu.</span><span class="sxs-lookup"><span data-stu-id="7c046-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="7c046-105">W przypadku korzystania z plików konfiguracji Specjalista IT musi tylko zaktualizować plik konfiguracji, nie jest wymagana ponowna kompilacja.</span><span class="sxs-lookup"><span data-stu-id="7c046-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="7c046-106">Pliki konfiguracji mogą jednak być skomplikowane i trudne do utrzymania.</span><span class="sxs-lookup"><span data-stu-id="7c046-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="7c046-107">Nie ma obsługi debugowania plików konfiguracji i elementów konfiguracji, do których odwołują się nazwy, co sprawia, że pliki konfiguracji tworzenia są podatne na błędy i trudne.</span><span class="sxs-lookup"><span data-stu-id="7c046-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> <span data-ttu-id="7c046-108">Funkcja WCF umożliwia również Konfigurowanie usług w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7c046-108">WCF also allows you to configure services in code.</span></span> <span data-ttu-id="7c046-109">We wcześniejszych wersjach programu WCF (4,0 i starszych) Konfigurowanie usług w kodzie było łatwe w scenariuszach samodzielnej obsługi, ale Klasa <xref:System.ServiceModel.ServiceHost> może skonfigurować punkty końcowe i zachowania przed wywołaniem ServiceHost. Open.</span><span class="sxs-lookup"><span data-stu-id="7c046-109">In earlier versions of WCF (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="7c046-110">Nie ma jednak bezpośredniego dostępu do klasy <xref:System.ServiceModel.ServiceHost> w scenariuszach hostowanych w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7c046-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="7c046-111">Aby skonfigurować usługę hostowaną w sieci Web, należy utworzyć `System.ServiceModel.ServiceHostFactory`, które utworzyły <xref:System.ServiceModel.Activation.ServiceHostFactory> i wykonać dowolną potrzebną konfigurację.</span><span class="sxs-lookup"><span data-stu-id="7c046-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="7c046-112">Począwszy od platformy .NET 4,5, WCF oferuje łatwiejszy sposób konfigurowania usług samodzielnych i hostowanych w sieci Web w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7c046-112">Starting with .NET 4.5, WCF provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="7c046-113">Metoda Configure</span><span class="sxs-lookup"><span data-stu-id="7c046-113">The Configure method</span></span>  
 <span data-ttu-id="7c046-114">Po prostu Zdefiniuj publiczną metodę statyczną o nazwie `Configure` z następującą sygnaturą w klasie implementacji usługi:</span><span class="sxs-lookup"><span data-stu-id="7c046-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="7c046-115">Metoda Configure przyjmuje <xref:System.ServiceModel.ServiceConfiguration> wystąpienie, które umożliwia deweloperowi Dodawanie punktów końcowych i zachowań.</span><span class="sxs-lookup"><span data-stu-id="7c046-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="7c046-116">Ta metoda jest wywoływana przez funkcję WCF przed otwarciem hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="7c046-116">This method is called by WCF before the service host is opened.</span></span> <span data-ttu-id="7c046-117">Po zdefiniowaniu wszystkie ustawienia konfiguracji usługi określone w pliku App. config lub Web. config zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="7c046-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="7c046-118">Poniższy fragment kodu ilustruje sposób definiowania metody `Configure` i dodawania punktu końcowego usługi, zachowania punktu końcowego i zachowań usługi:</span><span class="sxs-lookup"><span data-stu-id="7c046-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
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
  
 <span data-ttu-id="7c046-119">Aby włączyć protokół, taki jak https dla usługi, można jawnie dodać punkt końcowy, który używa protokołu lub można automatycznie dodać punkty końcowe, wywołując metodę ServiceConfiguration. EnableProtocol (Binding), która dodaje punkt końcowy dla każdego adresu podstawowego zgodne z protokołem i każdym zdefiniowanym kontraktem usługi.</span><span class="sxs-lookup"><span data-stu-id="7c046-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="7c046-120">Poniższy kod ilustruje sposób używania metody ServiceConfiguration. EnableProtocol:</span><span class="sxs-lookup"><span data-stu-id="7c046-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
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
       config.EnableProtocol(new BasicHttpsBinding());   
       config.EnableProtocol(new NetTcpBinding());   
       config.EnableProtocol(new NetNamedPipeBinding());   
       // add an extra BasicHttpBinding endpoint at http:///basic   
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");   
    }   
}   
```  
  
 <span data-ttu-id="7c046-121">Ustawienia w sekcji <`protocolMappings`> są używane tylko wtedy, gdy żadne punkty końcowe aplikacji nie są dodawane do <xref:System.ServiceModel.ServiceConfiguration> programowo. Opcjonalnie można załadować konfigurację usługi z domyślnego pliku konfiguracyjnego aplikacji przez wywołanie <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> a następnie zmianę ustawień.</span><span class="sxs-lookup"><span data-stu-id="7c046-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="7c046-122">Klasa <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> umożliwia również ładowanie konfiguracji z poziomu scentralizowanej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7c046-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="7c046-123">Poniższy kod ilustruje sposób implementacji:</span><span class="sxs-lookup"><span data-stu-id="7c046-123">The following code illustrates how to implement this:</span></span>  
  
```csharp
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
> <span data-ttu-id="7c046-124">Należy zauważyć, że <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignoruje <`host`> ustawień w <`service`> <.</span><span class="sxs-lookup"><span data-stu-id="7c046-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="7c046-125">Ze pojęciową <`host`> jest informacje o konfiguracji hosta, a nie konfiguracji usługi i jest ładowany przed wykonaniem metody Configure.</span><span class="sxs-lookup"><span data-stu-id="7c046-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c046-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c046-126">See also</span></span>

- [<span data-ttu-id="7c046-127">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7c046-127">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="7c046-128">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="7c046-128">Configuring Client Behaviors</span></span>](configuring-client-behaviors.md)
- [<span data-ttu-id="7c046-129">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="7c046-129">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="7c046-130">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="7c046-130">Configuration</span></span>](./samples/configuration-sample.md)
- [<span data-ttu-id="7c046-131">Aktywacja oparta na konfiguracji w usługach IIS i WAS</span><span class="sxs-lookup"><span data-stu-id="7c046-131">Configuration-Based Activation in IIS and WAS</span></span>](./feature-details/configuration-based-activation-in-iis-and-was.md)
- [<span data-ttu-id="7c046-132">Konfiguracja i obsługa metadanych</span><span class="sxs-lookup"><span data-stu-id="7c046-132">Configuration and Metadata Support</span></span>](./extending/configuration-and-metadata-support.md)
- [<span data-ttu-id="7c046-133">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="7c046-133">Configuration</span></span>](./diagnostics/exceptions-reference/configuration.md)
- [<span data-ttu-id="7c046-134">Instrukcje: określanie powiązania usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7c046-134">How to: Specify a Service Binding in Configuration</span></span>](how-to-specify-a-service-binding-in-configuration.md)
- [<span data-ttu-id="7c046-135">Instrukcje: tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7c046-135">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [<span data-ttu-id="7c046-136">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7c046-136">How to: Publish Metadata for a Service Using a Configuration File</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="7c046-137">Instrukcje: określanie powiązań klienta w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7c046-137">How to: Specify a Client Binding in Configuration</span></span>](how-to-specify-a-client-binding-in-configuration.md)
